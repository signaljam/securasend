# Secura

Share anything in a link. Secrua uses end-to-end encryption, so nobody but you (and your recipient) can see what you share— not even us. All links automatically self-destruct when you want.

**Try it:** [securasend.com](https://securasend.com)

## About this project

Secura is a fork of [Send](https://github.com/timvisee/send) — originally developed by Mozilla and continued by [Tim Visée](https://github.com/timvisee/send) — maintained as the engine behind the Secura instance. We track upstream closely and regularly merge upstream fixes and improvements.

Differences from upstream include:

- Secura branding: wordmark, favicon, and color palette
- A hex-rain background theme (light and dark modes)
- Slight layout adjustments and custom CSS tweaks
- Hardened defaults tuned for a public instance, behind a [go-away](https://git.gammaspectra.live/git/go-away) challenge proxy

See [LICENSING.md](./LICENSING.md) for what you may reuse: the software is MPL-2.0 and fully forkable; the Secura name and brand assets are not.

## Features

- End-to-end encryption in the browser — the server can't read your files
- Links that expire by time or download count
- Optional password protection
- Dark mode

## Self-hosting

The quickest way to run Secura (or your own fork of it):

1. Pull the image:

   ```yaml
   services:
     send:
       image: ghcr.io/signaljam/securasend:latest
       restart: always
       volumes:
         - ./uploads:/uploads
       environment:
         - NODE_ENV=production
         - BASE_URL=https://your.domain
         - PORT=1234
         - REDIS_HOST=redis
         - FILE_DIR=/uploads
   ```

2. Bring your own Redis and reverse proxy (nginx, Caddy, or a Docker proxy such as [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy)).

3. `docker compose up -d`

Configuration is driven by environment variables — expiry times, download limits, and max file size are all tunable. The full set is documented in [`docs/docker.md`](./docs/docker.md).

If you fork this repository, please rebrand before deploying publicly — see [LICENSING.md](./LICENSING.md).

## Development

```bash
npm install
npm start
```

Requirements: Node.js and Redis. See the upstream [Send documentation](https://github.com/timvisee/send/tree/master/docs) for details.

## Credits

- [Send](https://github.com/timvisee/send) by Tim Visée and contributors
- The original [Mozilla Send](https://github.com/mozilla/send) team
- Secura modifications by Signal Jam

## License

The software in this repository is licensed under the [MPL-2.0](./LICENSE). The Secura name, wordmark, logos, and favicons are held by Signal Jam — see [LICENSING.md](./LICENSING.md).