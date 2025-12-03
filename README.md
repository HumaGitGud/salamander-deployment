# Salamander Deployment

A full-stack application for video processing and centroid detection. Upload videos, apply color-based binarization, detect centroids, and download results as CSV.

## Project Structure

- **Frontend** (`src/frontend/`): Next.js React UI for video upload, preview, and result download
- **Server** (`src/centroid-finder/server/`): Express.js backend API for video management and job orchestration
- **Processor** (`src/centroid-finder/processor/`): Java application for video frame processing and centroid detection

## Quick Start

### Prerequisites

- Docker & Docker Compose
- Git

### Build & Run

```bash
cd src/...
npm install (run in node folders)
remove .example from .env file (contents within are accurate to this project structure)
docker compose build
docker compose up -d
```

Access the app at **http://localhost:3000**

### Check Logs

```bash
docker compose logs -f server
docker compose logs -f frontend
```

### Stop

```bash
docker compose down
```

## How It Works

1. **Upload/Select**: Choose a video from the frontend
2. **Preview**: View thumbnail, adjust target color and threshold
3. **Process**: Submit for processing (spawns Java centroid finder)
4. **Download**: Once complete, download the CSV with centroid coordinates

## Tech Stack

- **Frontend**: Next.js, Material-UI, React
- **Backend**: Express.js, Node.js
- **Processor**: Java 21, Maven, JavaCV
- **DevOps**: Docker, Docker Compose

## Environment Variables

See `.env` in `src/centroid-finder/` for configuration (paths, ports, etc.).

## Deploy to VM

For Ubuntu VM deployment, push the built images to a registry or build directly on the VM:

```bash
# On VM:
git clone <repo>
cd src/
docker compose build
docker compose up -d
```

Access via `http://<vm-ip>:3000`