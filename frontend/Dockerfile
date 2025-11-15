FROM node:20-alpine

# Install curl for health checks and Chromium for Playwright
RUN apk add --no-cache curl \
    chromium \
    nss \
    freetype \
    harfbuzz \
    ca-certificates \
    ttf-freefont

#USER 1001
RUN mkdir -p /app/.next && chmod -R g+rwX /app

WORKDIR /app

# Configure Playwright to use system Chromium
ENV PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1 \
    PLAYWRIGHT_BROWSERS_PATH=0 \
    npm_config_update_notifier=false \
    CHROMIUM_PATH=/usr/bin/chromium-browser \
    PW_LAUNCH_ARGS="--no-sandbox --disable-dev-shm-usage"

# Copy package files
COPY package.json package-lock.json* ./

# Install dependencies
RUN npm install

EXPOSE 3000

# Set environment variables
ENV PORT 3000
ENV HOSTNAME "0.0.0.0"

# Start development server

# Asegura que la carpeta exista y tenga permisos de escritura para grupo
# Usa un usuario genérico no root compatible con OpenShift


CMD ["npm", "run", "dev"]

