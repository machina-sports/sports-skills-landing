# sports-skills-landing

Landing page for [sports-skills.sh](https://sports-skills.sh), the open-source agent skills for live sports data and prediction markets by [Machina Sports](https://machina.gg).

Live at **https://go.sports-skills.sh**

A single static `index.html` (no build step). Fonts come from Google Fonts; everything else is inline.

## Deploy

Merging to `main` deploys automatically (`.github/workflows/deploy.yml`): GitHub OIDC assumes the IAM role `sports-skills-landing-github-deploy` (main branch only), uploads `index.html` and `og.png` to the private S3 bucket `go-sports-skills-sh`, and invalidates CloudFront `E34HXPZLTKORCP`. DNS (`go` CNAME) lives in the Azure DNS zone `sports-skills.sh`.

The social preview `og.png` (1200×630) is rendered from `og/og-card.html`:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars \
  --force-device-scale-factor=1 --window-size=1200,630 --virtual-time-budget=6000 \
  --screenshot="$PWD/og.png" "file://$PWD/og/og-card.html"
```
