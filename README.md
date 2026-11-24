# Portfolio content repository example

This folder is the starter for the separate `portfolio-content` GitHub
repository. Create that repository, copy `content.json` into its root, and set
the portfolio website's `PORTFOLIO_CONTENT_URL` to its raw GitHub URL.

Example:

```env
PORTFOLIO_CONTENT_URL=https://raw.githubusercontent.com/neeraj-kumar-rs/portfolio-content/main/content.json
```

## Demo behavior

Every project keeps the same **Demo** button and follows exactly two paths.

### 1. Explicit live link

Set `demo.url`. The button opens that URL immediately. `vercel` may be omitted.

```json
"demo": {
  "url": "https://my-project.example.com"
}
```

### 2. No explicit live link

Set `demo.url` to `null` and provide the allowlisted Vercel source. Clicking
Demo asks the portfolio's server route to create a Vercel deployment, waits for
it to become ready, and then opens it.

```json
"demo": {
  "url": null,
  "vercel": {
    "projectName": "my-project",
    "owner": "github-name",
    "repo": "repository-name",
    "ref": "main",
    "target": "preview"
  }
}
```

The website must have `VERCEL_TOKEN` configured as a server-only environment
variable. Never place that token in this content file.

If both `url` and `vercel` are missing, the Demo button is disabled.

## Updating content

Edit `content.json` directly on GitHub. The portfolio refreshes it on a cache
schedule. For immediate updates, configure the signed `/api/revalidate` webhook
described in the main repository README.
