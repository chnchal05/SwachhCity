Project Name: SwachhCity AI

Project Overview

SwachhCity AI is an AI-powered waste detection and verification system designed to proactively identify garbage accumulation, metal scrap, food waste, and e-waste across urban environments.

The system integrates with Surakshit Bharat CCTV infrastructure and citizen-uploaded images to automatically detect waste, classify it using dual AI models, generate geo-tagged alerts, and verify cleanup actions.

Its goal is to reduce manual monitoring, improve municipal response time, protect citizen privacy, and enable smarter waste management.

Functional Requirements:

Image acquisition from Surakshit Bharat CCTV feeds
Citizen image upload with location metadata
AI-based waste detection using YOLOv8
Waste classification using ResNet
Dual-model verification to reduce false positives
Scrap vehicle detection based on multiple visual conditions
Automatic face detection and blurring before storage
Geo-tagging of detected waste locations
Alert generation for municipal authorities
Interactive dashboard with map-based waste tracking
Pre- and post-cleanup image comparison for verification

Non-Functional Requirements:

Image processing within 5 seconds per frame
Detection accuracy above 85%( can improve by time )
False positive rate below 15%
Secure storage with encrypted data transmission
Scalable architecture to support multiple CCTV feeds
Reliable and responsive web dashboard

Assumptions:

Surakshit Bharat CCTV feeds are accessible
CCTV cameras have sufficient resolution (minimum 720p)
Municipal authorities access the system via web browser
Pre-trained AI models can be fine-tuned for waste detection

Constraints:

Must use YOLOv8 for object detection
Must use ResNet for classification
Face blurring must occur before image storage
Dependent on CCTV feed quality
Citizen uploads include location metadata

User Roles:

Municipal Authorities (Primary Users)
Waste Management Teams
City Administrators
Citizens submitting reports

Acceptance Criteria:

System detects waste with at least 85% accuracy
Dual-model verification reduces false positives significantly
Scrap vehicles flagged only when multiple conditions are met
Faces are blurred before any image storage
Dashboard displays geo-tagged alerts correctly
Pre- and post-cleanup comparison confirms waste removal