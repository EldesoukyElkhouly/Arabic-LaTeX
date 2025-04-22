# **شرح سريع لـ LaTeX**


# **دليل شامل لـ LaTeX**

## **المحتوى**
1. [مقدمة إلى LaTeX](#مقدمة-إلى-latex)
2. [إنشاء مستند LaTeX أساسي](#إنشاء-مستند-latex-أساسي)
3. [تنسيق النص](#تنسيق-النص)
4. [العناوين والأقسام](#العناوين-والأقسام)
5. [القوائم](#القوائم)
6. [الرياضيات والمعادلات](#الرياضيات-والمعادلات)
7. [الجداول](#الجداول)
8. [الصور والأشكال](#الصور-والأشكال)
9. [المراجع والفهارس](#المراجع-والفهارس)
10. [أمثلة متقدمة](#أمثلة-متقدمة)

---

## **1. مقدمة إلى LaTeX**
**LaTeX** هو نظام لتحضير المستندات يعتمد على لغة ترميز، ويُستخدم بكثرة في الأبحاث العلمية والكتب الأكاديمية بسبب دقته في تنظيم المحتوى، وخاصة في كتابة المعادلات الرياضية.

### **مميزات LaTeX:**
- يدعم المعادلات الرياضية المعقدة.
- إدارة تلقائية للفهارس والمراجع.
- مستندات ذات جودة طباعية عالية.
- مجاني ومفتوح المصدر.

### **عيوب LaTeX:**
- منحنى تعلم حاد مقارنةً ببرامج مثل Word.
- يحتاج إلى وقت أطول لتحرير المستندات البسيطة.

---

## **2. إنشاء مستند LaTeX أساسي**
```latex
\documentclass{article} % نوع المستند (article, report, book, etc.)
\usepackage[utf8]{inputenc} % دعم اللغة العربية
\usepackage{arabtex} % لحزمة العربية (إذا لزم الأمر)
\usepackage{graphicx} % لإدراج الصور

\title{عنوان المستند}
\author{اسم المؤلف}
\date{\today}

\begin{document}

\maketitle % إنشاء العنوان

\section{مقدمة}
هذا مستند LaTeX بسيط.

\end{document}
```

### **ملاحظات:**
- `\documentclass` تحدد نوع المستند (`article`, `report`, `book`, `beamer` للعروض).
- `\usepackage` تُستخدم لإضافة حزم إضافية مثل `amsmath` للرياضيات أو `hyperref` للروابط التشعبية.
- `\begin{document}` و `\end{document}` هما بداية ونهاية المحتوى.

---

## **3. تنسيق النص**
| الوظيفة | الأمر في LaTeX | النتيجة |
|---------|--------------|---------|
| **عريض** | `\textbf{نص}` | **نص** |
| *مائل* | `\textit{نص}` | *نص* |
| ~~مشطوب~~ | `\sout{نص}` (يتطلب `ulem`) | ~~نص~~ |
| تسطير | `\underline{نص}` | <u>نص</u> |
| خطأ إملائي | `\textcolor{red}{نص}` (يتطلب `xcolor`) | <span style="color:red">نص</span> |

### **تغيير حجم الخط:**
```latex
{\tiny نص صغير جداً}  
{\small نص صغير}  
{\normalsize نص عادي}  
{\large نص كبير}  
{\huge نص كبير جداً}
```

---

## **4. العناوين والأقسام**
```latex
\section{القسم الرئيسي}
\subsection{قسم فرعي}
\subsubsection{قسم فرعي آخر}
\paragraph{فقرة} % بدون ترقيم
\subparagraph{فقرة فرعية} % بدون ترقيم
```

### **إضافة جدول المحتويات:**
```latex
\tableofcontents % يُدرج فهرساً تلقائياً
```

---

## **5. القوائم**
### **قائمة غير مرقمة:**
```latex
\begin{itemize}
    \item عنصر 1
    \item عنصر 2
    \item عنصر 3
\end{itemize}
```

### **قائمة مرقمة:**
```latex
\begin{enumerate}
    \item أول عنصر
    \item ثاني عنصر
\end{enumerate}
```

### **قائمة متداخلة:**
```latex
\begin{itemize}
    \item عنصر رئيسي
    \begin{enumerate}
        \item جزء 1
        \item جزء 2
    \end{enumerate}
    \item عنصر آخر
\end{itemize}
```

---

## **6. الرياضيات والمعادلات**
### **معادلات داخل النص:**
```latex
عندما $a \neq 0$، المعادلة التربيعية $ax^2 + bx + c = 0$ لها حلول.
```

### **معادلات مستقلة:**
```latex
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]
```

### **بيئة `align` لمحاذاة المعادلات:**
```latex
\begin{align}
    f(x) &= x^2 + 3x + 2 \\
    g(x) &= \sin(x) + \cos(x)
\end{align}
```

---

## **7. الجداول**
```latex
\begin{tabular}{|l|c|r|} % l=يسار, c=وسط, r=يمين
\hline
العمود 1 & العمود 2 & العمود 3 \\ \hline
بيان 1 & بيان 2 & بيان 3 \\ \hline
\end{tabular}
```

### **جداول متقدمة (باستخدام `booktabs`):**
```latex
\usepackage{booktabs}

\begin{tabular}{llr}
\toprule
اسم الطالب & الجامعة & المعدل \\ \midrule
أحمد & جامعة القاهرة & 85.5 \\
محمد & جامعة الأزهر & 92.3 \\ \bottomrule
\end{tabular}
```

---

## **8. الصور والأشكال**
```latex
\usepackage{graphicx}

\begin{figure}[h] % h=هنا, t=أعلى الصفحة, b=أسفل الصفحة
    \centering
    \includegraphics[width=0.5\textwidth]{example.png}
    \caption{وصف الصورة}
    \label{fig:example}
\end{figure}
```

---

## **9. المراجع والفهارس**
### **إضافة مراجع:**
```latex
\begin{thebibliography}{9}
\bibitem{latexcompanion} 
Michel Goossens, Frank Mittelbach, and Alexander Samarin. 
\textit{The \LaTeX\ Companion}. 
Addison-Wesley, 1993.
\end{thebibliography}
```

### **استخدام BibTeX (أكثر احترافية):**
1. إنشاء ملف `references.bib`.
2. إدراجه في المستند:
```latex
\bibliographystyle{plain}
\bibliography{references}
```

---

## **10. أمثلة متقدمة**
### **إنشاء عرض تقديمي بـ `beamer`:**
```latex
\documentclass{beamer}
\usetheme{Madrid} % اختيار سمة

\begin{document}
\title{عرض تقديمي}
\author{اسمك}
\date{\today}

\begin{frame}
\titlepage
\end{frame}

\begin{frame}
\frametitle{شريحة 1}
هذا مثال على شريحة.
\end{frame}
\end{document}
```

### **إنشاء مستند متعدد اللغات:**
```latex
\usepackage[arabic,english]{babel}

\begin{document}
\selectlanguage{arabic}
هذا نص بالعربية.

\selectlanguage{english}
This is English text.
\end{document}
```
