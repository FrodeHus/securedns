# Secure DNS-over-HTTPS for Kubernetes

Based on [this awesome blog by Scott Helme](https://scotthelme.co.uk/securing-dns-across-all-of-my-devices-with-pihole-dns-over-https-1-1-1-1/) I figured it would be cool to translate this into a Kubernetes deployment since Raspberry Pi Kubernetes clusters are now a big thing for the container enthusiast.

### Quick deploy

> Change the default passwords before exposing this to the wild

```bash
kubectl apply -f deploy/
```

This will deploy:
- The actual deployment with two containers
  - PiHole
  - cloudflared
- ConfigMap for PiHole
- Secret for PiHole admin user (default: `admin` (you MIGHT want to change this))
- Service
- Ingress (configured for Traefik with Let's Encrypt certificates)
  - configured to use basic authentication (default: `admin/admin` (again, MIGHT want to change this))

