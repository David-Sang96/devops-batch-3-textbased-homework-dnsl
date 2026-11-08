### Time Travel ဆိုတာ အရင် commit တွေကို ပြန်သွားတာ changes တွေကို undo လုပ်တာ commit history ကို ပြန်ပြင်တာတွေကို ဆိုလိုတာပါ

## 1. View Commit History

```bash
# View commit history
git log

# Compact commit history
git log --oneline

# Show commit graph
git log --oneline --graph --all

# Show last 5 commits
git log -5
```

## 2. Git Reset
 Commit တွေကို နောက်ပြန်ရွှေ့ချင်တဲ့အခါ သုံးတယ်

```bash
# Undo last commit, keep changes staged
git reset --soft HEAD~1

# Undo last commit, keep changes unstaged
git reset --mixed HEAD~1

# Undo last commit and discard changes
git reset --hard HEAD~1

# Reset to specific commit
git reset --hard <commit-hash>
```

- --soft → Changes ကို staging area မှာထားတယ်
- --mixed → Changes ကို working directory မှာထားတယ် (Default)
- --hard → Changes တွေကိုပါ ဖျက်တယ်

## 3. Git Revert
Commit တစ်ခုကို history မဖျက်ဘဲ ပြန် undo လုပ်ချင်တဲ့အခါ သုံးပါတယ်

```bash
# Revert last commit
git revert HEAD

# Revert specific commit
git revert <commit-hash>

# Revert without creating commit immediately
git revert --no-commit <commit-hash>
```

- Original commit ကို မဖျက်ဘူး
- Undo လုပ်ပေးမယ့် commit အသစ်တစ်ခု ဖန်တီးတယ်
- Shared branches မှာ ပိုလုံခြုံတယ်

## 4. Git Checkout / Switch
အရင် commit သို့မဟုတ် branch ကို ပြန်သွားကြည့်ချင်တဲ့အခါသုံးတယ်

```bash
# Switch to another branch
git switch main

# Go back to previous branch
git switch -

# View specific commit (detached HEAD)
git checkout <commit-hash>

# Return to main
git switch main
```

## 5. Git Restore
File changes တွေကို undo လုပ်ချင်တဲ့အခါသုံးတယ်

```bash
# Discard unstaged changes in a file
git restore filename

# Unstage a file
git restore --staged filename

# Restore file from specific commit
git restore --source=<commit-hash> filename
```

## 6. Git Reflog

ကိုယ်လုပ်ခဲ့တဲ့ HEAD movements တွေကို ပြန်ကြည့်နိုင်တယ် Reset လုပ်ပြီး ပျောက်သွားတဲ့ commit တွေကို ပြန်ရှာရာမှာ အသုံးဝင်တယ်

```bash
# View HEAD history
git reflog

# Reset to previous HEAD position
git reset --hard HEAD@{1}
```

### အဓိက မှတ်ထားရန်
- reset → Branch pointer ကို အရင် commit ဆီ ပြန်ရွှေ့တယ်
- revert → Changes တွေကို ပြန်ဖျက်ဖို့ commit အသစ်တစ်ခု ဖန်တီးတယ်
- restore → File ထဲက changes တွေကို ပြန်ဖျက်တယ်
- reflog → အရင်က HEAD ရောက်ခဲ့တဲ့ နေရာတွေကို ပြန်ကြည့်ပြီး commit တွေကို ပြန်ရှာနိုင်တယ်


## Quick Reference

| Command                           | Purpose                         |
| --------------------------------- | ------------------------------- |
| `git log --oneline`               | View commit history             |
| `git log --oneline --graph --all` | View commit graph               |
| `git reset --soft HEAD~1`         | Undo commit, keep staged        |
| `git reset --mixed HEAD~1`        | Undo commit, keep unstaged      |
| `git reset --hard HEAD~1`         | Undo commit, discard changes    |
| `git reset --hard <commit-hash>`  | Reset to specific commit        |
| `git revert HEAD`                 | Undo last commit safely         |
| `git revert <commit-hash>`        | Revert specific commit          |
| `git restore filename`            | Discard file changes            |
| `git restore --staged filename`   | Unstage file                    |
| `git switch -`                    | Switch to previous branch       |
| `git checkout <commit-hash>`      | Visit specific commit           |
| `git reflog`                      | View HEAD history               |
| `git reset --hard HEAD@{1}`       | Reset to previous HEAD position |