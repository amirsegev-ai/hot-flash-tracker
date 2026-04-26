# 📋 מדריך הגדרת Google Cloud למעקב גלי חום

**זמן משוער:** 10-15 דקות (פעם אחת בלבד)

---

## שלב 1: יצירת פרויקט ב-Google Cloud

1. היכנסי ל: **https://console.cloud.google.com/**
2. התחברי עם חשבון Google שבו תרצי שהגיליון יישמר
3. בסרגל העליון לחצי על **Select a project** → **New Project**
4. שם הפרויקט: `Hot Flash Tracker` (או כל שם אחר)
5. לחצי **Create**
6. המתיני כמה שניות שהפרויקט יווצר, ואז בחרי אותו מהרשימה

---

## שלב 2: הפעלת APIs

1. בתפריט הצד (☰ בצד שמאל למעלה): **APIs & Services** → **Library**
2. חפשי **Google Sheets API** → לחצי עליו → **Enable**
3. חזרי ל-Library, חפשי **Google Drive API** → **Enable**

---

## שלב 3: OAuth Consent Screen

1. בתפריט: **APIs & Services** → **OAuth consent screen**
2. בחרי **External** → **Create**
3. מלאי:
   - **App name:** Hot Flash Tracker
   - **User support email:** כתובת הג'ימייל שלך
   - **Developer contact:** כתובת הג'ימייל שלך
4. **Save and Continue**
5. במסך Scopes - פשוט **Save and Continue**
6. במסך Test users - לחצי **Add Users** והוסיפי את כתובת הג'ימייל שלך
7. **Save and Continue** → **Back to Dashboard**

> ⚠️ חשוב: כל עוד האפליקציה ב-"Testing mode" היא תעבוד רק עבור המשתמשים שמוגדרים כ-Test users. זה מושלם לשימוש אישי.

---

## שלב 4: יצירת OAuth Client ID

1. בתפריט: **APIs & Services** → **Credentials**
2. לחצי **+ Create Credentials** → **OAuth client ID**
3. **Application type:** Web application
4. **Name:** Hot Flash Tracker Web
5. **Authorized JavaScript origins** - הוסיפי את הכתובות שמהן תריצי את האפליקציה:
   - אם תריצי מקומית לבדיקה: `http://localhost:8000`
   - אם תעלי לאירוח אמיתי: הכתובת של האתר (למשל `https://yourname.github.io`)
   - **חשוב:** ללא `/` בסוף הכתובת
6. לחצי **Create**
7. ייפתח חלון עם **Client ID** - העתיקי אותו ושמרי במקום בטוח
   (נראה משהו כמו: `123456789-abc...xyz.apps.googleusercontent.com`)

---

## שלב 5: מה עושים עם ה-Client ID?

1. תחזרי אליי עם ה-Client ID
2. אני אכניס אותו לאפליקציה
3. בפעם הראשונה שתפתחי את האפליקציה - היא תבקש הרשאה לגשת ל-Google Drive שלך
4. מרגע שאושר - האפליקציה תיצור אוטומטית גיליון Google Sheets חדש בשם `Hot Flash Tracker Data` ותעדכן אותו בכל פעם שתזיני נתונים

---

## 🔒 פרטיות ואבטחה

- הנתונים נשמרים רק בחשבון Google שלך
- רק את יכולה לראות את הגיליון
- האפליקציה לא שולחת מידע לאף שרת אחר
- ה-Client ID לא מסוכן אם מישהו רואה אותו (הוא לא סיסמה)

---

## ❓ שאלות נפוצות

**מה אם אני רוצה להריץ את זה בטלפון כ-PWA?**
- אחרי שנעלה את האפליקציה לאירוח (GitHub Pages / Netlify), נוסיף גם את הכתובת הזאת כ-Authorized Origin
- פותחים את האתר בטלפון → Chrome / Safari → "Add to Home Screen"

**מה אם משהו משתנה ב-API של גוגל?**
- Claude יעזור לעדכן את הקוד. תעדכני אותי אם משהו מפסיק לעבוד.

**צריך לשלם משהו?**
- לא. השימוש ב-Sheets/Drive API למעקב אישי הוא חינמי לגמרי וכולל מכסה נדיבה מאוד.
