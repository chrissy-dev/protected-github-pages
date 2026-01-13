# Password Protection for Static Pages

A tiny, zero-configuration password gate for static websites.

This project provides a lightweight client-side barrier for static hosting platforms such as GitHub Pages, Amazon S3, Dropbox, or any generic file host. It is designed for temporary or low-risk use cases where you want to hide content from casual access without running a server.

It is intentionally simple, dependency-free, and works as a single HTML file.

## What this is good for

This project is useful when you need:

- A quick way to hide a static site behind a password
- No server, no backend, no database
- No build step or tooling
- Something you can upload anywhere and forget about
- A temporary gate for:
  - Client previews
  - Staging demos
  - Internal documentation
  - Personal pages you do not want indexed
  - Short-lived or ad-hoc sharing

It still gets visits because it solves a very specific problem with almost zero setup.

## What this is not

This is not real authentication and should not be treated as security.

It does not protect against:

- Determined attackers
- Brute-force attempts
- Anyone who already knows or guesses the URL
- Directory listing on misconfigured hosts

If you need real access control, use a backend, signed URLs, or platform-level authentication.


## How it works

- The password is hashed in the browser using SHA1
- The hash becomes the folder name
- The script attempts to load `{hash}/index.html`
- If the file exists, the user is redirected
- If it does not exist, access is denied

There is no server-side logic involved.


## Setup

1. Upload `index.html` to the root of your static hosting
2. Open it in a browser and enter your chosen password
3. You will see an “incorrect password” message
4. Copy the value after the `#` in the URL
5. Create a folder with that exact name
6. Put the content you want to protect inside it

Your final structure should look like:

```
├── index.html
├── background.jpg
└── this-is-a-hash    # SHA1 hash of your password
    └── index.html    # your original index document
```

That is it.


## Demo

Live demo: [chrissy-dev.github.io/protected-github-pages/](https://chrissy-dev.github.io/protected-github-pages/)  
Demo password: `password`


## Things to consider

- If directory listing is enabled, this can be bypassed
- Anyone with the direct hashed URL can skip the login
- There is no rate limiting or brute-force protection
- This is intentionally minimal and unopinionated

Treat it as a speed bump, not a lock.

## Project status

**This is an older project that I no longer actively use, but it remains available because:**

- It still solves a real, narrow problem
- It has no dependencies or ongoing maintenance burden
- People still find it useful for temporary setups

The scope will remain deliberately small.

## Credits

Original concept and early implementation inspired by [@matteobrusa](https://github.com/matteobrusa/Password-protection-for-static-pages)

