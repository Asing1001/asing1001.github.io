---
title: Build Puppeteer Docker image to run inside K8s cluster
date: 2022-07-27 12:57:15
tags: [K8s, Puppeteer, Docker]
---

## Background

- To run Puppeteer, you can't just use an official Nodejs image and npm install puppeteer
- Below is the Dockerfile that I have tried and proved as a working solution
- More information see the [Puppeteer official troubleshooting](https://github.com/puppeteer/puppeteer/blob/main/docs/troubleshooting.md#running-puppeteer-in-docker)

### Dockerfile

```bash
FROM alpine

# Installs latest Chromium (100) package.
RUN apk add --no-cache \
  chromium \
  nss \
  freetype \
  harfbuzz \
  ca-certificates \
  ttf-freefont \
  nodejs \
  yarn

# Tell Puppeteer to skip installing Chrome. We'll be using the installed package.
ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true \
  PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium-browser

COPY package.json yarn.lock ./
RUN yarn

# Puppeteer v13.5.0 works with Chromium 100.
# RUN yarn add puppeteer@13.5.0

# Add user so we don't need --no-sandbox.
RUN addgroup -S pptruser && adduser -S -G pptruser pptruser \
  && mkdir -p /home/pptruser/Downloads /app \
  && chown -R pptruser:pptruser /home/pptruser \
  && chown -R pptruser:pptruser /app

# Run everything after as non-privileged user.
USER pptruser

WORKDIR /app

COPY . .

EXPOSE 3003
CMD ["yarn", "start"]
```
