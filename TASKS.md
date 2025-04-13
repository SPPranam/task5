# 🚀 TASK 4 - DevOps Git Workflow Documentation

## 🧰 Project Setup
- Initialized Git repo locally
- Connected it to GitHub at: [GitHub Repo Link](https://github.com/SPPranam/task4.git)
- Created a basic Node.js app with Express

---

## 🌱 Git Branching Workflow
- `main` → main production branch
- `dev` → development branch for testing and combining features
- `feature/docker` → added Docker support
- All changes done through pull requests (PRs)

---

## 🔀 Pull Requests
- Created PR: `feature/docker` → `dev` ✅
- Merged PR: `dev` → `main` ✅

---

## 📦 Docker Integration
- Added Dockerfile to containerize the Node.js app
- Dockerfile uses Node 18 base image
- Application runs on port 3000

---

## 📝 Project Files Added
- `app.js` – Basic Express server
- `Dockerfile` – Container config
- `README.md` – Project info & instructions
- `.gitignore` – Ignored node_modules, logs, etc.
- `TASKS.md` – Documentation of Git workflow

---

## 🔖 Git Tags
- `v1.0` – First stable version
- Command used:
  ```bash
  git tag -a v1.0 -m "First stable version"
  git push origin v1.0

