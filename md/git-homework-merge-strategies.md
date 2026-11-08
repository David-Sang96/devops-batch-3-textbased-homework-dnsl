# Git Cheat Sheet

## Merge Strategies
 Merge strategies ‌‌တွေက အဓိကအားဖြင့် ၃ မျိုးရှိတယ်

1. Fast-Forward Merge (--ff)
2. Three-Way Merge (--no-ff)
3. Squash Merge (--squash)


### Fast-Forward Merge (--ff)
Feature branch မှာ commit အသစ်တွေရှိပြီး main branch မှာ commit အသစ်မရှိတဲ့အခါ အသုံးပြုတယ်

```bash
git switch main
git merge feature
```

- Merge commit အသစ် မဖန်တီးဘူး
- Main ရဲ့ pointer ကို feature ရဲ့ နောက်ဆုံး commit ဆီ ရွှေ့ပေးတယ်
- History က linear ဖြစ်နေတယ်။
- Default behavior (--ff) --ff ကိုမထည့်လဲရတယ် default မို့လို့ 
- Fast-forward ဖြစ်နိုင်ရင် Fast-forward လုပ်တယ် မဖြစ်နိုင်ရင် Three-way merge လုပ်တယ်


### Three-Way Merge (--no-ff)
Main နဲ့ feature branch နှစ်ခုလုံးမှာ commit အသစ်တွေရှိတဲ့အခါ အသုံးပြုတယ်

```bash
git switch main
git merge --no-ff feature
```

- Fast-forward ဖြစ်နိုင်တဲ့အခြေအနေမှာတောင် Fast-forward မလုပ်ဘဲ Merge commit အသစ် ကို အတင်းဖန်တီးတယ်
- --ff က Git ရဲ့ default behavior ဖြစ်ပြီး --no-ff က အဲဒီ default behavior ကို override လုပ်တယ်
- Branch merge လုပ်ခဲ့တာကို history မှာ ရှင်းရှင်းလင်းလင်း မြင်ရတယ်

### Squash Merge (--squash)
Feature branch ထဲက commit အားလုံးကို commit တစ်ခုတည်းအဖြစ် ပေါင်းပြီး main ထဲထည့်တယ်

```bash
git switch main
git merge --squash feature
git commit -m "Add feature"
```

- Feature branch ရဲ့ commits အားလုံးကို တစ်ခုတည်းအဖြစ် ပေါင်းတယ်
- Merge commit မဖန်တီးဘူး
- ain history ကို clean ဖြစ်စေတယ်
- Original feature commits တွေကို main history ထဲမှာ သီးခြားမမြင်ရဘူး


## ဘယ်အချိန်မှာ ဘာသုံးမလဲ
- Fast-forward → Simple feature changes, linear history လိုချင်တဲ့အခါ
- Three-way → Feature branch history ကို preserve လုပ်ချင်တဲ့အခါ
- Squash → Feature branch ထဲက messy commits တွေကို main မှာ commit တစ်ခုတည်းအဖြစ် ထည့်ချင်တဲ့အခါ