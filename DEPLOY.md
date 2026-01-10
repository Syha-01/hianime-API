# Deploy to Render

This API is configured to be easily deployed on [Render](https://render.com).

## Automatic Deployment (Recommended)

1.  **Push Changes**: Ensure you have pushed the `render.yaml` file to your GitHub repository.
    ```bash
    git add render.yaml
    git commit -m "Add Render deployment configuration"
    git push origin main
    ```
2.  **Create Blueprint**:
    *   Go to your Render Dashboard.
    *   Click on **New +** and select **Blueprint**.
    *   Connect your GitHub repository (`yahyaMomin/hianime-API`).
    *   Render will automatically detect the `render.yaml` file and configure the service.
    *   Click **Apply** to start the deployment.

## Manual Deployment

If you prefer to configure it manually without `render.yaml`:

1.  Create a new **Web Service** on Render.
2.  Connect your repository.
3.  Use the following settings:
    *   **Runtime**: Bun
    *   **Build Command**: `bun install`
    *   **Start Command**: `bun index.js`
4.  Add Environment Variable:
    *   `PORT`: `10000` (or any port, Render assigns one automatically but it's good practice)
