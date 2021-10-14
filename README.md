# Netlify CMS on Vercel

A simple OAuth2 serverless gateway for Netlify CMS

## Why do I need this?

If you would like to use Netlify CMS to manage your site deployed to Vercel.

[GitHub](https://github.com) and [GitLab](https://gitlab.com) require an OAuth2 server for authentication. Netlify provides this server (https://api.netlify.com) only for sites deployed to Netlify. Fortunately, such server is rather small and can work with Vercel's serverless functions.

## Deploy

1. Deploy the OAuth serverless functions to your Vercel account:
   - For GitHub: [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fnop33%2Fnetlify-cms-oauth&env=OAUTH_GITHUB_CLIENT_ID,OAUTH_GITHUB_CLIENT_SECRET&envDescription=GitHub%20OAuth%20application%20env%20variables&envLink=https%3A%2F%2Fdocs.github.com%2Fen%2Fdevelopers%2Fapps%2Fbuilding-oauth-apps%2Fcreating-an-oauth-app&project-name=netlify-cms-oauth&repo-name=netlify-cms-oauth)
   - For GitLab: [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fnop33%2Fnetlify-cms-oauth&env=OAUTH_GITLAB_CLIENT_ID,OAUTH_GITLAB_CLIENT_SECRET&envDescription=GitLab%20OAuth%20application%20env%20variables&envLink=https%3A%2F%2Fdocs.gitlab.com%2Fee%2Fintegration%2Foauth_provider.html&project-name=netlify-cms-oauth&repo-name=netlify-cms-oauth)
2. Create an OAuth App on [GitHub](https://docs.github.com/en/developers/apps/building-oauth-apps/creating-an-oauth-app) or [GitLab](https://docs.gitlab.com/ee/integration/oauth_provider.html)
3. Set the _"Authorization callback URL"_ (GitHub) or the _"Redirect URI"_ (GitLab) to your deployed OAuth website callback endpoint: `https://<your-oauth-project>.vercel.app/callback`
4. Set environment variables on `Vercel`
   - For GitHub:
     ```shell
     OAUTH_GITHUB_CLIENT_ID=<your-client-id>
     OAUTH_GITHUB_CLIENT_SECRET=<your-client-secret>
     ```
   - For GitLab:
     ```shell
     OAUTH_GITLAB_CLIENT_ID=<your-client-id>
     OAUTH_GITLAB_CLIENT_SECRET=<your-client-secret>
     ```

## Usage

Update the `base_url` in the Netlify CMS `config.yml` file:

```yaml
backend:
  name: [github | gitlab]
  repo: your-username/your-repo # Path to your GitHub/GitLab repository
  branch: main # Branch to update
  base_url: https://<your-oauth-project>.vercel.app
```

## Authors

- Adrián UB ([@AdrianUB](https://twitter.com/AdrianUB))
- Ilias Trichopoulos ([@eyettea](https://twitter.com/eyettea))
