# מדריך Git לצוות

## הקמה (אחראית ההקמה, פעם אחת)
1. יוצרים repo מהתבנית (Use this template) בחשבון שלה.
2. Settings > Collaborators: מוסיפות את חברות הצוות.
3. ממלאות ב-README את טבלת האחריות. עושות commit ו-push ל-main.
4. רק אחרי זה כל אחת עושה `git clone` ופותחת branch.

## סדר עבודה לכל אחת
```
git switch main
git pull
git switch -c part-c            # שם ה-branch לפי החלק שלך
# עובדות רק בקובץ ה-CSS שלך ובאזור שלך ב-index.html
git add css/part-c.css index.html
git commit -m "grid cards"      # commit קטן ותכוף
git fetch
git merge origin/main           # מביאות את העבודה של האחרות לתוך ה-branch שלך
git push -u origin part-c
```
אחר כך פותחות Pull Request ל-main בגיטהאב. אחראית ההקמה ממזגת (Merge). מי שסיימה ראשונה ממזגת ראשונה.
אחרי כל merge של מישהי אחרת: `git switch main && git pull`, ואז `git switch part-c && git merge main`.

## התנגשות (conflict) - מה עושים
1. לא נבהלות. התנגשות אומרת ששתיים שינו את אותן שורות.
2. `git status` - מראה קבצים עם "both modified".
3. פותחות את הקובץ ומחפשות `<<<<<<<`, `=======`, `>>>>>>>`.
4. קוראות את שתי הגרסאות ומדברות עם החברה שכתבה את השנייה.
5. מחליטות: שלי / שלה / שתיהן. מוחקות את שלושת הסימונים.
6. פותחות את index.html בדפדפן ובודקות שהעמוד תקין.
7. `git add <הקובץ>` ואז `git commit` ואז `git push`.
8. נתקעתן? `git merge --abort` מחזיר הכול. אסור `git push --force`.

טיפ: ב-VS Code לוחצים על Accept Current Change / Accept Incoming Change / Accept Both Changes מעל ההתנגשות.

## פקודות לראות מה השתנה (diff)
- `git diff` - מה שינית ועוד לא עשית add.
- `git diff --staged` - מה שמוכן ל-commit.
- `git diff main..part-c` - ההבדל בין branch ל-main.
- `git log --oneline --graph --all` - ציר הזמן של כל ה-branches.
