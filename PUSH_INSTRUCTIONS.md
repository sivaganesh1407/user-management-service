# Push to GitHub – Step by step

Your project is committed locally. Follow these steps to push and get a **project link** for LinkedIn.

---

## 1. Create a new repository on GitHub

1. Go to **https://github.com/new**
2. **Repository name:** `user-management-service` (or any name you like)
3. **Description (optional):** `REST API for user management – Spring Boot 4, JPA, H2`
4. Choose **Public**
5. Do **not** check “Add a README” or “Add .gitignore” (you already have them)
6. Click **Create repository**

---

## 2. Connect your local repo and push

GitHub will show you “push an existing repository from the command line.” Use your actual GitHub username in the URL.

**PowerShell (Windows):**

```powershell
cd "c:\Users\sivag\OneDrive\Documents\DevProjects\user-management-service"

git remote add origin https://github.com/YOUR_USERNAME/user-management-service.git
git branch -M main
git push -u origin main
```

Replace **YOUR_USERNAME** with your GitHub username (e.g. `johndoe`).

- If GitHub asks for login, use **Personal Access Token** as password (Settings → Developer settings → Personal access tokens).
- If you use SSH instead:  
  `git remote add origin git@github.com:YOUR_USERNAME/user-management-service.git`

---

## 3. Your project link

After a successful push, your project link will be:

```
https://github.com/YOUR_USERNAME/user-management-service
```

Use this URL in:
- **LinkedIn** → Add project → URL
- **LINKEDIN.md** – replace the placeholder with this link
- **docs/PROJECT_SHOWCASE.html** – replace “your-username” in the link text with your username, then open the file in a browser and take a screenshot if you want

---

## 4. Optional: Update the showcase link

Edit `docs/PROJECT_SHOWCASE.html` and change:

```html
<p class="link">🔗 github.com/your-username/user-management-service</p>
```

to (with your real username):

```html
<p class="link">🔗 github.com/YOUR_USERNAME/user-management-service</p>
```

Then commit and push again:

```powershell
git add docs/PROJECT_SHOWCASE.html
git commit -m "Update showcase link with GitHub username"
git push
```

Done. You can now share the repo link on LinkedIn and use **LINKEDIN.md** for post text and **docs/SCREENSHOTS_GUIDE.md** for screenshots.
