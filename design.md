# SwachhCity – AI-Powered Waste Detection System
## Design Document

## 1. Overview

SwachhCity is an AI-based waste detection and verification system that uses CCTV feeds and citizen uploads to automatically detect waste accumulation and scrap vehicles, generate alerts, and verify cleanup actions.

Tech Stack:
- Backend: FastAPI (Python)
- AI Models: YOLOv8 + ResNet50
- Database: PostgreSQL + PostGIS
- Cloud: AWS (EC2, S3, RDS)
- Frontend: React.js Dashboard

---

## 2. System Architecture

Flow:

Input (CCTV / Citizen Upload/ Satellite)
        ↓
Privacy Protection (Face Blur)
        ↓
YOLOv8 Object Detection
        ↓
ResNet Classification
        ↓
Verification Logic
        ↓
Database Storage
        ↓
Municipal Dashboard + Alerts

---

## 3. AI Pipeline

### 3.1 YOLOv8 – Object Detection
- Detects waste objects and vehicles
- Confidence threshold: 0.5
- Outputs bounding boxes

### 3.2 ResNet50 – Waste Classification
- Classifies cropped waste regions
- Confidence threshold: 0.7
- Categories: Plastic, Paper, Organic, Metal Scrap, Debris, Scrap Vehicle

### 3.3 Dual-Model Verification

Detection is valid only if:
- YOLO confidence > 0.5
- ResNet confidence > 0.7
- Combined confidence > 0.6
- Classes match

This reduces false positives.

---

## 4. Scrap Vehicle Detection Logic

Vehicle is flagged as scrap if 3 or more conditions are met:
- Visible rust
- Missing parts
- Flat tires
- Deformation

This prevents incorrect vehicle tagging.

---

## 5. Data Flow

Image → Face Blur → Detection → Classification → Verification → Store → Alert

Cleanup Verification:
Pre-cleanup image stored  
Post-cleanup image uploaded  
If waste removed and similarity >70% → Mark Resolved

---

## 6. Database Design

Core Tables:
- detections
- alerts
- scrap_vehicles
- cctv_feeds

Geo-location stored using PostGIS for map-based dashboard view.

---

## 7. Deployment (Hackathon Setup)

- EC2 for backend + models
- RDS PostgreSQL with PostGIS
- S3 for blurred image storage
- HTTPS enabled
- JWT authentication for dashboard

---

## 8. Security & Privacy

- Faces blurred before storage
- No raw images stored
- TLS encryption in transit
- Encrypted S3 storage
- Rate limiting enabled

---

## 9. Performance Targets

- less than 5s processing per image
- more than 85% detection accuracy 
- less than 15% false positives
- Dashboard response <2s


