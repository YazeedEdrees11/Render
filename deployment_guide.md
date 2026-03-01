# Deployment Guide for Render

This guide explains how to deploy the Cell Avenue RAG application to Render using the provided Blueprint.

## Prerequisites

1.  A [Render](https://render.com/) account.
2.  Your project code pushed to a GitHub or GitLab repository.
3.  Necessary API keys (OpenAI, Pinecone, etc.).

## Steps to Deploy

### 1. Connect your Repository
Log in to your Render dashboard and click **New > Blueprint**. Connect your GitHub/GitLab repository.

### 2. Configure Service
Render will automatically detect the `render.yaml` file in your root directory. This provides a "zero-config" experience.

> [!NOTE]
> The `render.yaml` Blueprint is located at the project root, while the specific Dockerfiles remain in the `Render` folder for organization.

### 3. Set Environment Variables
During the Blueprint setup, Render will ask you for the values of the following environment variables:
- `OPENAI_API_KEY`
- `PINECONE_API_KEY`
- `PINECONE_ENVIRONMENT`
- `PINECONE_INDEX_NAME`

The `NEXT_PUBLIC_API_URL` for the frontend is automatically linked to the backend service.

### 4. Deploy
Click **Apply** (or **Create Blueprint**). Render will start building and deploying both the backend and frontend services.

## File Structure for Deployment
- `Render/backend.Dockerfile`: Specialized Dockerfile for the FastAPI backend.
- `Render/frontend.Dockerfile`: Specialized Dockerfile for the Next.js frontend.
- `Render/render.yaml`: The Blueprint file that orchestrates the deployment.

## Troubleshooting
- **Build Errors**: Check the build logs in the Render dashboard for both services. Ensure your `requirements.txt` and `package.json` are up to date.
- **Runtime Errors**: Check the service logs for any missing environment variables or connection issues.
