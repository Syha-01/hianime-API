# Deploy to Vercel

This API is configured to be easily deployed on [Vercel](https://vercel.com).

## Automatic Deployment

1.  **Push Changes**:
    ```bash
    git add .
    git commit -m "Add Vercel deployment configuration"
    git push origin main
    ```

2.  **Deploy**:
    *   Click the **Deploy with Vercel** button in the `README.md`.
    *   **OR** Import your repository on Vercel.

### How it works
This project uses **Bun** to build the application for Vercel Serverless.
*   **Note**: We pre-build the API locally using `bun build` to resolve path aliases (`@/`). The resulting `api/index.js` is committed to the repository.
*   Vercel deploys `api/index.js` as a Node.js Serverless Function.

## Local Development (Re-building)

If you modify the code, you must re-build the API before pushing:
```bash
bun build api/_entry.js --outfile api/index.js --target node --format esm
```

## Manual Deployment (CLI)

1.  Install Vercel CLI: `npm i -g vercel`
2.  Run `vercel` in the project root.
