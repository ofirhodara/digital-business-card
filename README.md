# כרטיס ביקור דיגיטלי

אתר כרטיס ביקור אישי — **HTML + CSS בלבד, ללא JavaScript**.

🔗 **אתר חי:** https://ofirhodara.github.io/digital-business-card/

## קבצים

| קובץ | תפקיד |
|---|---|
| `index.html` | מבנה סמנטי (header, nav, main, section, article, footer) |
| `style.css` | כל העיצוב — קובץ חיצוני נפרד, אין `style=` ואין `<style>` ב-HTML |
| `assets/profile.svg` | תמונת פרופיל |
| `.github/workflows/deploy.yml` | פריסה אוטומטית ל-GitHub Pages בכל push |

## אינטראקטיביות ללא JavaScript

| רכיב | המנגנון |
|---|---|
| מצב כהה/בהיר | `<input type="checkbox">` מוסתר לפני `.page`, והסלקטור `.theme-input:checked ~ .page` מחליף את משתני ה-CSS |
| טאבים בכישורים | שלושה `radio` לפני הפאנלים + `#tab-x:checked ~ .tabs__panels .panel--x` |
| חלונות פרויקט | `.modal:target` — קישור `#modal-name` פותח, `#projects` סוגר |
| אקורדיון | תגית `<details>` נייטיב |
| מדדי כישורים | `@keyframes grow` עד `var(--lvl)`; האחוזים במחלקות `.lvl-90` ולא בעיצוב פנימי |

**חשוב:** כל הסלקטורים לעיל מבוססים על סדר האחים ב-DOM (`~`) — אסור להזיז את ה-`input` אחרי האלמנט שהוא משפיע עליו.

## רספונסיביות

רוב ההתאמה קורית ללא media queries — `repeat(auto-fit, minmax(...))` ו-`flex-wrap`.
מעליהן ארבע נקודות שבירה: 1040px (שוליים), 820px (הכרטיס לעמודה), 620px (ניווט וסרגלי כישורים), 380px (סטטיסטיקות 2×2).
הטיפוגרפיה זורמת עם `clamp()`. כמו כן: `prefers-reduced-motion` וגרסת הדפסה.

## פריסה

הפריסה אוטומטית דרך GitHub Actions — כל push ל-`main` מפעיל את `deploy.yml`
(מקור ה-Pages מוגדר ל-**GitHub Actions**, לא ל-branch). מעקב בלשונית **Actions** ברפו.

```bash
git add . && git commit -m "..." && git push
```

## פרטים להחלפה (כרגע פרטים בדויים, כפי שהמטלה מתירה)

בקובץ `index.html`:
- טלפון: `tel:+972501234567` + הטקסט המוצג
- אימייל: `mailto:ofir.dev@example.com` (2 מקומות: כרטיס הקשר + כפתור הבאנר)
- תמונה: להחליף את `assets/profile.svg` בתמונה אישית ולעדכן את `src` ואת ה-`alt`
