# מעקב משימות

טבלת משימות משותפת. כל מי שמקבל את הקישור יכול לצפות, להוסיף ולערוך, בלי הרשמה ובלי חשבון.
העמוד יושב ב-GitHub Pages, והנתונים נשמרים ב-Firebase (Firestore) במסלול החינמי.

## הקבצים

| קובץ | מה הוא עושה |
|---|---|
| `index.html` | הטבלה עצמה. לא צריך לגעת בו. |
| `firebase-config.js` | שם הטבלה ופרטי החיבור ל-Firebase. זה הקובץ היחיד שעורכים. |
| `firestore.rules` | חוקי האבטחה שמדביקים ב-Firebase (שלב 1.4). |

## התקנה (פעם אחת, כ-10 דקות)

### 1. מסד הנתונים ב-Firebase

1. נכנסים ל-[console.firebase.google.com](https://console.firebase.google.com) ומתחברים עם חשבון גוגל.
2. יוצרים פרויקט חדש (Create a project). נותנים לו שם, למשל `tasks-board`. אפשר לכבות את Google Analytics, ולוחצים Create.
3. בתפריט הצד בוחרים **Databases & Storage ← Firestore** (בממשק הישן: Build ← Firestore Database) ולוחצים **Create database**:
   - בוחרים **Standard edition**.
   - בוחרים מיקום. אפשר את ברירת המחדל, או `me-west1 (Tel Aviv)` אם הוא מופיע.
   - בוחרים **Start in production mode** ולוחצים Create.
4. עוברים ללשונית **Rules**, מוחקים את כל מה שכתוב שם, מדביקים את כל התוכן של `firestore.rules` ולוחצים **Publish**.
5. חוזרים לדף הבית של הפרויקט (Project Overview) ומוסיפים אפליקציית Web: לוחצים על האייקון `</>`, או על Add app ואז Web. נותנים כינוי ולוחצים Register app. לא צריך לסמן Firebase Hosting.
6. יופיע קוד עם בלוק שמתחיל ב-`const firebaseConfig = {`. מעתיקים את הבלוק הזה, מהשורה הזו ועד `};` כולל.

### 2. העלאה ל-GitHub Pages

1. ב-GitHub יוצרים מאגר חדש (New repository), למשל `tasks`, ומסמנים אותו **Public**.
2. לוחצים **Add file ← Upload files**, גוררים את כל הקבצים ולוחצים Commit changes.
3. פותחים במאגר את `firebase-config.js`, לוחצים על העיפרון (Edit) ומחליפים את הבלוק `const firebaseConfig = {...};` בבלוק שהעתקתם מ-Firebase. אם רוצים, משנים גם את `boardTitle`. לוחצים Commit changes.
4. ב-**Settings ← Pages**, תחת Source בוחרים **Deploy from a branch**, ואז Branch: `main` ותיקייה `/ (root)`. לוחצים Save.
5. אחרי דקה או שתיים יופיע שם הקישור, למשל `https://USERNAME.github.io/tasks/`. זה הקישור שמשתפים.

## טוב לדעת

- **ה-apiKey גלוי בקוד וזה בסדר:** ככה Firebase עובד באתרים. מה שמגן על המאגר הם החוקים שב-`firestore.rules`.
- **הרשאות:** כל מי שיש לו את הקישור יכול גם למחוק. לכן כדאי לשתף אותו רק עם מי שצריך. אחרי מחיקת משימה מופיע כפתור "ביטול" לכמה שניות.
- **סנכרון:** שינויים מופיעים אצל כולם תוך שנייה. בלי אינטרנט הטבלה ממשיכה לעבוד, והשינויים נשלחים כשהחיבור חוזר.
- **עלות:** המסלול החינמי של Firebase מספיק בשפע לצוות. הוא נותן עשרות אלפי קריאות וכתיבות ביום.
- **צפייה בנתונים:** אפשר לראות ולערוך את הנתונים ישירות ב-Firebase, בלשונית Data של Firestore (אוספים `tasks` ו-`people`).
