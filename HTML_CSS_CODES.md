# أكواد HTML & CSS للتقرير
# =============================

## ملاحظات مهمة:
- هذا الملف يحتوي على الأكواد الكاملة لإنشاء التقرير
- يمكنك نسخ هذه الأكواد واستخدامها مباشرة
- الملف متوافق مع جميع المتصفحات الحديثة
- يدعم الطباعة والتصدير إلى PDF

---

## 1. كود HTML الأساسي

```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تقرير تحليل برامج المراجعة الأكاديمية</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <!-- رأس التقرير -->
        <div class="header">
            <h1>🎓 تقرير تحليل برامج المراجعة الأكاديمية</h1>
            <div class="date">تاريخ التقرير: 01/01/2026</div>
        </div>
        
        <!-- ملخص إحصائي -->
        <div class="summary">
            <div class="summary-card">
                <div class="number">10</div>
                <div class="label">إجمالي البرامج</div>
            </div>
            <div class="summary-card">
                <div class="number">9</div>
                <div class="label">برامج مكتملة</div>
            </div>
            <div class="summary-card">
                <div class="number">1</div>
                <div class="label">برنامج قيد الإنجاز</div>
            </div>
            <div class="summary-card">
                <div class="number">90%</div>
                <div class="label">نسبة الإنجاز الكلية</div>
            </div>
        </div>
        
        <!-- محتوى البرامج -->
        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 1: اسم البرنامج</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <!-- معلومات البرنامج -->
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">اسم الجامعة</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">البكالوريوس</div>
                        </div>
                        <!-- المزيد من المعلومات... -->
                    </div>
                    
                    <!-- نسبة الإنجاز -->
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100%">
                                100%
                            </div>
                        </div>
                        
                        <!-- عناصر الإنجاز -->
                        <div class="completion-items">
                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>
                            <!-- المزيد من العناصر... -->
                        </div>
                    </div>
                    
                    <!-- فريق المراجعة -->
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>
                        
                        <!-- رئيس الفريق -->
                        <div class="team-member chair">
                            <div class="member-avatar">ر</div>
                            <div class="member-info">
                                <div class="member-name">اسم رئيس الفريق</div>
                                <div class="member-details">
                                    أستاذ مشارك | الجامعة
                                </div>
                                <span class="member-role">رئيس الفريق</span>
                            </div>
                        </div>
                        
                        <!-- الأعضاء -->
                        <div class="team-member">
                            <div class="member-avatar">ع</div>
                            <div class="member-info">
                                <div class="member-name">اسم العضو</div>
                                <div class="member-details">
                                    أستاذ مساعد | الجامعة
                                </div>
                                <span class="member-role">عضو</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- تذييل التقرير -->
        <div class="footer">
            <p style="font-size: 1.2em; margin-bottom: 10px;">📊 تقرير شامل لبرامج المراجعة الأكاديمية</p>
            <p>تم إنشاء هذا التقرير تلقائياً | جميع الحقوق محفوظة © 2026</p>
        </div>
    </div>
</body>
</html>
```

---

## 2. كود CSS الكامل (styles.css)

```css
/* =============================
   تنسيقات عامة
   ============================= */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    padding: 20px;
    line-height: 1.8;
}

.container {
    max-width: 1400px;
    margin: 0 auto;
    background: white;
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
    overflow: hidden;
}

/* =============================
   رأس التقرير
   ============================= */

.header {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 40px;
    text-align: center;
}

.header h1 {
    font-size: 2.5em;
    margin-bottom: 10px;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
}

.header .date {
    font-size: 1.1em;
    opacity: 0.9;
}

/* =============================
   الملخص الإحصائي
   ============================= */

.summary {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    padding: 40px;
    background: #f8f9fa;
}

.summary-card {
    background: white;
    border-radius: 15px;
    padding: 25px;
    text-align: center;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    transition: transform 0.3s ease;
}

.summary-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 12px rgba(0,0,0,0.15);
}

.summary-card .number {
    font-size: 3em;
    font-weight: bold;
    color: #667eea;
    margin-bottom: 10px;
}

.summary-card .label {
    font-size: 1.1em;
    color: #666;
}

/* =============================
   أقسام البرامج
   ============================= */

.content {
    padding: 40px;
}

.program-section {
    margin-bottom: 50px;
    border: 2px solid #e0e0e0;
    border-radius: 15px;
    overflow: hidden;
    transition: all 0.3s ease;
}

.program-section:hover {
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    border-color: #667eea;
}

.program-header {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 25px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
}

.program-header.pending {
    background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
}

.program-title {
    font-size: 1.8em;
    font-weight: bold;
    flex: 1;
    min-width: 300px;
}

.program-badge {
    background: rgba(255,255,255,0.3);
    padding: 10px 20px;
    border-radius: 25px;
    font-weight: bold;
    font-size: 0.9em;
}

/* =============================
   معلومات البرنامج
   ============================= */

.program-info {
    padding: 30px;
    background: #f8f9fa;
}

.info-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    margin-bottom: 25px;
}

.info-item {
    background: white;
    padding: 15px;
    border-radius: 10px;
    border-right: 4px solid #667eea;
}

.info-item .label {
    font-weight: bold;
    color: #764ba2;
    margin-bottom: 5px;
    font-size: 0.95em;
}

.info-item .value {
    color: #333;
    font-size: 1.05em;
}

/* =============================
   شريط التقدم
   ============================= */

.progress-section {
    margin: 25px 0;
    padding: 20px;
    background: white;
    border-radius: 10px;
}

.progress-title {
    font-size: 1.3em;
    font-weight: bold;
    color: #764ba2;
    margin-bottom: 15px;
}

.progress-bar-container {
    background: #e0e0e0;
    border-radius: 25px;
    height: 40px;
    overflow: hidden;
    margin-bottom: 10px;
    box-shadow: inset 0 2px 4px rgba(0,0,0,0.1);
}

.progress-bar {
    height: 100%;
    background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
    border-radius: 25px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-weight: bold;
    font-size: 1.1em;
    transition: width 1s ease;
}

.progress-bar.pending {
    background: linear-gradient(90deg, #f093fb 0%, #f5576c 100%);
}

/* =============================
   عناصر الإنجاز
   ============================= */

.completion-items {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 15px;
    margin-top: 15px;
}

.completion-item {
    display: flex;
    align-items: center;
    padding: 10px;
    background: #f8f9fa;
    border-radius: 8px;
}

.completion-item .icon {
    width: 25px;
    height: 25px;
    border-radius: 50%;
    margin-left: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    font-size: 0.9em;
}

.completion-item .icon.done {
    background: #4caf50;
    color: white;
}

.completion-item .icon.pending {
    background: #ff9800;
    color: white;
}

.completion-item .icon.missing {
    background: #f44336;
    color: white;
}

/* =============================
   فريق المراجعة
   ============================= */

.team-section {
    margin-top: 25px;
    padding: 20px;
    background: white;
    border-radius: 10px;
}

.team-title {
    font-size: 1.3em;
    font-weight: bold;
    color: #764ba2;
    margin-bottom: 20px;
    border-bottom: 2px solid #667eea;
    padding-bottom: 10px;
}

.team-member {
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 15px;
    padding: 15px;
    margin-bottom: 15px;
    background: #f8f9fa;
    border-radius: 10px;
    border-right: 4px solid #667eea;
}

.team-member.chair {
    background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
    border-right: 4px solid #764ba2;
}

.member-avatar {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 1.5em;
    font-weight: bold;
}

.member-info {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.member-name {
    font-size: 1.2em;
    font-weight: bold;
    color: #333;
    margin-bottom: 5px;
}

.member-details {
    color: #666;
    font-size: 0.95em;
}

.member-role {
    display: inline-block;
    padding: 4px 12px;
    background: #667eea;
    color: white;
    border-radius: 15px;
    font-size: 0.85em;
    margin-top: 5px;
}

/* =============================
   صندوق التنبيه
   ============================= */

.alert-box {
    background: #fff3cd;
    border: 2px solid #ffc107;
    border-radius: 10px;
    padding: 20px;
    margin: 20px 0;
}

.alert-box .alert-title {
    font-size: 1.3em;
    font-weight: bold;
    color: #856404;
    margin-bottom: 10px;
}

.alert-box .alert-content {
    color: #856404;
    font-size: 1.05em;
}

/* =============================
   التذييل
   ============================= */

.footer {
    background: #2c3e50;
    color: white;
    padding: 30px;
    text-align: center;
}

/* =============================
   تنسيقات الطباعة
   ============================= */

@media print {
    body {
        background: white;
        padding: 0;
    }
    
    .container {
        box-shadow: none;
    }
    
    .program-section {
        page-break-inside: avoid;
    }
}

/* =============================
   تنسيقات الأجهزة المحمولة
   ============================= */

@media (max-width: 768px) {
    .header h1 {
        font-size: 1.8em;
    }
    
    .program-title {
        font-size: 1.3em;
    }
    
    .info-grid {
        grid-template-columns: 1fr;
    }
}
```

---

## 3. تعليمات الاستخدام

### طريقة الاستخدام:

1. **إنشاء ملف HTML جديد:**
   - احفظ كود HTML في ملف باسم `report.html`

2. **إنشاء ملف CSS منفصل:**
   - احفظ كود CSS في ملف باسم `styles.css`
   - ضعه في نفس المجلد مع ملف HTML

3. **ربط الملفات:**
   - تأكد من وجود السطر التالي في `<head>` بملف HTML:
   ```html
   <link rel="stylesheet" href="styles.css">
   ```

4. **فتح التقرير:**
   - افتح ملف `report.html` في المتصفح

### أو استخدام CSS مضمّن:

إذا كنت تفضل ملف HTML واحد فقط، ضع كود CSS داخل `<style>` في `<head>`:

```html
<head>
    <meta charset="UTF-8">
    <title>التقرير</title>
    <style>
        /* ضع هنا كود CSS كاملاً */
    </style>
</head>
```

---

## 4. ميزات التصميم

✅ **متجاوب تماماً** - يعمل على جميع أحجام الشاشات
✅ **ألوان احترافية** - تدرجات بنفسجية أنيقة
✅ **تأثيرات تفاعلية** - عند التمرير على العناصر
✅ **قابل للطباعة** - تنسيقات خاصة للطباعة
✅ **سهل التخصيص** - متغيرات ألوان واضحة
✅ **أيقونات Emoji** - لا يحتاج مكتبات خارجية

---

## 5. تخصيص الألوان

لتغيير الألوان الأساسية، ابحث عن هذه القيم واستبدلها:

- **اللون البنفسجي الفاتح:** `#667eea`
- **اللون البنفسجي الداكن:** `#764ba2`
- **اللون الوردي (للبرامج قيد الإنجاز):** `#f093fb` و `#f5576c`
- **لون النجاح:** `#4caf50`
- **لون التحذير:** `#ff9800`
- **لون الخطأ:** `#f44336`

---

## 6. إضافة برامج جديدة

لإضافة برنامج جديد، انسخ القسم التالي وعدّله:

```html
<div class="program-section">
    <div class="program-header">
        <div class="program-title">برنامج X: [اسم البرنامج]</div>
        <div class="program-badge">✅ مكتمل 100%</div>
    </div>
    
    <div class="program-info">
        <!-- أضف المحتوى هنا -->
    </div>
</div>
```

---

## 7. تصدير إلى PDF

### من المتصفح:
1. افتح التقرير في المتصفح
2. اضغط `Ctrl+P` (أو `Cmd+P` على Mac)
3. اختر "حفظ كـ PDF"
4. انقر "حفظ"

### برمجياً (Python):
```python
from weasyprint import HTML

HTML('report.html').write_pdf('report.pdf')
```

---

تم إنشاء هذا الملف بواسطة نظام تحليل البيانات الآلي
© 2026 - جميع الحقوق محفوظة
```
