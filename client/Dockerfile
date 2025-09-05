# Frontend: Vite/React -> Nginx
FROM node:18-alpine AS build
WORKDIR /app

COPY client/package*.json ./
RUN npm ci

COPY client ./
# Optional build-time API URL for Vite
ARG VITE_API_BASE_URL
ENV VITE_API_BASE_URL=${VITE_API_BASE_URL}
RUN npm run build

FROM nginx:alpine
# SPA + proxy to backend at http://backend:5000
COPY docker/nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
