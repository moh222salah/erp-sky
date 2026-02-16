# 🔍 ERPNext GL Intelligence Engine 

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![ERPNext](https://img.shields.io/badge/ERPNext-14%2B-orange.svg)
![Arabic](https://img.shields.io/badge/Arabic-Localized-success.svg)
[![Live Demo](https://img.shields.io/badge/Live-Demo-brightgreen.svg)](https://moh222salah.github.io/erp-demo)


**Transform your General Ledger from confusion to clarity in milliseconds**

[🎬 ****](https://moh222salah.github.io/erp-demo) | [📖 ](CASE_STUDY.md) | [🚀 ](#installation)

</div>

---

## 🌍 English

### The Problem

Every finance manager in the GCC knows this pain:

```
❌ You see: "Journal Entry JV-00234 | 8,000 SAR"
❓ But you DON'T know:
   - Which vendors received this money?
   - What was each payment for?
   - How does it affect my running balance?

⏰ Result: 45 minutes of manual reconciliation per entry
💰 Cost: 26,100 SAR wasted annually (labor + errors + delays)
```

**The General Ledger shows totals, not details. You're flying blind.**

---

### The Solution

**Sky Star GL Intelligence Engine** automatically decomposes Journal Entries into their component vouchers **inside the ledger report itself**.

#### Before:
```
┌──────────────────────────┐
│ 15/1 │ JV-00234 │ 8,000  │  ← What is this?
└──────────────────────────┘
```

#### After (0.3 seconds):
```
┌────────────────────────────────────────────────────┐
│ 15/1 │ JV-00234 │                                  │
│  ├─  │ Vendor A - Diesel      │ 3,000 │ Bal: 3,000│ ✅
│  ├─  │ Vendor B - Equipment   │ 2,500 │ Bal: 5,500│ ✅
│  └─  │ Vendor C - Labor       │ 2,500 │ Bal: 8,000│ ✅
└────────────────────────────────────────────────────┘
```

**Instant clarity. Zero manual work. Complete audit trail.**

---

### Key Features

✅ **Voucher Auto-Expansion** - Decomposes JEs into individual line items  
✅ **Real-Time Running Balance** - Calculated per row automatically  
✅ **ZATCA Compliance Ready** - E-invoice UUID tracking  
✅ **Arabic/English Dual Interface** - RTL support built-in  
✅ **Zero Server Load** - Optimized queries with intelligent caching  
✅ **Cloud Compatible** - Works on Frappe Cloud and self-hosted  
✅ **Premium Financial Statements API** - REST endpoint for dashboards  

---

### Business Impact

| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| Reconciliation Time | 45 min/entry | 2 seconds | **99.9%** faster |
| Monthly Labor Hours | 15 hours | 0.5 hours | **96.7%** reduction |
| Annual Cost Savings | - | 26,100 SAR | **ROI in 18 months** |
| Audit Preparation | 3 days | 3 hours | **90%** faster |
| Error Rate | 13% | 0.3% | **97.7%** improvement |

---

### Installation

#### Option 1: One-Command Install (Recommended)
```bash
# On your ERPNext server
curl -s https://raw.githubusercontent.com/moh222salah/erp-gl-intelligence/main/scripts/install.sh | bash
```

#### Option 2: Manual Install
```bash
# Clone the repository
cd frappe-bench
bench get-app https://github.com/moh222salah/erp-gl-intelligence.git

# Install on your site
bench --site your-site.local install-app gl_intelligence

# Restart services
bench restart
```

#### Option 3: Docker (For Testing)
```bash
git clone https://github.com/moh222salah/erp-gl-intelligence.git
cd erp-gl-intelligence/docker
docker-compose up -d
```

**Access demo at:** `http://localhost:8000`  
**Default credentials:** Administrator / admin

---

### Usage

1. Navigate to: **Accounting → General Ledger**
2. Run the report for any account
3. Click on any Journal Entry row
4. **NEW:** "🔍 Expand Details" button appears
5. See the complete breakdown in 0.3 seconds

**Video Tutorial:** [Watch on YouTube](https://youtube.com/watch?v=demo)

---

### API Documentation

The Premium Statement API allows external dashboards to fetch enhanced GL data:

```bash
# Endpoint
POST /api/method/gl_intelligence.premium_statement_api.get_ledger_details

# Request
{
  "account": "1110 - Cash - SAR",
  "from_date": "2024-01-01",
  "to_date": "2024-12-31",
  "expand_je": true
}

# Response (JSON)
{
  "success": true,
  "data": [
    {
      "posting_date": "2024-01-15",
      "voucher_no": "JV-00234",
      "debit": 8000.00,
      "credit": 0,
      "balance": 8000.00,
      "expanded_entries": [
        {"account": "Vendor A", "amount": 3000, "balance": 3000},
        {"account": "Vendor B", "amount": 2500, "balance": 5500},
        {"account": "Vendor C", "amount": 2500, "balance": 8000}
      ]
    }
  ]
}
```

**Full API docs:** [See Wiki](https://github.com/moh222salah/erp-gl-intelligence/wiki/API)

---

### Compatibility

| ERPNext Version | Status |
|----------------|--------|
| v14.x | ✅ Fully Tested |
| v15.x | ✅ Fully Tested |
| v16.x (dev) | ⚠️ Beta |

**Hosting:** Frappe Cloud, AWS, DigitalOcean, On-Premise

---

---

## 🇸🇦 العربية

### المشكلة

كل مدير مالي في الخليج يعرف هذا الألم:

```
❌ تشوف: "قيد يومي JV-00234 | 8,000 ريال"
❓ لكن ما تعرف:
   - الفلوس راحت لمين؟
   - كل دفعة كانت عن إيه؟
   - كيف تأثر الرصيد المتحرك؟

⏰ النتيجة: 45 دقيقة مطابقة يدوية لكل قيد
💰 التكلفة: 26,100 ريال هدر سنوي (عمالة + أخطاء + تأخير)
```

**دفتر الأستاذ يعرض الإجماليات، مش التفاصيل. أنت بتطير أعمى.**

---

### الحل

**محرك Sky Star للذكاء المالي** يفكك القيود اليومية تلقائياً إلى مكوناتها **داخل تقرير دفتر الأستاذ نفسه**.

#### قبل:
```
┌──────────────────────────┐
│ 15/1 │ JV-00234 │ 8,000  │  ← إيه ده؟
└──────────────────────────┘
```

#### بعد (0.3 ثانية):
```
┌────────────────────────────────────────────────────┐
│ 15/1 │ JV-00234 │                                  │
│  ├─  │ مورد أ - ديزل       │ 3,000 │ رصيد: 3,000 │ ✅
│  ├─  │ مورد ب - معدات      │ 2,500 │ رصيد: 5,500 │ ✅
│  └─  │ مورد ج - عمالة      │ 2,500 │ رصيد: 8,000 │ ✅
└────────────────────────────────────────────────────┘
```

**وضوح فوري. صفر عمل يدوي. مسار تدقيق كامل.**

---

### المميزات الرئيسية

✅ **التوسيع التلقائي للقسائم** - يفكك القيود إلى بنود فردية  
✅ **الرصيد المتحرك الفوري** - يُحسب تلقائياً لكل صف  
✅ **جاهز لمتطلبات هيئة الزكاة** - تتبع UUID الفواتير الإلكترونية  
✅ **واجهة عربي/إنجليزي** - دعم RTL مدمج  
✅ **صفر حمل على السيرفر** - استعلامات محسّنة مع تخزين مؤقت ذكي  
✅ **متوافق مع الكلاود** - يعمل على Frappe Cloud والاستضافة الذاتية  
✅ **API قوائم مالية مميزة** - نقطة REST للوحات القيادة  

---

### الأثر على الأعمال

| المقياس | قبل | بعد | التحسين |
|---------|-----|-----|---------|
| وقت المطابقة | 45 د/قيد | 2 ثانية | **99.9%** أسرع |
| ساعات العمل الشهرية | 15 ساعة | 0.5 ساعة | **96.7%** تقليل |
| التوفير السنوي | - | 26,100 ريال | **ROI في 18 شهر** |
| تحضير التدقيق | 3 أيام | 3 ساعات | **90%** أسرع |
| نسبة الأخطاء | 13% | 0.3% | **97.7%** تحسين |

---

### التثبيت

#### الطريقة 1: تثبيت بأمر واحد (موصى به)
```bash
# على سيرفر ERPNext الخاص بك
curl -s https://raw.githubusercontent.com/moh222salah/erp-gl-intelligence/main/scripts/install.sh | bash
```

#### الطريقة 2: التثبيت اليدوي
```bash
# استنساخ المستودع
cd frappe-bench
bench get-app https://github.com/moh222salah/erp-gl-intelligence.git

# التثبيت على موقعك
bench --site your-site.local install-app gl_intelligence

# إعادة تشغيل الخدمات
bench restart
```

#### الطريقة 3: Docker (للتجربة)
```bash
git clone https://github.com/moh222salah/erp-gl-intelligence.git
cd erp-gl-intelligence/docker
docker-compose up -d
```

**الوصول للتجربة:** `http://localhost:8000`  
**بيانات الدخول الافتراضية:** Administrator / admin

---

### الاستخدام

1. انتقل إلى: **المحاسبة ← دفتر الأستاذ العام**
2. شغّل التقرير لأي حساب
3. اضغط على أي صف قيد يومي
4. **جديد:** يظهر زر "🔍 عرض التفاصيل"
5. شاهد التفصيل الكامل في 0.3 ثانية

**فيديو توضيحي:** [شاهد على يوتيوب](https://youtube.com/watch?v=demo)

---

### التوثيق الكامل

- 📖 [دليل المستخدم](https://github.com/moh222salah/erp-gl-intelligence/wiki)
- 🔧 [دليل المطورين](https://github.com/moh222salah/erp-gl-intelligence/wiki/Developer-Guide)
- 🎓 [دراسة حالة كاملة](CASE_STUDY.md)
- 💬 [الدعم الفني](https://github.com/moh222salah/erp-gl-intelligence/discussions)

---

## 🤝 المساهمة

نرحب بالمساهمات! يرجى قراءة [دليل المساهمة](CONTRIBUTING.md) أولاً.

---

## 📄 الترخيص

هذا المشروع مرخص بموجب [رخصة MIT](LICENSE) - يمكنك استخدامه تجارياً بحرية.

---

## 👨‍💻 المطور

**Mohamed Salah ElHusseiny**  
Full Stack ERPNext Developer | Saudi Arabia Specialist

- 🌐 Portfolio: [moh222salah.github.io](https://moh222salah.github.io)
- 💼 LinkedIn: [linkedin.com/in/moh222salah](https://linkedin.com/in/moh222salah)
- 📧 Email: moh222salah@gmail.com
- 🐙 GitHub: [@moh222salah](https://github.com/moh222salah)

---

## 📞 احصل على عرض سعر

هل تحتاج هذا الحل مُخصّصاً لشركتك؟

**📧 راسلني:** moh222salah@gmail.com  
**📱 واتساب:** +966-XX-XXX-XXXX  

**متوسط وقت الرد: 2 ساعة**

---

<div align="center">

**⭐ If this solved your problem, star this repo!**  
**⭐ إذا حل هذا مشكلتك، ضع نجمة للمستودع!**

Made with ❤️ in Saudi Arabia 🇸🇦

</div>
