# Nexa — Built by Ibrahim (18yo Sudanese Builder from Port Sudan)
> Sudanese Financial OS | USDT Wallet + Escrow + Virtual Visa | Coding since age 12

**Founder:** Ibrahim, 18yo self-taught developer - Port Sudan
# Nexa — الوثيقة التوثيقية الكاملة والتقرير الشامل
إصدار: 1.0
تاريخ: 2026-10-13
المالك: مشروع Nexa
معدّ التقرير: تجميع ومراجعة تقنية

---

مقدمة تنفيذية
--------------
Nexa هي منصة رقمية متكاملة للتجارة الإلكترونية، المحفظة الرقمية، ونظام وساطة مالي (Escrow) مصممة لحماية رأس المال عبر USDT وتزويد التجار السودانيين بأدوات عالمية لسحب الأرباح وتمويل الاستيراد. تم تصميم النظام لأتمتة المبيعات، إدارة المخزون، ومنع الاحتيال، مع دمج وكيل ذكاء اصطناعي للدعم والرد الآلي.

ملف المطوّر العصامي (ملف شخصي ورحلة)
-----------------------------------
الاسم: (مطور المشروع) — شاب سوداني، 18 سنة و2 شهر  
الملخص: بدأ التعلم الذاتي للبرمجة منذ سن 12، ترك المدرسة لظروف مادية، عمل لساعات طويلة لتمويل نفسه وتطوير مهاراته، يعيش مغترباً منذ 5 سنوات، ويمتلك رؤية إنسانية لبناء بنية رقمية تخدم الطلاب والتجار، مع نهج أخلاقي قوي في الأمن السيبراني.  
الخبرات الفنية الأساسية:
- لغات: Python (FastAPI)، Dart/Flutter، Flet (واجهة سطح المكتب/ويب).
- قواعد بيانات: PostgreSQL، مفاهيم العمل مع blockchain (USDT/TRC20, BEP20, Polygon).
- أمن: فحص باختبار نِقاط الضعف، هندسة عكسية، استجابة للإخطار الأمني الأخلاقي.
الدافع والرؤية: بناء منظومة تضمن حماية مدخرات الفقراء، تسهيل التجارة عبر USDT، وتمكين استقلالية مالية للتجار.

سجل الإبلاغات الأمنية (Ethical Disclosures)
------------------------------------------
مبدأ العمل: الكشف الأخلاقي والتبليغ دون استغلال. الأمثلة الموثقة:
1. Genihat.com — ملاحظات: FTP مفتوح (21)، MySQL على الإنترنت (3306)، قابلية DDoS. توصية: إغلاق بورت 21 و3306 عبر جدار الحماية، ضبط DB على localhost، تفعيل WAF/Cloudflare، تفعيل Rate Limiting.
2. بوت "كاتم" — اكتشاف خداع في API (ردود مولَّدة باستخدام random بدل فحص حقيقي للسيرفرات). توصية: ربط API بخدمات حقيقية، تقوية حماية الـ headers/parameter validation.
3. zid-cash.com — User Enumeration عبر رسائل مختلفة في استعادة كلمة المرور؛ اكتشاف مسار /admin/login مكشوف. توصية: توحيد رسائل استعادة كلمة المرور، حجب مسارات الإدارة خلف VPN/ACL، فرض سياسات مصادقة متعددة العوامل.

أخلاقيات وإجراءات الإبلاغ
- توثيق الاستكشافات، عدم استخراج بيانات، إبلاغ عبر قناة رسمية (واتساب/بريد) ثم متابعة.
- تقديم تقرير إرشادي مع خطوات إصلاح عملية وخيارات مراقبة لاحقة.

صِف المعمارية العامة (Architecture Overview)
---------------------------------------------
مكوّنات رئيسية:
- واجهة API (Backend): Python + FastAPI. تستضيف المنطق المالي، محركات الحجز، وواجهات التكامل مع شبكات البلوكشين ومزوّدي البطاقات.
- قاعدة البيانات: PostgreSQL (مع استخدام Decimal للحسابات المالية، وقفل الصفوف FOR UPDATE خلال المعاملات الحرجة).
- واجهات المستخدم: Flutter (Mobile) + Flet (Web/Desktop أدوات تجارية ولوحات تحكم).
- طبقة الحماية: WAF (Cloudflare أو بديل)، Rate Limiting، IDS/IPS، جدران نارية، إدارة مفاتيح سرية (KMS).
- مكونات Blockchain: Nodes/Providers لTRC20/BEP20/Polygon أو موفّرو بوابة دفع (custodial/non-custodial) عبر APIs.
- خدمات خارجية: موفرو إصدار البطاقات الافتراضية (Virtual Card Issuers) عبر تكامل API، خدمات KYC/AML، خدمات البريد/شحن (شركاء لوجستي).

نموذج البيانات الأساسي (مقتطفات جدولية)
-----------------------------------------
الجداول الرئيسية (مفاهيمي):
- users (id, name, email, password_hash, kyc_status, created_at)
- wallets (id, user_id, network, address, balance_decimal, created_at)
- transactions (id, wallet_id, type, amount_decimal, status, related_order_id, created_at)
- marketplace_products (id, merchant_id, title, price_usdt_decimal, stock_qty, is_digital, created_at)
- marketplace_orders (id, buyer_id, merchant_id, total_usdt_decimal, status [pending/processing/delivered/cancelled], created_at)
- marketplace_held_funds (id, order_id, amount_decimal, status [held/released/refunded], created_at)
- sessions_devices (id, user_id, device_fingerprint, ip, last_seen, is_revoked)

سلوك البيانات النقدية
- كل القيم المالية مخزنة كـ Decimal (وليس float) بدقة مناسبة (مثلاً Decimal(28,8) حسب متطلبات الـ USDT).
- اعتماد نظام أحكام تناسق: عمليات المال تتم ضمن معاملة (DB transaction) وباستخدام SELECT ... FOR UPDATE على صفوف رصيد المحفظة والطلبات.

تفصيل سير الدفع والـ Escrow (تدفق العملية)
-------------------------------------------
1. checkout (marketplace_checkout):
   - تحقق من رصيد المحفظة (FOR UPDATE).
   - إن كافٍ: خصم المبلغ وتسجيله في marketplace_held_funds بحالة = held.
   - إنشاء marketplace_order بحالة = pending.
   - إرسال إشعار للتاجر والوكيل الذكي.

2. complete_marketplace_order:
   - عند تأكيد الاستلام من المشتري (UI button): تغيير حالة الطلب إلى delivered.
   - نقل المبلغ من marketplace_held_funds إلى محفظة التاجر (داخل نفس الـ transaction).
   - التحديثات والسجلات (auditing).

3. cancel_marketplace_order (آلي):
   - معيار: لم يستجب التاجر خلال نافذة زمنية (مثلاً 10 ساعات) أو طلب إلغاء المشتري.
   - إرجاع كامل المبلغ للمشتري (update wallet balance) وتغيير حالة held → refunded.
   - إعادة كمية المنتج إلى مخزون التاجر، إخطار المستخدمين.

حماية التزامن ومنع السباقات (Race conditions)
- استخدام FOR UPDATE عند قراءة/تعديل أرصدة المحافظ وسجلات الـ held_funds.
- مراجعة عزل المعاملات (transaction isolation level) وضبط timeouts.
- وضع قيود SQL لمنع negative stock: WHERE quantity >= %s قبل أي إنقاص.

التحقق من عناوين المحفظة (Address Validation)
- التحقق الصارم لطول/بداية العنوان لكل شبكة (مثلاً Tron تبدأ بـ 'T').
- استخدام مكتبات معتمدة للتحقق (مثلاً py-tron, web3.py).
- عملية اختبار قبل إجراء سحب فعلي: إرسال تحويل اختبار صغير (اختياري) أو التحقق عبر واجهة موفر الشبكة.

دعم الشبكات المتعددة
- كل محفظة مرتبطة بشبكة محددة (network enum).
- عمليات السحب ترسل عبر Node/Provider مناسب أو عبر خدمة custodial/third-party.

الوكيل الذكي (AI Agent) — وصف وظيفي
-----------------------------------
مهامه:
- الرد الآلي على المستخدمين داخل المتجر (عرض منتجات، الأسعار، متابعة الشحن).
- قراءة وتحليل سجلات الخطأ وحل المشكلات الشائعة.
- تصعيد الحوادث المالية الحرجة للمطور.
تقنيات مقترحة:
- نموذج LLM مصغّر على مهام محددة مع قواعد منطقية (no hallucination)، تكامل مع DB/Logs عبر وظائف محدودة (retrieval+tooling).
- سياسات أمان: منع الوكيل من إجراء تحويلات مالية مباشرة دون موافقة بشرية.

البطاقات الافتراضية والكيان القانوني (LLC + Virtual Cards)
------------------------------------------------------------
خطوات عامة:
1. إنشاء LLC في ولاية مناسبة (مثل Wyoming) للحصول على EIN وحساب بنكي تجاري.
2. تكامل مع موفري FinTech لإصدار Virtual Cards (APIs). التحقق من السياسات ومتطلبات KYC/AML.
3. ربط دخل التاجر المحول بالـ USDT بآلية تسييل وتحويل إلى رصيد البطاقة عند الشروط.
ملاحظات قانونية:
- الالتزام بالقوانين الدولية المحلية والدولية، AML/KYC صارم، والامتثال لشروط مزود البطاقات.

إدارة الجلسات والأجهزة النشطة (Sessions & Device Management)
-------------------------------------------------------------
- واجهة تعرض الأجهزة النشطة (device_fingerprint, ip, last_seen).
- زر طرد/سحب الجلسة يؤدي إلى وضع is_revoked = true وإنهاء التوكنات.
- توكنات قصيرة العمر + Refresh token مع سجل أجهزة.

حملات الحماية والوقاية (Hardening)
----------------------------------
- WAF + Rate Limiting + IP Reputation.
- تشفير المستودعات الحساسة (KMS) وإدارة مفاتيح آمنة.
- سياسات كلمات مرور قوية، MFA للمروجين والإداريين.
- مراجعات أمنية دورية (SAST/DAST/pen-testing).
- مراقبة سلوك المستخدم لاكتشاف أنماط الاحتيال.

التشغيل والنشر (Deployment & Runbook)
--------------------------------------
بيئة الإنتاج:
- بنية Microservices أو Monolith مقسّم: API + Workers (background jobs) + DB + Cache (Redis) + Message Queue (RabbitMQ/Redis streams).
نسخة احتياطية واستعادة:
- نسخ احتياطية يومية للـ DB، اختبار استعادة شهري.
- نسخ احتياطي للمفاتيح الحرِجة خارج خوادم الخدمة.
مراقبة:
- Metrics (Prometheus/Grafana)، Alerts (PagerDuty/Email/Telegram).
استجابة للحوادث:
- playbooks للحوادث المالية (قفل المعاملات، ترحيل الأموال المؤقت إلى cold-wallet، إشعار المستخدمين).
- قنوات اتصال للطوارئ (رقم مسؤول، بريد احتياطي، فريق أمان).

اختبارات ونوعية (QA)
--------------------
- وحدات لاختبار الحسابات المالية (precision tests).
- اختبارات تكامل مع شبكات البلوكشين في بيئة Sandbox.
- حمل محاكاة DDoS في بيئة اختبارية مغلقة.
- اختبارات سياسات الإساءة وUser Enumeration.

تحليل تنافسي واستراتيجية السوق
-------------------------------
نقاط القوة:
- حماية رأس المال بالـ USDT = ميزة فريدة ضد التضخم.
- نظام Escrow قوي يؤمن التجارة البينية داخل الدولة.
- إصدار بطاقات افتراضية ليكسر قيود السحب الدولي.
- واجهات مؤتمتة وAI Agent يقللان الحاجة للرد اليدوي.
مخاطر وموانع:
- تنظيمات مصرفية وقيود KYC/AML قد تعرقل عمليات البطاقات.
- اعتماد مزودي الخدمات الخارجيين لعمليات السحب قد يخلق نقطة فشل.
- ضرورة إدارة السمعة وثقة التجار والمستخدمين.

خريطة الطريق (Roadmap)
-----------------------
مرحلة 1 (MVP):
- API أساسي، محفظة USDT (شبكة واحدة)، Escrow، Flutter app بسيط، لوحة تاجر أساسية.
مرحلة 2:
- شبكات متعددة، آلية KYC مدمجة، نظام إصدار البطاقات الافتراضية تجريبي.
مرحلة 3:
- AI Agent منفّذ، نظام تعليقات/تقييمات، سوق مستقل Freelancing، بنية قابلة للتوسع عالميًا.
مرحلة 4:
- شراكات مالية دولية، تدقيق أمني خارجي سنوي، شهادة PCI DSS إن لزم.

مرفقات تقنية (Pseudocode ومقتطفات)
------------------------------------
مقتطف: Checkout (مبسط)
```python
def marketplace_checkout(user_id, order_items, db):
    # يبدأ transaction
    with db.transaction() as tx:
        wallet = tx.query("SELECT balance FROM wallets WHERE user_id=%s FOR UPDATE", (user_id,))
        total = calculate_total(order_items)
        if wallet.balance < total:
            raise InsufficientFunds()
        # خصم وتخزين الحجز
        tx.execute("UPDATE wallets SET balance = balance - %s WHERE user_id=%s", (total, user_id))
        order_id = tx.insert("INSERT INTO marketplace_orders ... RETURNING id", ...)
        tx.insert("INSERT INTO marketplace_held_funds (order_id, amount, status) VALUES (%s,%s,'held')", (order_id, total))
        tx.commit()
    notify_merchant(order_id)
    return order_id
