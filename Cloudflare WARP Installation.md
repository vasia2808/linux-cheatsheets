# Cloudflare WARP Installation

Install the package:

```bash
paru -S cloudflare-warp-minimal-bin
```

or

```bash
paru -S cloudflare-warp-nox-bin
```

Enable **warp-svc** service:

```bash
sudo systemctl enable --now warp-svc
```

Register the client:

```bash
warp-cli registration new
```

Connect:

```bash
warp-cli connect
```
