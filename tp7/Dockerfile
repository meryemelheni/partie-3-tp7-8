# syntax=docker/dockerfile:1
# TP7 partie 3 : Dockerfile multi-stage à compléter.

# ---------- Étape 1 : dépendances ----------
FROM node:24-alpine AS deps
WORKDIR /app
# TODO : copier uniquement package.json et package-lock.json (meilleur cache des couches)
# TODO : npm ci

# ---------- Étape 2 : build ----------
FROM node:24-alpine AS build
WORKDIR /app
# TODO : récupérer node_modules depuis l'étape deps (COPY --from=deps ...)
# TODO : copier tsconfig.json et src/, puis npm run build
# TODO : supprimer les devDependencies (npm prune --omit=dev)

# ---------- Étape 3 : runtime ----------
FROM node:24-alpine AS runtime
ENV NODE_ENV=production
WORKDIR /app
# TODO : copier dist/, node_modules/ et package.json depuis l'étape build,
#        avec --chown=node:node
# TODO : passer en utilisateur non-root (l'image node fournit l'utilisateur "node")
EXPOSE 3000
# TODO : HEALTHCHECK qui interroge http://localhost:3000/health
#        (astuce : wget -qO- est disponible dans alpine)
CMD ["node", "dist/server.js"]
