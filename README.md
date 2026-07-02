# chiquechics-landing

This repository hosts the static, luxury editorial landing page for Chique Chics.

## Custom domain
A `CNAME` file has been added to the repository root to connect the site to your official domain:

- `chiquechics.com`

## GitHub Pages deployment
To publish the live site via GitHub Pages:

1. Go to the **Settings** tab of this repository.
2. Navigate to **Pages** in the left sidebar menu.
3. Under **Build and deployment**, set the source to `Deploy from a branch`.
4. Choose the `main` branch and select the `/ (root)` folder as the publishing source, then hit **Save**.
5. Scroll down to **Custom domain**, confirm it is listed as `chiquechics.com`, and ensure **Enforce HTTPS** is checked.

## DNS settings
To successfully route your custom apex domain `chiquechics.com` to GitHub's servers, configure these **A records** at your domain registrar (e.g., Namecheap, GoDaddy, Google Domains):

- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

### Subdomain Setup (WWW)
If you want `www.chiquechics.com` to safely redirect to your main site, add the following record at your registrar:

* **Type:** `CNAME`
* **Host/Name:** `www`
* **Value/Target:** `chiquechics.github.io` *(or your exact GitHub organization/username URL)*