# cloudflare-registry-proxy

![deploy](https://github.com/ketches/cloudflare-registry-proxy/actions/workflows/deploy.yaml/badge.svg)

## Deploy

1. Fork this project
2. Modify the routes map in `index.js`, and commit the changes
   ```javascript
   const routes = {
     "docker.ketches.cn": "https://registry-1.docker.io",
     "quay.ketches.cn": "https://quay.io",
     "gcr.ketches.cn": "https://gcr.io",
     "k8s-gcr.ketches.cn": "https://k8s.gcr.io",
     "k8s.ketches.cn": "https://registry.k8s.io",
     "ghcr.ketches.cn": "https://ghcr.io",
     "cloudsmith.ketches.cn": "https://docker.cloudsmith.io",
   };
   ```
3. Enable GitHub Actions in your fork (Actions > I understand my workflows, go ahead and enable them)
4. Add Secrets in your fork (Settings > Secrets > New repository secret)
   - `CLOUDFLARE_API_TOKEN`: Cloudflare API Token
   - `CLOUDFLARE_ACCOUNT_ID`: Cloudflare Account ID
5. Deploy to Cloudflare Workers (Actions > Deploy to **Cloudflare** Workers)
6. Add Custom Domains for your Cloudflare Worker as the routes in `index.js`

## Usage

```bash
# docker pull k8s.gcr.io/pause:3.9
# use k8s.ketches.cn as the registry proxy =>

docker pull k8s.ketches.cn/pause:3.9
```