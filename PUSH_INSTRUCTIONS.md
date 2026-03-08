# Push to GitHub – Step by step

Your project is committed locally. Follow these steps to push and get a **project link** for LinkedIn.

---

## 1. Create a new repository on GitHub

1. Go to **https://github.com/new**
2. **Repository name:** `user-management-service`
3. **Description (optional):** `REST API for user management – Spring Boot, JPA, H2`
4. Choose **Public**
5. Do **not** check "Add a README" or "Add .gitignore" (you already have them)
6. Click **Create repository**

---

## 2. Connect your local repo and push

After creating the repo, GitHub shows "push an existing repository from the command line."

**Run these commands in your terminal:**

```bash
cd /Users/sivagolla/Downloads/user-management-service

git remote add origin https://github.com/sivagolla/user-management-service.git
git branch -M main
git push -u origin main
```

Replace **sivagolla** with your actual GitHub username if different.

- If GitHub asks for login, use **Personal Access Token** as password (Settings → Developer settings → Personal access tokens).
- If you use SSH instead:  
  `git remote add origin git@github.com:sivagolla/user-management-service.git`

---

## 3. Your project link

After a successful push, your project link will be:

```
https://github.com/sivagolla/user-management-service
```

Use this URL in:
- **LinkedIn** → Add project → URL
- **Resume** → Projects section
- **Portfolio** → GitHub link

---

## 4. Verify everything is uploaded

Visit your repo URL and check:
- README.md displays correctly with features and API table
- All source files are present under `src/`
- `.gitignore` is working (no `target/` folder uploaded)

---

## Quick Reference Commands

**Check commit history:**
```bash
git log --oneline
```

**Check remote connection:**
```bash
git remote -v
```

**Push future changes:**
```bash
git add .
git commit -m "Your commit message"
git push
```

Done! Your project is now live on GitHub and ready to share on LinkedIn.
