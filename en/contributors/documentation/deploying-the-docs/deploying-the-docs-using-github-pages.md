# Deploying the docs using GitHub Pages

To showcase your updates, especially helpful for design changes pending review, you can deploy the docs website either to your infrastructure or to GitHub Pages, a free hosting service. Once deployed, share the link with us for review.

## Prerequisites

In your `stride-docs` repository:

1. Navigate to **Settings** → **Actions** → **General** → **Workflow Permissions**
   - Choose **Read and write permissions**

## Run GitHub Action

1. Go to **Actions**, select **Build Stride Docs for GitHub Staging**
   - Click **Run workflow**; you may optionally select a branch
2. Monitor the build logs while the action is in progress
3. Upon successful build, a `gh-pages` branch will be created
4. Navigate to **Settings** → **Pages** → **Branch** section
   - Choose the `gh-pages` branch with the root option and click **Save**
5. After saving, an internal GitHub Action **pages build and deployment** is automatically created and triggered, deploying the content to the GitHub Pages website
6. The website will be accessible at `https://[your-username].github.io/stride-docs/4.2/en`
   - Change the version in the URL accordingly. You might see some JS errors, related to file expected in the root level.

## Add Custom Domain

Optionally, you can add also a custom domain. This should resolve JS url related errors.

1. Go to **Settings** → **Pages** → **Custom domain**
   - Enter your custom domain and follow the instructions for verification
1. Upon saving, the **pages build and deployment** action is triggered again, adding a `CNAME` file containing your custom domain name to the `gh-pages` branch
1. Your website should now be fully operational on your custom domain, for example, `https://stride-docs.vaclavelias.com/4.2/en/` is hosted on GitHub Pages
