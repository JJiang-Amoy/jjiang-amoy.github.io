---
title: "Deploy site in Netlify"
date: 2020-06-08T21:00:15+06:00
menu:
  sidebar:
    name: Deploy in Netlify
    identifier: getting-started-netlify
    parent: getting-started
    weight: 30
---

[Netlify](https://www.netlify.com/) offers an excellent and easy process for deploying hugo static site. You can deploy your site in matter of few clicks. Unlike Github Pages, you can name your repository whatever you want. You can also customize the site URL.

In this post, we will show the step-by-step process of deploying a hugo site with netlify.

### Add Netlify Configuration

At first, create a `netlify.toml` file at the root of your repository and add the following configuration there:

```toml
[build]
command = "hugo --gc --minify"
publish = "public"

[context.production.environment]
HUGO_ENABLEGITINFO = "true"
HUGO_ENV           = "production"
HUGO_THEME         = "toha"
HUGO_VERSION       = "0.77.0"

[context.split1]
command = "hugo --gc --minify --enableGitInfo"

    [context.split1.environment]
    HUGO_ENV     = "production"
    HUGO_VERSION = "0.77.0"

[context.deploy-preview]
command = "hugo --gc --minify --buildFuture -b $DEPLOY_PRIME_URL"

    [context.deploy-preview.environment]
    HUGO_VERSION = "0.77.0"

[context.branch-deploy]
command = "hugo --gc --minify -b $DEPLOY_PRIME_URL"

    [context.branch-deploy.environment]
    HUGO_VERSION = "0.77.0"

[context.next.environment]
HUGO_ENABLEGITINFO = "true"
```

Commit and push the `netlify.toml` file into Github. Now, you are ready to deploy your site with netlify.

### Deploy Site

Now, login into [netlify](https://www.netlify.com/). Then, go to `Sites` tab of your netlify dashboard and click `New site form Git` button.

{{< img src="images/2.png" align="center" >}}

{{< vs 2 >}}

A new popup will open. Select `Github` and authenticate, with your Github account.

{{< img src="images/3.png" align="center" >}}

{{< vs 2 >}}

After authenticating, it will ask to select your desired repository. Select the repository you are using for your site.

{{< img src="images/4.png" align="center" >}}

{{< vs 2 >}}

Now, netlify will take you to the deployment page. Select the branch you want to deploy. Netlify should automatically populate the required fields from the `netlify.toml` file you created earlier in this post. When you are satisfied with the configurations, press the `Deploy` button.

{{< img src="images/5.png" align="center" >}}

{{< vs 2 >}}

Now, netlify will start publishing your site immediately. Wait for the publishing process to complete. Once, the site has been published, you can browse your site at the URL automatically generated by netlify. The auto-generated URL has been pointed out by a red rectangle in the screenshot below.

{{< img src="images/6.png" align="center" >}}

### Customize URL

You can easily customize the URL of your site with just few clicks as shown below.

1. Click the `Domain Setting` button under `Site Overview` tab.

{{< img src="images/7.png" align="center" >}}

2. Now, you can either add your own domain by clicking on `Add custom domain` button or you can just use `<your custom prefix>.netlify.app` domain. Here, we are going with the later. Click the `options` dropdown and select `Edit site name`.

{{< img src="images/8.png" align="center" >}}

{{< vs 2 >}}

3. Then, give your site whatever name you want.

{{< img src="images/9.png" align="center" >}}

{{< vs 2 >}}

4. Once you have saved the new name, you will see the URL of your site has been updated instantly. Now, you can browse your site at the new URL.

{{< img src="images/10.png" align="center" >}}