<a href="https://vercel.com/new/git/external?repository-url=https%3A%2F%2Fgithub.com%2Fublabs%2Fnetlify-cms-oauth&env=OAUTH_GITHUB_CLIENT_ID,OAUTH_GITHUB_CLIENT_SECRET,OAUTH_GITLAB_CLIENT_ID,OAUTH_GITLAB_CLIENT_SECRET&envDescription=Create%20a%20OAuth%20App%20on%20Github%20and%20Gitlab%20and%20set%20variables%20information%20&envLink=https%3A%2F%2Fgithub.com%2Fublabs%2Fnetlify-cms-oauth%23deploy&project-name=netlify-cms-oauth&repo-name=netlify-cms-oauth&demo-title=Netlify%20CMS%20OAuth&demo-description=Use%20Netlify%20CMS%20for%20sites%20hosted%20on%20Vercel.&demo-url=https%3A%2F%2Fnetlify-cms-adrianub.vercel.app"><img height="100" src="https://vercel.com/button" alt="Deploy with Vercel" align="right"></a>

<div align="center">
    <h3>
        Netlify CMS on Vercel
    </h3>
    <p>
        A simple OAuth2 serverless gateway for Netlify CMS
    </p>
</div>

---

## Why do I need this?

If you would like to use Netlify CMS to manage your site deployed to Vercel.

[GitHub](https://github.com) and [GitLab](https://gitlab.com) require a server for authentication and Netlify provides this server only for sites deployed to it. Fortunately, such server is rather small and can work with Vercel's serverless functions.

## Usage

In your projects modify the `config.yml` file:

```yaml
backend:
  name: [github | gitlab]
  repo: adrian-ub/adrian-ub # Path to your GitHub/GitLab repository
  branch: main # Branch to update
  base_url: https://netlify-cms.adrianub.vercel.app
```

## Deploy

1. Deploy the OAuth serverless functions to your Vercel account
2. Create an OAuth App on [GitHub](https://docs.github.com/en/developers/apps/building-oauth-apps/creating-an-oauth-app) or [GitLab](https://docs.gitlab.com/ee/integration/oauth_provider.html)
3. Set the _"Authorization callback URL"_ (GitHub) or the _"Redirect URI"_ (GitLab) to your deployded OAuth website callback endpoint: `https://<your-oauth-project>.vercel.app/callback`
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

## Authors

- Adrián UB ([@AdrianUB](https://twitter.com/AdrianUB))
