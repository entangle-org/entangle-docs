# Entangle Hotfix Protocol

This document describes the process to follow whenever a hotfix is made directly to the `master` branch.

---

## 🔥 When to Use This

- You apply a critical fix directly to `master`
- You bypass the normal `dev → master` release flow (e.g., for emergency patches)

---

## ✅ Steps After a Hotfix to Master

1. **Complete the hotfix.**
   - Create a hotfix branch (`hotfix/your-description`)
   - Merge it into `master`
   - Push changes to GitHub

2. **Immediately sync `master` into `dev`.**
   - Switch to `dev` branch:

     ```bash
     git checkout dev
     ```

   - Pull or merge the latest from `master`:

     ```bash
     git pull origin master
     ```

   - Resolve any merge conflicts (rare if hotfixes are clean)

   - Push the updated `dev`:

     ```bash
     git push origin dev
     ```

3. **Continue normal development.**
   - Future features are built from the now-updated `dev`
   - Future releases will cleanly merge `dev → master`

---

## 🧠 Why This Matters

| Reason | Explanation |
|--------|-------------|
| Avoids merge conflicts | `dev` stays fully aligned with latest `master` changes |
| Ensures stability | New features are based on the most recent production code |
| Keeps release flow smooth | `release.sh` assumes `dev` is ahead of `master`, not behind |

---

## 🔔 Quick Reminder

Always update `dev` **immediately** after any master hotfix to avoid branch drift.

```bash
git checkout master
git pull
git checkout dev
git merge master 
git commit
git push
```