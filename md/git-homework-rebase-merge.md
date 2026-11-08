## Git မှာ merge နဲ့ rebase နှစ်ခုလုံးက Branch နှစ်ခုရဲ့ changes တွေကို ပေါင်းဖို့ သုံးတယ် ဒါပေမဲ့ Commit history ကို ကိုင်တွယ်ပုံ မတူဘူး

### 1. Git Merge
Branch နှစ်ခုရဲ့ history ကို မပြောင်းဘဲ ပေါင်းပေးတယ်

```bash
# Switch to main
git switch main

# Merge feature into main
git merge feature

# Force merge commit
git merge --no-ff feature

# Squash merge
git merge --squash feature

# Abort merge
git merge --abort
```

- Original commits တွေကို ထိန်းထားတယ်
- --no-ff သုံးရင် merge commit အသစ် ဖန်တီးတယ်
- Original branch history ကို preserve လုပ်တယ်

### 2. Git Rebase
Feature branch ရဲ့ commits တွေကို main ရဲ့ နောက်ဆုံး commit ပေါ်မှာ ပြန်တင်ပေးတယ်

```bash
# Switch to feature
git switch feature

# Rebase onto main
git rebase main

# Continue after resolving conflicts
git rebase --continue

# Skip current commit
git rebase --skip

# Abort rebase
git rebase --abort
```

- Commit history ကို ပြန်ရေးတယ် (Rewrite history)
- Commit hash အသစ်တွေ ဖြစ်လာတယ်
- History က linear ဖြစ်သွားတယ်
- Merge commit မလိုအပ်ဘူ:
  

### 3. Visual Comparison

#### Before
```bash
      D---E  feature
     /
A---B---C    main
```

#### After Merge
```bash
      D---E
     /     \
A---B---C---M  main
```

#### After Rebase
```bash
A---B---C---D'---E'  feature
        main
```
##### D' and E' = New commits with new hashes


## 4. Quick Comparison

| Merge                     | Rebase                          |
| ------------------------- | ------------------------------- |
| History ကို preserve လုပ်တယ်   | History ကို rewrite လုပ်တယ်          |
| Merge commit ရှိနိုင်တယ်        | Merge commit မရှိဘူး               |
| Non-linear history ဖြစ်နိုင်တယ် | Linear history ဖြစ်တယ်             |
| Shared branch အတွက်ပိုသင့်တော်တယ်  | Local feature branch အတွက်ပိုသင့်တော်တယ် |

## 5. ဘယ်အချိန်မှာသုံးရမလဲ

- **Merge** → Team shared branches တွေမှာ history မပြောင်းဘဲပေါင်းချင်တဲ့အခါ
- **Rebase** → ကိုယ့် local feature branch ကို main ရဲ့ latest changes နဲ့ update လုပ်ပြီး clean history လိုချင်တဲ့အခါ

> **Important:** Public/shared branch တွေကို Rebase မလုပ်ပါနဲ့။ တခြားသူတွေရဲ့ commit history ကို ရှုပ်ထွေးစေနိုင်တယ်

## အဓိက မှတ်ထားရန်

- `merge` → Branch နှစ်ခုရဲ့ history ကိုမပြောင်းဘဲပေါင်းတယ်
- `rebase` → ကိုယ့် commits တွေကို base အသစ်ပေါ်မှာ ပြန်တင်ပြီး history ကိုပြန်ရေးတယ်
- `--no-ff` → Fast-forward ဖြစ်နိုင်ရင်တောင် Merge commit ဖန်တီးတယ်
- `--squash` → Commits အများကြီးကို commit တစ်ခုတည်းအဖြစ်ပေါင်းတယ်