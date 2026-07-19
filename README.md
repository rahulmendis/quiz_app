# COM1301 Quiz Console

Self-contained, single-file interactive quiz app for COM1301 (Introduction to Computer Systems).

- 5 question banks, 290 questions total (3 lecture-module quizzes + 2 combined MCQ banks)
- Instant grading with per-section mark breakdown
- Question data is AES-256-GCM encrypted and decrypted client-side, so casual "view source" doesn't reveal the answer key
- No build step, no dependencies, no backend — it's just `index.html`

## Deploy on Vercel

1. Push this folder to a GitHub repo (see below).
2. Go to https://vercel.com/new and import the repo.
3. Framework preset: **Other** (Vercel will auto-detect a static `index.html` at the root — no build command, no output directory needed).
4. Click **Deploy**. Done — you'll get a live URL.

Any time you push new commits to the repo's default branch, Vercel redeploys automatically.

## Push to GitHub

```bash
cd com1301-quiz-console      # this folder
git init
git add .
git commit -m "Initial commit: COM1301 quiz console"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

Then import that repo on Vercel as above.

## Note on the encryption

The answer key is encrypted so it doesn't sit in plaintext in the page source. This stops casual cheating (view-source / Ctrl+F), but it isn't real security — the decryption key ships in the same file, so anyone willing to open devtools and run the decrypt function could still recover it. There's no way to fully hide client-side data without a server holding the key. If the repo is public, that same limitation applies on GitHub too — the ciphertext is visible, just not readable.
