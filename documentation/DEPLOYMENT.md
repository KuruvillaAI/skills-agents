# Deployment

## Current Platform

The project is deployed from separate GitHub repositories in the `KuruvillaAI` organization:

| Component | Repository | Render service | Public URL |
|---|---|---|---|
| Backend | `KuruvillaAI/backend` | `backend` | `https://backend-57rc.onrender.com` |
| Frontend | `KuruvillaAI/frontend` | `kuruvillaai` | `https://frontend-lvhc.onrender.com` |

Render is connected directly to each repository's `main` branch. A push to either repository triggers an automatic deployment.

## Backend

The backend is a Render Docker Web Service using `backend/Dockerfile` and the free plan. Render checks `GET /health` after deployment. Free instances sleep after inactivity, so the first request can be delayed while the service wakes.

Production configuration is supplied through Render environment variables. At minimum:

```text
APP_ENV=production
EMBEDDING_PROVIDER=mock
LLM_PROVIDER=mock
VECTOR_DB_PROVIDER=memory
CORS_ALLOWED_ORIGINS=https://frontend-lvhc.onrender.com
```

Provider secrets such as `OPENAI_API_KEY` and `PINECONE_API_KEY` must be added only as Render secrets when those providers are enabled.

## Frontend

The frontend is a Render Static Site built from `KuruvillaAI/frontend`:

```text
npm ci && npm run type-check && npm run build
```

The published directory is `dist`. The production build receives:

```text
VITE_API_BASE_URL=https://backend-57rc.onrender.com
VITE_BASE_PATH=/
```

## Verification

After every deployment:

1. Open the frontend public URL.
2. Confirm the page renders and the health badge becomes `Backend online` after the backend wakes.
3. Check `GET https://backend-57rc.onrender.com/health` returns HTTP 200.
4. Verify the backend CORS response allows `https://frontend-lvhc.onrender.com`.
5. Exercise upload and chat through the frontend when approved knowledge content is available.

## URL Naming

Renaming a GitHub repository or Render service changes its display/source name, not an existing generated `onrender.com` hostname. A custom domain requires ownership of that domain and DNS configuration in Render.

## Cost And Limitations

This deployment uses Render's free services. The backend can cold-start after inactivity, free services have limited resources, and local in-memory/FAISS data is not durable across restarts. Production persistence requires a separately provisioned database/vector store.