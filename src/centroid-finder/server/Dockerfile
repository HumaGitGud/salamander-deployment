FROM node:20-slim

# Create app directory
WORKDIR /app

# Install dependencies (production only)
COPY package*.json ./
RUN npm ci --only=production

# Copy server source
COPY . .

# Install ffmpeg (used by fluent-ffmpeg)
RUN apt-get update && apt-get install -y ffmpeg && rm -rf /var/lib/apt/lists/*

# Create runtime directories for persisted data
RUN mkdir -p /app/videos /app/results /app/thumbnails

ENV PORT=3000 \
    RESULTS_DIR=/app/results \
    VIDEO_DIR=/app/videos \
    THUMBNAIL_DIR=/app/thumbnails \
    JOBS_FILE=/app/jobs.json

EXPOSE 3000

CMD ["node", "server.js"]
