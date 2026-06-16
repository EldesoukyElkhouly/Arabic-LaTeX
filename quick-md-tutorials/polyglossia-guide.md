# **دليل شامل لاستخدام حزمة `polyglossia` في LaTeX**

## **1. مقدمة عن `polyglossia`**
`polyglossia` هي حزمة في LaTeX تتيح الكتابة بلغات متعددة في نفس المستند، مع دعم مُحسَّن للغات غير اللاتينية مثل العربية والعبرية والفارسية والصينية وغيرها. تُعتبر البديل الحديث لـ `babel` في محركات LaTeX الحديثة مثل **XeLaTeX** و **LuaLaTeX**.

### **مميزات `polyglossia`:**
- دعم ممتاز للغات اليمين-إلى-يسار (RTL) مثل العربية.
- تكامل جيد مع الخطوط الحديثة (Unicode).
- توفير أوامر مخصصة للغات متعددة في نفس المستند.

---

## **2. تهيئة المستند لاستخدام `polyglossia`**
للاستفادة من `polyglossia`، يجب استخدام **XeLaTeX** أو **LuaLaTeX** بدلاً من pdfLaTeX.

### **البنية الأساسية:**
```latex
\documentclass{article}
\usepackage{polyglossia}

% تعيين اللغة الأساسية (الإنجليزية هنا)
\setdefaultlanguage{english}

% تعيين لغات إضافية (العربية مع خيارات RTL)
\setotherlanguage{arabic}
\newfontfamily\arabicfont[Script=Arabic]{Amiri} % خط عربي

\begin{document}

هذا نص عربي داخل مستند إنجليزي.

\end{document}
```

### **ملاحظات مهمة:**
- يجب تحديد خط يدعم اللغة (مثل `Amiri` أو `Traditional Arabic` للعربية).
- `\setdefaultlanguage` تحدد اللغة الأساسية للمستند.
- `\setotherlanguage` يُضيف لغات أخرى.

---

## **3. التبديل بين اللغات**
يمكنك التبديل بين اللغات باستخدام الأوامر التالية:

### **أمثلة:**
```latex
\begin{document}

\section{باللغة الإنجليزية}
This is an English text.

\begin{Arabic} % بداية بيئة عربية
\section{باللغة العربية}
هذا نص عربي بخط مناسب.
\end{Arabic}

\end{document}
```

### **أوامر التبديل السريع:**
| الأمر | الوصف |
|--------|-------|
| `\textarabic{نص}` | نص عربي داخل سطر إنجليزي |
| `\textenglish{text}` | نص إنجليزي داخل سطر عربي |
| `\selectlanguage{arabic}` | تغيير اللغة حتى نهاية المجموعة |

---

## **4. إعدادات متقدمة للغة العربية**
### **ضبط اتجاه النص (RTL):**
```latex
\usepackage{polyglossia}
\setotherlanguage{arabic}
\newfontfamily\arabicfont[Script=Arabic, Scale=1.5]{Amiri} % تكبير الخط 1.5x
```

### **خصائص إضافية للغة:**
```latex
\setotherlanguage[numerals=maghrib]{arabic} % الأرقام المغربية (١،٢،٣)
% أو:
\setotherlanguage[numerals=arabicdigits]{arabic} % الأرقام الغربية (1,2,3)
```

### **الخطوط المُوصى بها للعربية:**
- `Amiri`
- `Traditional Arabic`
- `Scheherazade`
- `Lateef`

---

## **5. كتابة مستند ثنائي اللغة**
### **مثال: إنجليزي-عربي**
```latex
\documentclass{article}
\usepackage{polyglossia}
\setdefaultlanguage{english}
\setotherlanguage{arabic}
\newfontfamily\arabicfont[Script=Arabic]{Amiri}

\title{وثيقة ثنائية اللغة}
\author{اسمك}

\begin{document}
\maketitle

\section{Introduction}
This is the English section.

\section{مقدمة}
\begin{Arabic}
هذه هي الفقرة العربية.
\end{Arabic}

\end{document}
```

### **نتيجة المحاذاة:**
- النص الإنجليزي: LTR (يسار إلى يمين).
- النص العربي: RTL (يمين إلى يسار) مع محاذاة صحيحة.

---

## **6. حلول لمشاكل شائعة**
### **المشكلة 1: الخط لا يظهر بشكل صحيح**
**الحل:** تأكد من:
1. استخدام **XeLaTeX** أو **LuaLaTeX**.
2. تثبيت الخطوط العربية على النظام.
3. تحديد الخط الصحيح في `\newfontfamily`.

### **المشكلة 2: الأرقام غير صحيحة**
**الحل:** اضبط خيار `numerals`:
```latex
\setotherlanguage[numerals=maghrib]{arabic} % للأرقام العربية
```

### **المشكلة 3: تنبيهات غير معروفة**
**الحل:** أضف حزمة `fontspec` قبل `polyglossia`:
```latex
\usepackage{fontspec}
\usepackage{polyglossia}
```

---

## **7. أمثلة إضافية**
### **نص مختلط مع إشارات مرجعية:**
```latex
\begin{document}

According to \textarabic{ابن خلدون}, history is cyclical.

\footnote{
  \textenglish{This is an English footnote.}
  \textarabic{هذه حاشية عربية.}
}

\end{document}
```

### **قوائم ثنائية اللغة:**
```latex
\begin{itemize}
    \item English item.
    \begin{Arabic}
    \item عنصر عربي.
    \end{Arabic}
\end{itemize}
```

---

## **8. خاتمة**
`polyglossia` تُعد أداة قوية للتعامل مع مستندات متعددة اللغات في LaTeX، خاصة للغات مثل العربية. لتحقيق أفضل النتائج:
1. استخدم **XeLaTeX** أو **LuaLaTeX**.
2. اختر خطوطًا تدعم Unicode.
3. جرب الخيارات المختلفة مثل `numerals` و `direction`.

### **روابط مفيدة:**
- [وثائق polyglossia](https://ctan.org/pkg/polyglossia)
- [قائمة الخطوط العربية لـ LaTeX](https://www.overleaf.com/learn/latex/Arabic)

