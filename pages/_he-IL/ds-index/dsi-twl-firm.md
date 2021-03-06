---
lang: he-IL
layout: wiki
section: ds-index
category: reference
title: Nintendo DSi / Nintendo 3DS TWL_FIRM
description: מידע בנושא הNintendo DSi והTWL_FIRM של הNintendo 3DS
---

### התקנת קושחה מותאמת אישית CFW
מאחר ורוב היתרונות של הקושחה המותאמת אישית הם עבור משפחת המערכות של הNintendo DSi והNintendo 3DS, זה מאפשר לכם לפתוח את כל האפשרויות של הקונסלות שלכם. התקנת קושחה מותאמת אישית היא יחסית קלה, וברוב המקרים כל מה שנדרש זה כרטיס (מיקרו) SD. יש לנו את המדריכים הטובים ביותר בשבילכם, עם הוראות שלב אחר שלב.

- [מדריך פריצה 3DS](https://3ds.hacks.guide)
   - פקודת Lightning: `mod 3ds`
   - פקודת Kuriisu: `guide 3ds`
- [מדריך פריצת DSi](https://dsi.cfw.guide)
   - פקודת Lightning: `mod dsi cfw`
   - פקודת Kuriisu: `guide dsi`

### מהירויות מעבד
הNintendo DS הגיע עם מעבד 67 MHz ב2004. הNintendo DSi הגיע עם מעבד של 133 MHz ב2009. רוב המשחקים בספריה של הNintendo DS נוצרו לפני שהNintendo DSi יצא, כתוצאה מכך המעבד היחיד שהיה להם זמין הוא 67 MHz. חלק מהתוכנות קשרו את עצמם למהירות השעון הזאת, כתוצאה מכך הם לא יעבדו כראוי עם מהירות שעון גבוהה יותר. בפועל, רוב המשחקים יעבדו בצורה טובה יותר מהמקור עם מהירות השעון הגבוהה יותר.

לnds-bootstrap יש את האופציה למהירות שעון של TWL, אבל הוא לא ינסה להתאים את הרום לעבודה עם המהירות הגבוהה יותר. ההתאמה תלויה בתוכנה עצמה, ותוכנות שלא עובדות עם מהירות השעון הגבוהה יותר לא נובעות מבאג בצד של nds-bootstrap.

### תפריט מערכת של Nintendo DSi
תפריט המערכת של הNintendo DSi משתמש במספר שלם בגודל 32 ביט על מנת לקבוע כמה זכרון פנוי יש למערכת. כשמשתמשים במקור שהוא גדול מהמגבלה של מספר שלם בגודל 32 ביט, המספר זולג למספר שלילי, שמוביל לקריסה המציגה מסך שחור עם הכיתוב "An error has occurred".

הטווחים שגורמים לו לזלוג נקבע על ידי זוגות של שתיים. לדוגמה, מקום פנוי בנפח של 1-2 GB מותר, בעוד שנפח של 3-4 GB לא. מקום פנוי בנפח של 5-6 GB מותר, בעוד שנפח של 7-8 GB לא.

קריסה זו לא תקרה במידה ותפריט המערכת עולה מרכיב NAND אמיתי (מאחר והנפח המקסימלי שלו הוא 128MB), אבל מערכת הכוונה מחדש (כמו hiyaCFW) יגרום לזה לקרות. למזלנו, ניתן לתקן את הבאג הזה בקלות על ידי קבצי דמה בשביל להעביר את הסופר למספר חיובי. זה קורה אוטומטית עם hiyaCFW בגרסה העדכנית שלו.

בגרסה 1.4.0 חתימות RSA ברשימה הלבנה של הקלטות DS לא נבדקות. יש פירצה הקשורה לפגיעות ברשימה הלבנה של הפלאשקארדים בNintendo DSi המאפשרת לנו לקבל שליטה על המעבד ARM9. זה דורש מכשיר בגרסה 1.4.0 (פירצה זו נחסמה בגרסות עתידיות, ולא הייתה קיימת בגרסות ישנות יותר) ופלאשקארט עם רום ערוך.

### גישה & חסימה לSlot-1 בNintendo DSi
גישה לSlot-1 נחסמת כאשר מריצים תוכנות מתפריט המערכת, מלבד המקרים בהם התוכנה עצמה היא המפעיל של Slot-1 או תפריט הגדרות המערכת. על מנת להפעיל קלטות slot-1 שלא ניתן להפעיל באופן רגיל, תצטרכו או פירצה בתפריט הגדרות המערכת או להתקין את Unlaunch. ללא אחד מאלה, לא תוכלו להפעיל פלאשקארדים שלא ניתן להפעיל ולא תוכלו לחלץ רומים לכרטיס הSD שלכם.

הרשימה הלבנה של הפלאשקארדים נבדקת על ידי חתימות RSA שמוכלות במפתחות RSA בכל קושחה מלבד 1.4.0. זאת אומרת שאנשים יוכלים להכניס את הקלטות שלהם לרשימה הלבנה

לפני גרסה 1.4.0, הרשימה הלבנה הכילה 2 חלקים. ב1.4.0, הם הוסיפו חלק נוסף שיועד לחסום פלאשקארדים שעקפו את שני החלקים הראשונים. החלק השלישי טוען עד שמונה חלקים שונים של הרום ובודק אותם מול hash בשביל לבדוק אם הרום שונה בצורה כלשהיא. למרות זאת, כתוצאה מהעובדה ששכחו לשים בדיקות שפיות, אנחנו יכולים לגרום להצפה לכתובת הההפרעה או וקטור החריגים באמצעות ערך גדול מספיק. החשוב מכל, זה פועל על ARM7 (המכונה גם מעבד האבטחה) ולכן זה הופך את זה לפריצה הראשונה עבור מעבד ARM7. מאחר וזה קורה לפני הנעילה של רישומי הSCFG, ניתן יהיה להריץ הומברו מתקדם (לדוגמת מחלצי Slot-1 & מחלצי slot-1 חיצוניים)

לרוע המזל, הדרישות לחוצות. זה דורש גרסה 1.4.0 ופלאשקארד עם רום שעבר שינוי. בנוסף, הפירצה מעולם לא יצאה באופן רשמי, מאחר וUnlaunch פשוט יותר להתקנה ובעל פחות דרישות (נדרשת רק דרך לגשת להומברו) עם אותם היתרונות.

### המצלמה של Nintendo DSi
התוכנה Nintendo DSi Camera בעלת יכולת לצלם תמונות בפורמט JPEG ולשמור אתם או לזכרון המערכת או לכרטיס SD. הצורה בה היא נטענת מגבילה אותה לתמונות שנוצרו על ידי DSi בלבד, כתוצאה מהעדר HMAC תקין שמאוחסן בתוך טאג הEXIF המותאם. כל תמונה מותאמת אישית לא קריאה על ידי הDSi, בין אם היא נלקחה מהמחשב או נערכה בו.

קובץ `pit.bin` משמש למען טעינת התמונות. אבל, גודל הheader בoffset 0x16 לא נבדק, כך שגודל header מספיק גדול יכול לעבור את המגבלות ולגרום לbuffer לכתוב מעבר ולקפוץ לקוד לא חתום. זאת הדרך שבה Memory Pit פועל.

### Nintendo DSi bootstage 2
שלב העליה השני של הNintendo DSi טוען את ה"title.tmd" של המפעיל לזכרון. אבל, הם לא בודקים את הגודל המקסימלי של הקובץ, כך ש80k הבתים הראשוניים נטענים לRAM והשאר יכולים להיות מטען מותאם אישית. זה הבסיס של פירצת הUnlaunch.

### RTCom
RTCom הוא השימוש בRTC של ה3DS לאפשר למעבדי הARM7 והARM11 לתקשר אחד עם השני, אפילו בתוך TWL_FIRM. זה מאפשר שימוש בפונקציות של ה3DS בזמן שהוא במצב DS(i). זה כולל את הקלט האנלוגי מהגויסטיק, הפעלה של מסך רחב, ותמיכה בגירוסקופ. כרגע, ההומברו הפומבי היחיד שמשתמש בRTCom הוא בניות מסויומות של GBARunner2 שכוללות תמיכה בגירו של ה3DS. על מנת לאפשר את RTCom, תצטרכו להשתמש ב[TWPatch](https://gbatemp.net/threads/542694/).
