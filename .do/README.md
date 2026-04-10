# DigitalOcean Deployment Configuration

This directory contains configuration for deploying DisasterPulse to **DigitalOcean App Platform**.

## Files

- **app.yaml** — DigitalOcean App Platform specification
  - Defines backend service configuration
  - Build and run commands
  - Health checks and resources
  - Auto-deployed from GitHub

## How It Works

1. Push code to GitHub `main` branch
2. DigitalOcean webhook triggers
3. DigitalOcean reads `.do/app.yaml`
4. Builds and deploys according to spec
5. Backend service available at auto-assigned URL

## Key Settings

| Setting | Value |
|---------|-------|
| Service | `backend` |
| Source | `app/` directory |
| Build | `pip install -r requirements.txt` |
| Run | `uvicorn main:app --host 0.0.0.0 --port 8080` |
| Port | `8080` |
| Health Check | `/health` every 10s |
| Auto-Deploy | Enabled (main branch) |

## Setup

1. Create DigitalOcean account: https://www.digitalocean.com
2. Go to App Platform: https://cloud.digitalocean.com/apps
3. Click **Create App** → Select GitHub repo
4. DigitalOcean auto-detects `.do/app.yaml`
5. Review and deploy

See full guide: [docs/DIGITALOCEAN_DEPLOYMENT.md](../docs/DIGITALOCEAN_DEPLOYMENT.md)

## Modifying Configuration

To change build/run commands, instance size, etc.:

1. Edit `app.yaml`
2. Commit and push
3. DigitalOcean auto-redeploys with new config

## Cost

- Basic-xs: ~$5-12/month
- Your $200 credit covers ~20-28 months
- Add persistent volume: +$1-2/month
