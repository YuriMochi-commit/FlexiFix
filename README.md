# FlexiFit

Gym member နဲ့ admin နှစ်မျိုးအတွက် ဖုန်း၊ tablet၊ desktop အားလုံးမှာ သုံးလို့ရတဲ့ gym management web app။
Member သက်တမ်း၊ ကိုယ်ပိုင် Goal၊ Intermittent Fasting နဲ့ AI အစားအသောက်လမ်းညွှန်တို့ကို တစ်နေရာတည်းမှာ စီမံနိုင်ပါတယ်။

> Firebase (Authentication + Firestore + Hosting) နဲ့ Gemini API ကိုသုံးထားပြီး backend server မလိုပါဘူး။ Firebase အခမဲ့ Spark plan ပေါ်မှာ အလုပ်လုပ်ပါတယ်။

<!-- Screenshot တွေကို ဒီမှာထည့်ပါ -->
<!-- ![Member home](docs/member-home.png) ![Admin dashboard](docs/admin-dashboard.png) -->

## Features

### Member
- **Member မှသာ ဝင်ခွင့်**: Gym ကစာရင်းသွင်းပေးထားတဲ့ ဖုန်းနံပါတ် + စကားဝှက်နဲ့ပဲ ဝင်လို့ရပါတယ်။
- **Member အမျိုးအစား**: Normal / Premium / PT Player ခွဲခြားပြသပါတယ်။ PT Player မှာ Trainer နဲ့ PT Session ကျန်ရေ ပါပါတယ်။
- **ကိုယ်ပိုင်အချက်အလက်**: အမြင့်၊ အလေးချိန်၊ BMI၊ ပန်းတိုင်အလေးချိန်၊ Goal။ အလေးချိန်မှတ်တမ်းနဲ့ graph ပါပါတယ်။
- **လစဉ်ရည်မှန်းချက်**: Gym လာမည့်ရက်နဲ့ အလေးချိန်ပြောင်းလဲမှုကို progress bar နဲ့ ပြပါတယ်။
- **Fasting Mode**: 14:10 / 16:8 / 18:6 / 20:4 / OMAD။ "ဒီနေ့ကစမယ်" ဒါမှမဟုတ် "ရက်ရွေးမယ်" ရွေးလို့ရပါတယ်။ Countdown၊ streak၊ နေ့စဉ်အောင်မြင်မှတ်ခြင်း ပါပါတယ်။
- **AI အစားအသောက်လမ်းညွှန်**: Goal၊ အလေးချိန်၊ Fasting အချိန်ကိုကြည့်ပြီး မြန်မာအစားအစာနဲ့ meal plan ထုတ်ပေးပါတယ်။
- **Membership alert**: သက်တမ်းကုန်ရန် ၁၄/၇/၃ ရက်အလိုနဲ့ ကုန်ဆုံးချိန်မှာ alert ပြပါတယ်။ Bell icon ကနေ ကြည့်လို့ရပါတယ်။
- Gym check-in၊ ဒီနေ့ class schedule၊ Gym ကြေညာချက်၊ စကားဝှက်ပြောင်းခြင်း၊ Dark / Light theme။

### Admin
- **Dashboard**: Member စုစုပေါင်း၊ အသုံးပြုနိုင်/ကုန်ခါနီး/ကုန်ဆုံး အရေအတွက်၊ ဒီနေ့ check-in၊ ခန့်မှန်းဝင်ငွေ။
- **Members**: ရှာ၊ filter၊ ထည့်၊ ပြင်၊ ဖျက်၊ သက်တမ်းတိုး။
- **သက်တမ်းကုန်ခါနီး**: ၁၄ ရက်အတွင်းကုန်မည့်သူစာရင်း၊ သတိပေးစာပို့၊ Member တောင်းဆိုထားတဲ့ သက်တမ်းတိုးကို မြင်ရခြင်း။
- **ကြေညာချက်**: Member အားလုံးထံ ပို့ခြင်း။
- **ဆက်တင်**: Gemini API key နဲ့ model သတ်မှတ်ခြင်း။

## Tech stack

| အပိုင်း | သုံးထားတာ |
|---|---|
| UI | HTML + CSS + vanilla JavaScript (ES modules)၊ framework နဲ့ build step မလိုပါ |
| Login | Firebase Authentication (Email/Password) |
| Database | Cloud Firestore (Standard edition) |
| Hosting | Firebase Hosting |
| AI | Google Gemini API (key မရှိရင် app ထဲက တွက်ချက်မှုကို သုံးပါတယ်) |
| Font | Noto Sans Myanmar၊ Space Grotesk (Google Fonts) |

## Repository ဖွဲ့စည်းပုံ

```
.
├── public/
│   └── index.html        # App တစ်ခုလုံး (HTML + CSS + JS)
├── firestore.rules       # Firestore လုံခြုံရေးစည်းကမ်း
├── firebase.json         # Hosting + rules deploy ဆက်တင်
├── .firebaserc           # Firebase project ID
├── SETUP.md              # Setup အဆင့်ဆင့်
└── README.md
```

## စတင်သုံးရန်

အသေးစိတ်ကို [SETUP.md](SETUP.md) မှာ ရေးထားပါတယ်။ အကျဉ်းချုပ်ကတော့ ဒီလိုပါ။

1. [Firebase Console](https://console.firebase.google.com) မှာ project ဖွင့်ပါ။ Firestore (Standard edition) ကို ဖန်တီးပါ၊ Authentication မှာ **Email/Password** ကို Enable လုပ်ပါ။
2. `public/index.html` ထဲက `firebaseConfig` ကို သင့် project ရဲ့ တန်ဖိုးတွေနဲ့ အစားထိုးပါ။ `.firebaserc` ထဲက project ID ကိုလည်း ပြောင်းပါ။
3. Admin user တစ်ယောက်ကို Authentication ထဲမှာ ထည့်ပါ။ ပြီးရင် Firestore မှာ `admins` collection ဖန်တီးပြီး အဲဒီ user ရဲ့ **UID** ကို Document ID အဖြစ်ထည့်ကာ `ok: true` field ထည့်ပါ။
4. Deploy လုပ်ပါ။

```bash
npm install -g firebase-tools
firebase login
firebase deploy
```

5. `https://<project-id>.web.app` ကိုဖွင့်ပြီး Admin tab မှာ ဝင်ပါ။ Members tab မှာ Member တွေကို ထည့်ပါ။
6. (လိုရင်) ဆက်တင်မှာ [Google AI Studio](https://aistudio.google.com) က Gemini API key နဲ့ model code ထည့်ပါ။

## Data model (Firestore)

| Collection / Doc | အကြောင်း |
|---|---|
| `admins/{uid}` | Admin သတ်မှတ်ချက်။ `ok: true`။ Console မှာသာ လက်ဖြင့်ဖန်တီးပါ |
| `members/{uid}` | Member တစ်ယောက်ချင်းစီ (doc ID က Auth UID) |
| `announcements/{id}` | Gym ကြေညာချက် (`text`, `date`) |
| `settings/ai` | Gemini `key` နဲ့ `model` |

`members/{uid}` ထဲက field တွေ: `name, phone, sex, age, tier, start, months, height, weight, targetWeight, goal, trainer, ptLeft, wlog[], att[], goalsM{}, fast{}, notes[], renewReq, createdAt`။

သက်တမ်းကုန်ရက် = `start` + `months`။ ကျန်ရက်ကို app က နေ့စဉ်တွက်ပါတယ်။

## လုံခြုံရေး

- Member က ကိုယ့်စာရင်းကိုပဲ ဖတ်နိုင်ပါတယ်။ ပြင်ခွင့်ရှိတာက `weight, height, targetWeight, goal, goalsM, wlog, att, fast, renewReq` ပဲဖြစ်ပါတယ်။ `tier`၊ `start`၊ `months`၊ `phone` ကို Admin ပဲ ပြင်နိုင်ပါတယ်။
- Admin ဆိုတာ `admins` collection မှာ document ရှိသူပဲ ဖြစ်ပြီး app ထဲကနေ ထည့်လို့မရပါဘူး။
- `firebaseConfig` ထဲက `apiKey` က လျှို့ဝှက်ချက် မဟုတ်ပါဘူး၊ Firebase project ကို ဖော်ပြတဲ့ ID ပါ။ ကာကွယ်မှုက `firestore.rules` ကနေ လာတာပါ။
- **Admin ရဲ့ email၊ စကားဝှက်၊ Gemini API key ကို repository ထဲ မထည့်ပါနဲ့။** Gemini key ကို app ရဲ့ ဆက်တင်ကနေ Firestore ထဲမှာ သိမ်းပါတယ်၊ code ထဲမှာ မရှိပါဘူး။

## သိထားရမယ့် ကန့်သတ်ချက်များ

- **Gemini key** ကို Member app တွေက Firestore ကနေ ဖတ်ရပါတယ်။ အခမဲ့ key ပဲသုံးပါ၊ ငွေပေးရတဲ့ key မထည့်ပါနဲ့။ ပိုလုံခြုံချင်ရင် Cloud Function (Blaze plan) နဲ့ ကြားခံပါ။
- **Member ဖျက်ရင်** Firestore စာရင်းကပဲ ပျောက်ပါတယ်။ Authentication ထဲက login account ကို Console မှာ ဖျက်ပေးရပါမယ်။
- **ဖုန်းနံပါတ်ပြောင်းလို့ မရပါ**။ Login id နဲ့ ချိတ်ထားလို့ပါ။
- **စကားဝှက်မေ့ရင်** Email reset မရပါ (Member login က ဖုန်းနံပါတ်အခြေပြုလို့ပါ)။ Console မှာ account ဖျက်ပြီး Admin က ပြန်ထည့်ပေးရပါမယ်။
- **PT Session ကျန်ရေ** က အလိုအလျောက် မလျော့ပါ။ Admin က ကိုယ်တိုင်ပြင်ရပါတယ်။
- **Alert** တွေက app ဖွင့်မှ ပေါ်ပါတယ်။ ဖုန်းကို push notification မပို့နိုင်သေးပါ။
- Member ဖန်တီးတဲ့အခါ Admin ရဲ့ browser ကနေ Firebase Auth ကို တိုက်ရိုက်ခေါ်ပါတယ်။ အကြီးစား (member ရာချီ) ဆိုရင် Admin SDK သုံးတဲ့ Cloud Function ပြောင်းသင့်ပါတယ်။

## Roadmap

- [ ] Gemini ကို Cloud Function ကနေ ခေါ်ခြင်း (key ကို Member မမြင်စေရန်)
- [ ] သက်တမ်းကုန်ခါနီး Push notification (FCM)
- [ ] PT Session "-၁" ခလုတ်နဲ့ အလိုအလျောက်လျှော့ခြင်း
- [ ] QR Check-in
- [ ] KBZPay / Wave Pay ပေးချေမှုနဲ့ သက်တမ်းတိုးမှတ်တမ်း
- [ ] PT Player အတွက် Trainer သတ်မှတ်တဲ့ Workout Plan
- [ ] အင်္ဂလိပ် / မြန်မာ ဘာသာစကားပြောင်းခလုတ်
- [ ] PWA (ဖုန်းမှာ app လို install လုပ်ရန်)

## License

<!-- သင့်ရွေးချယ်မှုကို ဒီမှာ ထည့်ပါ (ဥပမာ MIT)။ မရွေးရသေးရင် အခြားသူများ ဒီ code ကို ပြန်သုံးခွင့် မရှိပါဘူး။ -->
