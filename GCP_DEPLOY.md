# Deploying Hianime API to Google Cloud Run

This guide explains how to deploy your Bun-based API to Google Cloud Run.

## Prerequisites

1.  **Google Cloud Platform (GCP) Project**: You need a GCP project with billing enabled.
2.  **gcloud CLI**: Install the [Google Cloud SDK](https://cloud.google.com/sdk/docs/install).

## Deployment Steps

1.  **Login to Google Cloud**:
    ```bash
    gcloud auth login
    ```

2.  **Set your project ID**:
    ```bash
    gcloud config set project YOUR_PROJECT_ID
    ```

3.  **Deploy to Cloud Run**:
    Run the following command in the root directory of your project:

    ```bash
    gcloud run deploy hianime-api \
      --source . \
      --platform managed \
      --region us-central1 \
      --allow-unauthenticated \
      --port 3030
    ```

    *   `--source .`: Builds the container image from the current directory using the `Dockerfile`.
    *   `--platform managed`: Uses the fully managed Cloud Run platform.
    *   `--region us-central1`: Specifies the region (change if needed).
    *   `--allow-unauthenticated`: Allows public access to your API.
    *   `--port 3030`: Cloud Run defaults to 8080, but your `bun-server.js` defaults to 3030 (unless `PORT` env var is set). Cloud Run sets the `PORT` env var automatically, so this flag might be redundant if your app listens on `process.env.PORT`, but it's good for clarity or if you want to hardcode the container port.

    **Note:** Creating a Cloud Build artifact registry might be required on the first run. The CLI will prompt you to enable the necessary APIs (Cloud Build API, Artifact Registry API, Cloud Run Admin API). Say "y" (yes) to these prompts.

4.  **Get the URL**:
    Once the deployment is complete, the command will output the Service URL (e.g., `https://hianime-api-xxxxx-uc.a.run.app`).

## Testing Locally (Optional)

You can build and run the Docker image locally to verify it before deploying.

1.  **Build**:
    ```bash
    docker build -t hianime-api .
    ```

2.  **Run**:
    ```bash
    docker run -p 3030:3030 -e PORT=3030 hianime-api
    ```

3.  Access `http://localhost:3030` in your browser.
