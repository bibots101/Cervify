# Cervify

Cervify is a computer-aided diagnosis platform for cervical cancer analysis. It combines a FastAPI backend, a React web frontend, and an Electron desktop application into a single end-to-end system for image upload, automated analysis, progress tracking, and result review.

The repository is organized into three independent deliverables that work together as one product:

- [Backend](Backend/README.md) - FastAPI service that handles authentication, image upload, encrypted storage, prediction orchestration, and history persistence.
- [Frontend](Frontend/README.md) - React + Vite web application for user sign-in, image submission, live progress tracking, and results viewing.
- [Desktop App](Desktop-app/README.md) - Electron wrapper that packages the frontend with the bundled backend for desktop distribution.

## Overview

The platform is built around a computer-vision pipeline that receives user images, processes them through the analysis stages in the backend, and returns prediction results through the web or desktop interface. Each subproject has its own documentation and can be developed independently.

## Repository Structure

- `Backend/` - FastAPI backend, pipeline code, database layer, and utility modules.
- `Frontend/` - Web UI built with React, Vite, and Tailwind CSS.
- `Desktop-app/` - Electron-based desktop launcher and packaging configuration.

## Quick Start

### 1. Run the backend

Follow the backend README for full setup instructions:
[Backend/README.md](Backend/README.md)

Typical development start:

```bash
cd Backend
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload --host 127.0.0.1 --port 8000
```

### 2. Run the frontend

Follow the frontend README for UI setup and configuration:
[Frontend/README.md](Frontend/README.md)

Typical development start:

```bash
cd Frontend
npm install
npm run dev
```

Make sure the frontend is pointed at the backend API URL configured in `Frontend/src/services/api.js`.

### 3. Run the desktop app

Follow the Electron wrapper documentation here:
[Desktop-app/README.md](Desktop-app/README.md)

Typical development start:

```bash
cd Desktop-app
npm install
npm start
```

The desktop app expects a compiled backend executable in the location described in its README.

## How the Pieces Fit Together

1. The frontend or desktop app sends a request to the backend.
2. The backend validates the request, encrypts and stores the uploaded image, and runs the pipeline.
3. The pipeline produces predictions and progress updates.
4. The frontend or desktop app displays the result and history to the user.

## Key Documentation

- [Backend README](Backend/README.md)
- [Frontend README](Frontend/README.md)
- [Desktop App README](Desktop-app/README.md)
- [Backend pipeline](Backend/pipeline/)
- [Backend utilities](Backend/utils/)

## Notes

- The backend uses local persistence and model assets defined in `Backend/utils/global_var.py`.
- The frontend is configured to talk to a backend running on `http://127.0.0.1:8000` by default.
- The desktop app packages the backend binary for distribution and uses it at runtime.

## Contributing

Keep changes focused on the relevant module and update the corresponding README when behavior or setup steps change. For user-facing or integration changes, update this global README if the project structure or startup flow changes.

## License

Refer to the license files or package metadata in each module for licensing details.
