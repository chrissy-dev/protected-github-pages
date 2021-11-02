# Password protection for static pages

Very simple password protection to static pages or whole websites with no server configuration required: you ca use Dropbox, Amazon S3 or any generic hosting service to host a private, password protected site.

### [Check out the demo](https://scottishstoater.github.io/protected-github-pages/) 
>Password is: password

## Setup

- Upload the `index.html` document to the root of your static hosting service.
- Load it up in your browser, enter the password of your choice
- It will show "wrong password", never mind. Copy the section of the URL after the # sign.
- Create a folder with that name next to the `index.html` file
- Upload the content that you want to protect inside the folder

The final structure will be:

```
- index.html
- background.jpg
- this-is-a-hash      <-- the SHA1 hash of your password
  \ - index.html      <-- your original index document
```

### Things to consider 

- If your hosting service offers directory listing, a visitor can bypass the protection.
- there's no protection against brute force attack. Pick a very long and hard to guess password.
- Pasting the link directly to someone will bypass the login

> Credit to [@matteobrusa](https://github.com/matteobrusa/Password-protection-for-static-pages) for his initial findings and implementation.
