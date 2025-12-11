# StoryForge Technical Architecture
## Version 1.0 | December 2024 | CONFIDENTIAL

---

# 1. System Overview

StoryForge is a cloud-native, microservices-based platform for generative cinematic content creation. The system orchestrates multiple AI models, manages complex state across multi-scene projects, and provides real-time collaborative editing capabilities.

## 1.1 High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              CLIENT LAYER                                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐    │
│  │   Web App    │  │  Mobile App  │  │  Desktop App │  │   TV App     │    │
│  │  (Next.js)   │  │(React Native)│  │  (Electron)  │  │   (Preview)  │    │
│  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘    │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            API GATEWAY LAYER                                 │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Kong / AWS API Gateway                                               │  │
│  │  • Rate Limiting  • Auth (JWT)  • Request Routing  • Load Balancing  │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  GraphQL Gateway (Apollo Federation)                                  │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            SERVICE LAYER                                     │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌──────────┐ │
│  │  Project   │ │   Scene    │ │ Continuity │ │   Brain    │ │  Format  │ │
│  │  Service   │ │  Service   │ │   Engine   │ │  Service   │ │ Service  │ │
│  └────────────┘ └────────────┘ └────────────┘ └────────────┘ └──────────┘ │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌──────────┐ │
│  │ Generation │ │   Export   │ │   User     │ │  Billing   │ │Marketplace│ │
│  │Orchestrator│ │  Service   │ │  Service   │ │  Service   │ │ Service  │ │
│  └────────────┘ └────────────┘ └────────────┘ └────────────┘ └──────────┘ │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            AI/ML LAYER                                       │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │                    Model Router & Load Balancer                       │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐      │
│  │  Runway API  │ │  Sora API    │ │  Kling API   │ │ Stability AI │      │
│  │  (Video)     │ │  (Video)     │ │  (Video)     │ │  (Image)     │      │
│  └──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘      │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐                       │
│  │   Claude     │ │  ElevenLabs  │ │  Custom      │                       │
│  │  (Prompts)   │ │   (Voice)    │ │  Fine-tunes  │                       │
│  └──────────────┘ └──────────────┘ └──────────────┘                       │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            DATA LAYER                                        │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐      │
│  │  PostgreSQL  │ │    Redis     │ │   Pinecone   │ │  S3 + CDN    │      │
│  │  (Primary)   │ │   (Cache)    │ │  (Vectors)   │ │   (Media)    │      │
│  └──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘      │
│  ┌──────────────┐ ┌──────────────┐                                         │
│  │    Kafka     │ │  ClickHouse  │                                         │
│  │  (Events)    │ │ (Analytics)  │                                         │
│  └──────────────┘ └──────────────┘                                         │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

# 2. Core Services Detail

## 2.1 Project Service
**Purpose:** Manages project lifecycle, scene ordering, and project-level metadata

**Responsibilities:**
- CRUD operations for projects, episodes, seasons
- Scene ordering and timeline management
- Export job orchestration
- Collaboration permissions and sharing
- Project templates and duplication

**Data Model:**
```
Project
├── id: UUID
├── user_id: UUID
├── title: String
├── type: ENUM (series, movie, short)
├── brain_id: UUID
├── format_id: UUID
├── settings: JSONB
├── scenes: Scene[]
└── created_at, updated_at
```

## 2.2 Continuity Engine
**Purpose:** Maintains character and environment consistency across scenes

**Key Components:**

1. **Character Identity Manager**
   - Face embedding storage (512-dim vectors)
   - Clothing/appearance descriptors
   - Voice signature references
   - Age/expression consistency

2. **Environment Tracker**
   - Location fingerprints
   - Lighting state machine
   - Prop inventory
   - Spatial relationships

3. **Temporal Coherence**
   - Time-of-day tracking
   - Weather continuity
   - Season/date awareness

**Algorithm:**
```python
def inject_continuity(scene_prompt, project_context):
    # 1. Extract character references
    characters = extract_characters(scene_prompt)
    
    # 2. Fetch embeddings from Pinecone
    for char in characters:
        char.embedding = vector_db.query(char.id)
        char.reference_frames = get_best_reference_frames(char)
    
    # 3. Build continuity injection
    continuity_prompt = build_continuity_context(
        characters=characters,
        location=project_context.current_location,
        time_state=project_context.time_of_day,
        prev_scene=project_context.previous_scene
    )
    
    # 4. Merge with original prompt
    return merge_prompts(scene_prompt, continuity_prompt)
```

## 2.3 Brain Service
**Purpose:** Manages cinematic style models and their application

**Brain Types:**
| Brain | Shot Language | Pacing | Color Palette | Specialty |
|-------|---------------|--------|---------------|-----------|
| Thriller | Tight close-ups, Dutch angles | Fast cuts, tension building | Desaturated, high contrast | Suspense, reveals |
| K-Drama | Wide establishing, emotional close-ups | Slow burn, cliffhangers | Warm, nostalgic | Romance, melodrama |
| Pixar | Dynamic camera, exaggerated perspective | Scene rhythm, comic timing | Vibrant, saturated | Family, emotion |
| Nolan | IMAX-style wide, practical effects feel | Non-linear, complex | Cool, metallic | Epic scale, time |
| Horror | Found footage, POV shots | Slow dread, jump scares | Dark, desaturated | Fear, atmosphere |

**Style Encoding:**
```json
{
  "brain_id": "thriller_v2",
  "style_vector": [0.23, 0.87, ...],  // 128-dim learned embedding
  "parameters": {
    "shot_composition": {
      "close_up_ratio": 0.4,
      "dutch_angle_freq": 0.15,
      "tracking_shot_duration": 3.5
    },
    "color_grading": {
      "saturation": -0.2,
      "contrast": 0.3,
      "color_temp": 5500
    },
    "pacing": {
      "avg_shot_duration": 2.1,
      "tension_curve": "exponential",
      "cut_rhythm": "syncopated"
    }
  }
}
```

## 2.4 Generation Orchestrator
**Purpose:** Coordinates multi-model inference pipelines

**Pipeline Stages:**

```
User Prompt
    │
    ▼
┌─────────────────────┐
│ 1. PROMPT ENHANCEMENT│
│   • Brain injection  │
│   • Format beat      │
│   • Continuity refs  │
│   • LLM expansion    │
└─────────────────────┘
    │
    ▼
┌─────────────────────┐
│ 2. CACHE CHECK      │
│   • Exact match     │
│   • Semantic sim    │
│   • Component reuse │
└─────────────────────┘
    │ (miss)
    ▼
┌─────────────────────┐
│ 3. STORYBOARD GEN   │
│   • Key frame imgs  │
│   • User selection  │
│   • Iteration loop  │
└─────────────────────┘
    │
    ▼
┌─────────────────────┐
│ 4. VIDEO SYNTHESIS  │
│   • Model routing   │
│   • Img-to-video    │
│   • Quality scoring │
└─────────────────────┘
    │
    ▼
┌─────────────────────┐
│ 5. POST-PROCESSING  │
│   • Audio sync      │
│   • Color grading   │
│   • Stabilization   │
└─────────────────────┘
    │
    ▼
Final Scene
```

---

# 3. Data Architecture

## 3.1 Database Schema (PostgreSQL)

```sql
-- Users & Auth
CREATE TABLE users (
    id UUID PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    subscription_tier VARCHAR(50),
    credits_balance INTEGER DEFAULT 0,
    created_at TIMESTAMP DEFAULT NOW()
);

-- Projects
CREATE TABLE projects (
    id UUID PRIMARY KEY,
    user_id UUID REFERENCES users(id),
    title VARCHAR(255) NOT NULL,
    project_type VARCHAR(50), -- series, movie, short
    brain_id UUID,
    format_id UUID,
    settings JSONB,
    status VARCHAR(50) DEFAULT 'draft',
    created_at TIMESTAMP DEFAULT NOW()
);

-- Scenes
CREATE TABLE scenes (
    id UUID PRIMARY KEY,
    project_id UUID REFERENCES projects(id),
    sequence_number INTEGER,
    prompt TEXT,
    enhanced_prompt TEXT,
    parameters JSONB,
    status VARCHAR(50), -- pending, generating, complete, locked
    video_url VARCHAR(500),
    thumbnail_url VARCHAR(500),
    duration_seconds FLOAT,
    iteration_count INTEGER DEFAULT 0,
    created_at TIMESTAMP DEFAULT NOW()
);

-- Characters
CREATE TABLE characters (
    id UUID PRIMARY KEY,
    project_id UUID REFERENCES projects(id),
    name VARCHAR(255),
    face_embedding VECTOR(512), -- pgvector extension
    appearance_descriptor JSONB,
    voice_reference_url VARCHAR(500),
    reference_images JSONB -- array of S3 URLs
);

-- Scene Versions (for iteration history)
CREATE TABLE scene_versions (
    id UUID PRIMARY KEY,
    scene_id UUID REFERENCES scenes(id),
    version_number INTEGER,
    prompt TEXT,
    parameters JSONB,
    video_url VARCHAR(500),
    created_at TIMESTAMP DEFAULT NOW()
);
```

## 3.2 Caching Strategy

| Layer | Storage | TTL | Use Case |
|-------|---------|-----|----------|
| L1: Exact Match | Redis | 30 days | Identical prompt + params |
| L2: Semantic | Pinecone | 90 days | Similar prompts (cosine > 0.95) |
| L3: Components | S3 + DB | Permanent | Reusable characters, backgrounds |
| L4: Pre-gen | Redis | 24 hours | Predicted next scenes |

**Cost Impact:**
- L1 cache hit: $0 (no inference)
- L2 cache hit: $0.01 (similarity search only)
- L3 partial: $0.20 (partial regeneration)
- Full generation: $0.50-2.00 (depending on model)

Target: 40% L1 hit rate, 60% overall cache utilization → 50% inference cost reduction

---

# 4. Infrastructure

## 4.1 AWS Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         AWS Cloud                                │
│                                                                  │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                    VPC (10.0.0.0/16)                     │   │
│  │                                                          │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │   │
│  │  │ Public Subnet│  │ Public Subnet│  │ Public Subnet│  │   │
│  │  │   (AZ-1a)    │  │   (AZ-1b)    │  │   (AZ-1c)    │  │   │
│  │  │   ALB, NAT   │  │   ALB, NAT   │  │   ALB, NAT   │  │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  │   │
│  │                                                          │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │   │
│  │  │Private Subnet│  │Private Subnet│  │Private Subnet│  │   │
│  │  │   EKS Nodes  │  │   EKS Nodes  │  │   EKS Nodes  │  │   │
│  │  │   RDS, Redis │  │   RDS, Redis │  │   RDS, Redis │  │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  │   │
│  │                                                          │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                  │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐       │
│  │    S3     │ │CloudFront │ │    SQS    │ │  Lambda   │       │
│  │  (Media)  │ │   (CDN)   │ │ (Queues)  │ │(Webhooks) │       │
│  └───────────┘ └───────────┘ └───────────┘ └───────────┘       │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

## 4.2 Kubernetes Deployment

```yaml
# Example: Generation Orchestrator Deployment
apiVersion: apps/v1
kind: Deployment
metadata:
  name: generation-orchestrator
spec:
  replicas: 3
  selector:
    matchLabels:
      app: generation-orchestrator
  template:
    spec:
      containers:
      - name: orchestrator
        image: storyforge/orchestrator:v1.2.0
        resources:
          requests:
            memory: "512Mi"
            cpu: "500m"
          limits:
            memory: "2Gi"
            cpu: "2000m"
        env:
        - name: RUNWAY_API_KEY
          valueFrom:
            secretKeyRef:
              name: ai-credentials
              key: runway-key
        - name: REDIS_URL
          value: "redis://redis-cluster:6379"
```

---

# 5. Security & Compliance

## 5.1 Security Measures

| Layer | Measure | Implementation |
|-------|---------|----------------|
| Network | WAF, DDoS protection | AWS WAF, Shield |
| Transport | TLS 1.3 everywhere | ACM certificates |
| Authentication | JWT + OAuth 2.0 | Auth0 / Cognito |
| Authorization | RBAC | Custom middleware |
| Data at Rest | AES-256 encryption | AWS KMS |
| API | Rate limiting, input validation | Kong, Joi |
| Secrets | Vault/SSM | AWS Secrets Manager |

## 5.2 Content Safety

- **Generation Filtering:** NSFW detection on all outputs
- **Prompt Moderation:** LLM-based content policy enforcement
- **IP Protection:** Watermarking, origin tracking
- **User Content:** Clear ToS, DMCA process

---

# 6. Scalability Roadmap

| Phase | Users | Infra | Key Investments |
|-------|-------|-------|-----------------|
| Alpha (M1-2) | 100 | Single region, minimal redundancy | Core functionality |
| Beta (M3-4) | 1,000 | Multi-AZ, auto-scaling | Reliability, monitoring |
| Launch (M5-6) | 10,000 | Multi-region read replicas | Performance, caching |
| Scale (M7-12) | 100,000 | Global CDN, edge processing | Cost optimization |
| Growth (Y2) | 500,000+ | Multi-cloud, custom inference | Vertical integration |

---

**Document Classification:** CONFIDENTIAL  
**Last Updated:** December 2024  
**Contact:** tech@storyforge.ai
