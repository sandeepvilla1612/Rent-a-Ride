# Backend: Node/Express
FROM node:18-alpine
WORKDIR /app

# Install only prod deps
COPY backend/package*.json ./
RUN npm ci --omit=dev

# Copy source
COPY backend ./

ENV NODE_ENV=production
# Change if your app listens on a different port
ENV PORT=5000
EXPOSE 5000

# Uses the repo's "start" script (recommended)
CMD ["npm", "start"]
# If you don't have a start script, change to:
# CMD ["node", "index.js"]
