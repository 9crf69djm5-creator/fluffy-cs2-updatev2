# Fluffy-Cs2 update repo

Push this folder to a **new GitHub repo** so the loader can auto-update from it.

## 1. Create the repo on GitHub

1. Go to https://github.com/new
2. Name it whatever you want (e.g. `fluffy-cs2-update`)
3. Public, no README/license
4. Create repository

## 2. Push these files

From this folder (`github-update`):

```bash
git init
git add version.txt download_url.txt README.md
git commit -m "initial"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

(Replace YOUR_USERNAME and YOUR_REPO with your GitHub username and repo name.)

## 3. Edit download_url.txt for your repo

- Open `download_url.txt` in the repo on GitHub (edit file).
- Replace the URL with your real one. It must point to **CS2 External.exe**.
- Easiest: use **Releases**. Create a release (e.g. tag `1.0.0`), upload `CS2 External.exe`, then the URL is:
  `https://github.com/YOUR_USERNAME/YOUR_REPO/releases/download/1.0.0/CS2%20External.exe`
- For “always latest”: use tag `latest` or create a release named “latest” and use:
  `https://github.com/YOUR_USERNAME/YOUR_REPO/releases/latest/download/CS2%20External.exe`
  (GitHub redirects “latest” to the latest release.)

So `download_url.txt` should contain exactly one line: that URL.

## 4. version.txt

- One line, e.g. `1.0.0` or `1.0.1`.
- When you release a new build, bump this (e.g. to `1.0.1`) and push. Then create a new Release and upload the new `CS2 External.exe` (or add it to the “latest” release).

## 5. What customers use

They only need the **loader** (one exe). You give them:

- **update_config.txt** in the same folder as the loader, with:
  ```
  BaseUrl=https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO/main/
  ```
  (Use your real username and repo; if your default branch is `master`, use `/master/` instead of `/main/`.)

Then when they run the loader:

1. KeyAuth (they enter key)
2. Loader fetches `version.txt` from the URL above
3. If version is newer than their local one, it fetches `download_url.txt`, then downloads the exe from that URL and replaces their cheat
4. Loader launches the cheat

So: **one loader exe + update_config.txt** (you can send the config once or embed the URL in your build). No need for a separate updater unless you want it.

## 6. Releasing a new version

1. Bump `version.txt` in the repo (e.g. 1.0.0 → 1.0.1) and push.
2. On GitHub: Releases → create new release, tag e.g. `1.0.1`, upload the new `CS2 External.exe`.
3. If you use “latest”: upload the new exe to the release that has the “latest” tag (or create a new release and set it as latest).

After that, everyone with the loader and correct `update_config.txt` will get the update next time they run it.
