
Bankga mijozlarining qarzni qaytarish prognozi.

Ushbu loyiha orqali bank mijozlarining qarzni qaytarish ehtimoli (Exited = 1) yoki 
qaytarmaslik ehtimoli (Exited = 0) sun'iy intellekt asosida oldindan aniqlab beriladi.

 Loyiha vazifasi
------------------
Loyihaning maqsadi — mavjud mijozlar haqidagi ma'lumotlarga asoslanib, ularning 
bankdan chiqib ketish yoki kreditni to'lamaslik xavfini bashorat qilish. 
Bu bank uchun risklarni oldindan aniqlash va profilaktik choralar ko‘rishga yordam beradi.

 Dataset haqida
-------------------
Ma'lumotlar quyidagi 3 ta CSV fayldan iborat:
- train.csv — O'rgatish uchun asosiy ma'lumotlar (Exited mavjud)
- test.csv — Bashorat qilish uchun test to'plami (Exited yo'q)
- sample_submission.csv — Yuboriladigan faylning namunasi

Ustunlar ro'yxati (avval inglizcha, so'ng o'zbekcha):
- id:              Qator tartib raqami
- CustomerId:      Mijoz ID raqami
- Surname:         Mijoz familiyasi
- CreditScore:     Kredit skori(kredit reytingi)
- Geography:       Yashash mamlakati (France, Germany, Spain)
- Gender:          Jinsi (Male/Female)
- Age:             Yoshi
- Tenure:          Bank bilan ishlagan yillari
- Balance:         Hisobdagi mablag'
- NumOfProducts:   Foydalanayotgan mahsulotlar soni
- HasCrCard:       Kredit kartasi mavjudligi (1/0)
- IsActiveMember:  Faol mijozmi (1/0)
- EstimatedSalary: Yillik daromad
- Exited:          Mijoz chiqib ketganmi (1 — ha, 0 — yo'q)

  Foydalanilgan kutubxonalar va texnologiyalar
-----------------------------------------------
- pandas, numpy — ma'lumotlar bilan ishlash
- matplotlib, seaborn — vizualizatsiya
- sklearn — model qurish, baholash, metrikalar
- catboost — asosiy ML modeli
- shap — modelni tushuntirish
- Google Colab — ish muhiti

  Qilingan ishlar
------------------
1. Ma'lumotlarni o'qish va tozalash
2. Statistik ko'rinish va tozalash
3. Kategorik ustunlarni kodlash (Geography, Gender)
4. Masshtablash (StandardScaler)
5. Modellarni solishtirish: LogisticRegression, RandomForest, XGBoost, LightGBM, CatBoost
6. ROC AUC, F1-score, confusion matrix
7. SHAP orqali tushuntirish
8. Test uchun bashorat
9. submission.csv tayyorlash

   Tanlangan model: CatBoostClassifier
---------------------------------------
- ROC AUC: 0.936
- F1-score: ~0.71

  Submission fayl
--------------------
Final natijalar quyidagicha CSV formatga yoziladi:
id,Exited
15000,0.8123
15001,0.1067
...

submission.csv yaratish kodi:

submission = pd.DataFrame({
    'id': test_ids,
    'Exited': model.predict_proba(X_test_scaled)[:, 1]
})
submission.to_csv('submission.csv', index=False)

   Ma'lumot manbasi
--------------------
Mohirdev tanlovi / Kaggle musobaqasi:
https://kaggle.com/competitions/binaryclassificationwithabankchurndataset

  Foydalanish
---------------
- Portfolio (GitHub, Upwork)
- Kompaniya uchun prototip
- Web-app yoki Telegram bot orqali foydalanish

