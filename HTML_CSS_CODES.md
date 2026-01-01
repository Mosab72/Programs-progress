<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تقرير تحليل برامج المراجعة الأكاديمية</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
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
        .footer {
            background: #2c3e50;
            color: white;
            padding: 30px;
            text-align: center;
        }
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
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎓 تقرير تحليل برامج المراجعة الأكاديمية</h1>
            <div class="date">تاريخ التقرير: 01/01/2026</div>
        </div>
        
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

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 1: MBBS</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة جدة - UJ</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Bachelor</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic - On-Site</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Ali Hendi</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/01/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/03/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member chair">
                            <div class="member-avatar">ر</div>
                            <div class="member-info">
                                <div class="member-name">رانيه غازي محمد طه زيني</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة أم القرى - UQU
                                </div>
                                <span class="member-role">رئيس الفريق - Alternative Chair</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ن</div>
                            <div class="member-info">
                                <div class="member-name">نوال حمدان ضيف الله المحمدي</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة طيبة - TaibahU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ه</div>
                            <div class="member-info">
                                <div class="member-name">هاني أحمد إبراهيم أبو زيد</div>
                                <div class="member-details">
                                    Professor | أستاذ | جامعة الطائف - TU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">أ</div>
                            <div class="member-info">
                                <div class="member-name">أميره مهدي العطوي</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة تبوك - UT
                                </div>
                                <span class="member-role">مراقب - Observer</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">م</div>
                            <div class="member-info">
                                <div class="member-name">ملك محمد مساعد خالد الحكيم</div>
                                <div class="member-details">
                                    Professor | أستاذ | جامعة الملك سعود - KSU
                                </div>
                                <span class="member-role">مراقب - Observer</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 2: تصميم الأزياء + الرسم والفنون</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة جدة - UJ</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Bachelor</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Suzanne M. Bardeas</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">11/30/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/01/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member chair">
                            <div class="member-avatar">م</div>
                            <div class="member-info">
                                <div class="member-name">مسعودة عالم جان قربان</div>
                                <div class="member-details">
                                    Professor | أستاذ | مستشار في المعهد الملكي للفنون التقليدية
                                </div>
                                <span class="member-role">رئيس الفريق - Chair</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 3: تصميم الأزياء</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة جدة - UJ</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Bachelor</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Suzanne M. Bardeas</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">11/30/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/01/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member">
                            <div class="member-avatar">ت</div>
                            <div class="member-info">
                                <div class="member-name">تهاني ناصر صالح العجاجي</div>
                                <div class="member-details">
                                    Professor | أستاذ | جامعة الأميرة نورة بنت عبدالرحمن - PNU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ا</div>
                            <div class="member-info">
                                <div class="member-name">اسماء عبدالرحمن حمود النويصر</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | جامعة القصيم - QU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 4: الرسم والفنون</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة جدة - UJ</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Bachelor</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Suzanne M. Bardeas</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">11/30/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/01/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member">
                            <div class="member-avatar">ح</div>
                            <div class="member-info">
                                <div class="member-name">حنان سعود الهزاع</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة الأميرة نورة بنت عبدالرحمن - PNU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ه</div>
                            <div class="member-info">
                                <div class="member-name">هدى بنت عبد العزيز المقرن</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | جامعة الأميرة نورة بنت عبدالرحمن - PNU
                                </div>
                                <span class="member-role">Alternative Member</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 5: BSc.Health informatics system + Anesthesia Technology</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة المعرفة – UM</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Bachelor</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Thoraia M. Shinawi</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/07/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/08/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member chair">
                            <div class="member-avatar">ع</div>
                            <div class="member-info">
                                <div class="member-name">عبدالرحمن بن محمد جعبور</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة جازان - JazanU
                                </div>
                                <span class="member-role">رئيس الفريق - Chair</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 6: BSc.Health informatics system</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة المعرفة – UM</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Bachelor</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Thoraia M. Shinawi</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/07/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/08/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member">
                            <div class="member-avatar">ا</div>
                            <div class="member-info">
                                <div class="member-name">البيان بنت صلاح بن مهل الردادي</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | جامعة طيبة - TaibahU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">أ</div>
                            <div class="member-info">
                                <div class="member-name">أروى عبدالرحمن الثميري</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | جامعة الإمام عبدالرحمن بن فيصل - IAU
                                </div>
                                <span class="member-role">Alternative Member</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 7: BSc.Anesthesia Technology</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة المعرفة – UM</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Bachelor</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Thoraia M. Shinawi</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/07/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/08/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member">
                            <div class="member-avatar">س</div>
                            <div class="member-info">
                                <div class="member-name">سعد محمد سعد الربيعة</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | كلية الأمير سلطان العسكرية للعلوم الصحية - PSMCHS
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">س</div>
                            <div class="member-info">
                                <div class="member-name">سيماء محمد عمر ناصر</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | جامعة الملك سعود بن عبدالعزيز للعلوم الصحية - KSAU-HS
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ط</div>
                            <div class="member-info">
                                <div class="member-name">طه طاهر اسماعيل</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة الملك سعود بن عبدالعزيز للعلوم الصحية - KSAU-HS
                                </div>
                                <span class="member-role">مراقب - Observer</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 8: دكتوراه العقيدة والمذاهب المعاصرة</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة القصيم - QU</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">PhD</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic - Hybrid</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Mohammed Alsulami</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/15/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/16/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 85.71428571428571%">
                                86%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon missing">✗</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member chair">
                            <div class="member-avatar">ش</div>
                            <div class="member-info">
                                <div class="member-name">شريفة أحمد الحازمي</div>
                                <div class="member-details">
                                    Professor | أستاذ | جامعة الأميرة نورة بنت عبدالرحمن - PNU
                                </div>
                                <span class="member-role">رئيس الفريق - Chair</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ا</div>
                            <div class="member-info">
                                <div class="member-name">ابتسام ناصر عبدالعزيز اللهيم</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | جامعة الإمام محمد بن سعود الإسلامية - IMISIU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ع</div>
                            <div class="member-info">
                                <div class="member-name">علي محمد العتيبي</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | الجامعة الإسلامية بالمدينة المنورة - IU
                                </div>
                                <span class="member-role">Alternative Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ف</div>
                            <div class="member-info">
                                <div class="member-name">فالح سالم القحطاني</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة نايف العربية للعلوم الأمنية - NAUSS
                                </div>
                                <span class="member-role">مراقب - Observer</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 9: Dentistry</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة الملك عبدالعزيز -  KAU</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Bachelor</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic - Hybrid</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Raid A. Al-Akeel</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/09/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/10/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member chair">
                            <div class="member-avatar">س</div>
                            <div class="member-info">
                                <div class="member-name">سميه حسني محمود حسن أبو عجور</div>
                                <div class="member-details">
                                    Professor | أستاذ | Faculty of Medicine, Suez Canal University
                                </div>
                                <span class="member-role">رئيس الفريق - Alternative Chair</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">D</div>
                            <div class="member-info">
                                <div class="member-name">Duncan John Wood</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | University of Sheffield
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ه</div>
                            <div class="member-info">
                                <div class="member-name">هشام صالح المعلم</div>
                                <div class="member-details">
                                    Professor | أستاذ | جامعة الملك سعود - KSU
                                </div>
                                <span class="member-role">Alternative Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ن</div>
                            <div class="member-info">
                                <div class="member-name">نوف محمد الحمياني</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | جامعة الطائف - TU
                                </div>
                                <span class="member-role">مراقب - Observer</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 10: MSc of Applied Energy Economics + MSc Accounting</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة الملك فيصل -  KFU</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Master</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic - Hybrid</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Suzanne M. Bardeas</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/21/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/22/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member chair">
                            <div class="member-avatar">J</div>
                            <div class="member-info">
                                <div class="member-name">James Francis O'Kane</div>
                                <div class="member-details">
                                    Professor | أستاذ | Retired
                                </div>
                                <span class="member-role">رئيس الفريق - Chair</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 11: MSc of Applied Energy Economics</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة الملك فيصل -  KFU</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Master</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic - Hybrid</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Suzanne M. Bardeas</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/21/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/22/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member">
                            <div class="member-avatar">P</div>
                            <div class="member-info">
                                <div class="member-name">Pedro Nuno De Freitas Lopes Teixeira</div>
                                <div class="member-details">
                                    Professor | University of Porto
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ح</div>
                            <div class="member-info">
                                <div class="member-name">حاتم خالد عقيل</div>
                                <div class="member-details">
                                    Assistant Professor | أستاذ مساعد | جامعة الأعمال والتكنولوجيا - UBT
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="program-section">
                <div class="program-header">
                    <div class="program-title">برنامج 12: MSc Accounting</div>
                    <div class="program-badge">✅ مكتمل 100%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة الملك فيصل -  KFU</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Master</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic - Hybrid</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Suzanne M. Bardeas</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">12/21/25</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء</div>
                            <div class="value">12/22/25</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar" style="width: 100.0%">
                                100%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member">
                            <div class="member-avatar">ه</div>
                            <div class="member-info">
                                <div class="member-name">هند عبدالله الرقيب</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة الطائف - TU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ه</div>
                            <div class="member-info">
                                <div class="member-name">هبه شفيق شلهوب</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة الملك عبدالعزيز - KAU
                                </div>
                                <span class="member-role">Alternative Member</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="content">
            <div class="alert-box">
                <div class="alert-title">⚠️ تنبيه: برنامج قيد الإنجاز</div>
                <div class="alert-content">
                    برنامج Mathematics - جامعة الجوف متبقي له عنصر واحد فقط (خطاب الاستعانة)
                    <br>تاريخ الانتهاء المتوقع: 25 يناير 2026
                </div>
            </div>
            
            <div class="program-section">
                <div class="program-header pending">
                    <div class="program-title">برنامج 13: Mathematics</div>
                    <div class="program-badge">⏳ باقي 14.29%</div>
                </div>
                
                <div class="program-info">
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="label">🏛️ المؤسسة</div>
                            <div class="value">جامعة الجوف -  JU</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📚 الدرجة العلمية</div>
                            <div class="value">Master</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📋 نوع المراجعة</div>
                            <div class="value">Programmatic - Hybrid</div>
                        </div>
                        <div class="info-item">
                            <div class="label">👨‍💼 المستشار</div>
                            <div class="value">Dr. Waild S. Al-Sabah</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ البدء</div>
                            <div class="value">01/25/26</div>
                        </div>
                        <div class="info-item">
                            <div class="label">📅 تاريخ الانتهاء المتوقع</div>
                            <div class="value">25 يناير 2026</div>
                        </div>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-title">📊 نسبة الإنجاز</div>
                        <div class="progress-bar-container">
                            <div class="progress-bar pending" style="width: 85.71%">
                                85.71%
                            </div>
                        </div>
                        
                        <div class="completion-items">

                            <div class="completion-item">
                                <div class="icon missing">✗</div>
                                <div>الحزمة الأولى</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج الإفصاح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>نموذج تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>البيانات البنكية</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon pending">⏳</div>
                                <div>خطاب الاستعانة</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon done">✓</div>
                                <div>جدول تضارب المصالح</div>
                            </div>

                            <div class="completion-item">
                                <div class="icon missing">✗</div>
                                <div>الحزمة الثالثة</div>
                            </div>

                        </div>
                    </div>
                    
                    <div class="team-section">
                        <div class="team-title">👥 فريق المراجعة</div>

                        <div class="team-member chair">
                            <div class="member-avatar">A</div>
                            <div class="member-info">
                                <div class="member-name">Andrew Harold Osbaldestin</div>
                                <div class="member-details">
                                    Emeritus Professor | أستاذ فخري | University of Portsmouth, UK
                                </div>
                                <span class="member-role">رئيس الفريق - Alternative Chair</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ف</div>
                            <div class="member-info">
                                <div class="member-name">فيصل بن عبدالله المالكي</div>
                                <div class="member-details">
                                    Professor | أستاذ | جامعة الطائف - TU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                        <div class="team-member">
                            <div class="member-avatar">ح</div>
                            <div class="member-info">
                                <div class="member-name">حصه فيحان مفلح القحطاني</div>
                                <div class="member-details">
                                    Associate Professor | أستاذ مشارك | جامعة الملك عبدالعزيز - KAU
                                </div>
                                <span class="member-role">Member</span>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <div class="footer">
            <p style="font-size: 1.2em; margin-bottom: 10px;">📊 تقرير شامل لبرامج المراجعة الأكاديمية</p>
            <p>تم إنشاء هذا التقرير تلقائياً | جميع الحقوق محفوظة © 2026</p>
        </div>
    </div>
</body>
</html>
