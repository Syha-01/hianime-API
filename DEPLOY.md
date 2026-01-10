# Deploy to Vercel

This API is configured to be easily deployed on [Vercel](https://vercel.com).

## Automatic Deployment (Recommended)

1.  **Push Changes**: Ensure you have pushed the `api` folder and `vercel.json` file to your GitHub repository.
    ```bash
    git add .
    git commit -m "Add Vercel deployment configuration"
    git push origin main
    ```

2.  **Deploy**:
    *   Click the "Deploy to Vercel" button in the `README.md`.
    *   **OR** Go to your Vercel Dashboard, click **Add New Project**, import your repository, and click **Deploy**.
    *   Vercel will automatically detect the configuration.

## Manual Deployment (CLI)

1.  Install Vercel CLI: `npm i -g vercel`
2.  Run `vercel` in the project root.
