# docs

Documentation of random things for my own and other people's purposes.

If you are here to read rather than contribute, you may prefer to look at the
[rendered site](https://scode.github.io/docs/).

## Development

```bash
./bin/build
dprint fmt
dprint check
```

## Publishing

This book is deployed by GitHub Actions using an artifact-based GitHub Pages workflow in `.github/workflows/deploy.yml`.

Generated build output in `/book/` is intentionally not tracked in git.
