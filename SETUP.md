# FlexiFit Firebase Setup

Project: `flexifix-327a2` (Spark plan၊ အခမဲ့)

## ဖိုင်များ

| ဖိုင် | အကြောင်း |
|---|---|
| `public/index.html` | App အပြည့်အစုံ (Hosting ပေါ်တင်မည့်ဖိုင်) |
| `firestore.rules` | လုံခြုံရေးစည်းကမ်း |
| `firebase.json`, `.firebaserc` | Deploy လုပ်ရန် ဆက်တင် (project ချိတ်ပြီးသား) |

## အဆင့် ၁ — Console မှာ အရင်လုပ်ထားရမယ့်အရာ

1. **Firestore**: Standard edition၊ location `asia-southeast1`၊ Production mode ဖြင့် Create database။
2. **Authentication**: Get started → Sign-in method → **Email/Password** ကို Enable။
3. Authentication → Users → **Add user**: သင့် Admin email နဲ့ စကားဝှက်။

## အဆင့် ၂ — Deploy

ကွန်ပျူတာမှာ [Node.js](https://nodejs.org) (LTS) install လုပ်ပြီးရင် ဒီဖိုင်တွေရှိတဲ့ folder ထဲမှာ Terminal ဖွင့်ပါ။

```
npm install -g firebase-tools
firebase login
firebase deploy
```

`firebase deploy` က rules နဲ့ website နှစ်ခုလုံး တင်ပေးပါတယ်။ ပြီးရင် `https://flexifix-327a2.web.app` မှာ app ကို သုံးလို့ရပါပြီ။

Rules ကို CLI မသုံးဘဲ တင်ချင်ရင် Console → Firestore → **Rules** tab ထဲ `firestore.rules` ရဲ့ စာသားကို ကူးထည့်ပြီး Publish နှိပ်ပါ။ Website ကိုတော့ CLI နဲ့ပဲ တင်ရပါတယ်။

## အဆင့် ၃ — Admin အဖြစ် သတ်မှတ်ရန် (တစ်ကြိမ်ပဲ)

Admin ကို app ထဲကနေ သတ်မှတ်လို့မရပါဘူး။ Console မှာ လက်နဲ့ လုပ်ရပါမယ်။

1. Authentication → Users မှာ Admin user ရဲ့ **User UID** ကို ကူးပါ။
2. Firestore → **Start collection** → Collection ID `admins`။
3. Document ID နေရာမှာ အဲဒီ UID ကို ကူးထည့်ပါ။
4. Field: အမည် `ok`၊ type `boolean`၊ တန်ဖိုး `true`။ Save။

## အဆင့် ၄ — စတင်သုံးပါ

1. Website ကိုဖွင့်၊ **Admin** tab မှာ email နဲ့ ဝင်ပါ။
2. **Members** → "Member အသစ်": ဖုန်းနံပါတ်နဲ့ စတင်စကားဝှက် ထည့်ပါ။ အဲဒီနှစ်ခုကို Member ကို ပေးပါ။
3. **ဆက်တင်** → Gemini API key နဲ့ model code ထည့်ပါ (လိုရင်)။

## သိထားရမယ့်အချက်များ

- **Member ကို ဖျက်ရင်** စာရင်းထဲကပဲ ပျောက်ပါတယ်။ ဝင်ခွင့်မရတော့ပေမဲ့ Login account က Console → Authentication မှာ ကျန်နေပါတယ်။ သန့်ရှင်းအောင် အဲဒီမှာ ဖျက်ပါ။
- **ဖုန်းနံပါတ်ပြောင်းလို့ မရပါ**။ Login ကို ဖုန်းနံပါတ်နဲ့ ချိတ်ထားလို့ပါ။ ပြောင်းချင်ရင် Member အသစ်ပြန်ဖွင့်ပါ။
- **Gemini key** ကို Member app တွေက ဖတ်ရပါတယ်။ အခမဲ့ key ပဲ သုံးပါ။
- **စကားဝှက်မေ့ရင်** Console → Authentication မှာ Member ရဲ့ account ကို ဖျက်ပြီး Admin က Member ကို ပြန်ဖန်တီးပါ (Firebase ရဲ့ email reset က ဒီစနစ်မှာ အလုပ်မလုပ်ပါ)။

## ပြဿနာရှာဖွေခြင်း

| ပေါ်လာတာ | အဓိပ္ပာယ် |
|---|---|
| ချိတ်ဆက်မှု ပြဿနာ / ခွင့်ပြုချက် မရှိပါ | `firebase deploy` မလုပ်ရသေးလို့ rules မရှိဘူး၊ ဒါမှမဟုတ် `admins` document မဖန်တီးရသေးဘူး |
| `auth/invalid-email` | ကျွန်တော့်ဆီ screenshot ပို့ပါ (Member login ပုံစံကို ပြင်ရပါမယ်) |
| `auth/operation-not-allowed` | Authentication မှာ Email/Password ကို Enable မလုပ်ရသေးဘူး |
| Member စာရင်းထဲ မပါပါ | Login account ရှိပေမဲ့ `members` document မရှိဘူး |
