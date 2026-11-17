# sports-skills-landing

Landing page for [sports-skills.sh](https://sports-skills.sh), the open-source agent skills for live sports data and prediction markets by [Machina Sports](https://machina.gg).

Live at **https://go.sports-skills.sh**

A single static `index.html` (no build step). Fonts come from Google Fonts; everything else is inline.

## Deploy

Hosted on AWS: private S3 bucket behind CloudFront (Origin Access Control), ACM certificate in `us-east-1`. DNS lives in the Azure DNS zone `sports-skills.sh`.

```bash
aws s3 cp index.html s3://go-sports-skills-sh/index.html --content-type "text/html; charset=utf-8" --cache-control "public, max-age=300" --profile machina
aws cloudfront create-invalidation --distribution-id E34HXPZLTKORCP --paths "/*" --profile machina
```
