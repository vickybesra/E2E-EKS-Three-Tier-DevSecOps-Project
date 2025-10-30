FROM node:14 AS backend
WORKDIR /usr/src/app
COPY ../../../app/backend/. .
RUN npm install

FROM node:14.0.0-alpine
WORKDIR /app
COPY --from=backend /usr/src/app/node-modules ./node-modules
COPY --from=backend /usr/src/app/modules .
COPY --from=backend /usr/src/app/routes .
COPY --from=backend /usr/src/app/db.js .
COPY --from=backend /usr/src/app/index.js .
CMD ["node", "index.js"]
