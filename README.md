# Ornithopter Vision Detection System

A real-time computer vision system designed to give an autonomous ornithopter the ability to identify and locate important objects in its environment.

The system uses a trained object detection model to recognize a designated **nest** and other **items of interest** from camera footage. The goal is to provide the ornithopter with visual awareness that can support autonomous navigation, search, monitoring, and mission-specific tasks.

## Overview

The Ornithopter Vision Detection System is being developed as an onboard computer vision pipeline for autonomous flight.

During flight, a camera captures images or video of the surrounding environment. The detection model processes this visual information and identifies objects relevant to the mission.

### Primary Detection Classes

The initial system is designed to detect:

- **Nest** - The primary target/reference location.
- **Items of Interest** - Objects that the ornithopter needs to identify during a mission.

Additional detection classes may be added as the project develops.

## Project Goals

The primary goals of this project are to:

1. Detect nests reliably from aerial imagery.
2. Detect designated items of interest.
3. Perform detection in real time.
4. Maintain reliable detection under changing outdoor conditions.
5. Minimize inference latency.
6. Create a lightweight system suitable for eventual onboard deployment.
7. Provide detection data that can be used by the ornithopter's autonomous flight system.

## System Architecture

```text
             ┌─────────────────┐
             │      Camera     │
             └────────┬────────┘
                      │
                      ▼
             ┌─────────────────┐
             │  Image Capture  │
             └────────┬────────┘
                      │
                      ▼
             ┌─────────────────┐
             │ Object Detector │
             │    YOLO Model   │
             └────────┬────────┘
                      │
              ┌───────┴────────┐
              ▼                ▼
        ┌───────────┐    ┌───────────────┐
        │   Nest    │    │ Item of       │
        │ Detection │    │ Interest      │
        └─────┬─────┘    └───────┬───────┘
              │                  │
              └────────┬─────────┘
                       ▼
              ┌──────────────────┐
              │ Mission / Flight │
              │    Decisions     │
              └──────────────────┘
