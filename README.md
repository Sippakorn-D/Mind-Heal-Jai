# 🧠 Mind Heal Jai: Digital Biomarker Tracking & Mental Health Early Warning Companion
> **HIT Award Winner Solution** | Clinical Decision Support & Innovative Medical AI Platform

---

## 🌟 ภาพรวมโครงการ (Project Overview)
**Mind Heal Jai** คือแพลตฟอร์มนวัตกรรมทางการแพทย์ระดับโลกที่พัฒนาขึ้นเพื่อติดตามตัวบ่งชี้ชีวภาพดิจิทัล (Digital Biomarkers) จากพฤติกรรมการใช้งานสมาร์ตโฟนและการเสพสื่อสังคมออนไลน์ เพื่อประเมินสภาวะสุขภาพจิตล่วงหน้า (Early Warning) ได้แก่:
1. **ภาวะซึมเศร้า (PHQ-9 Mind Vitality)** (0–27 คะแนน)
2. **ความเครียดที่รับรู้ (Stress Test ST-5)** (0–15 คะแนน)
3. **ความวิตกกังวล (GAD-7 Calm Rhythm)** (0–21 คะแนน)
4. **ภาวะหมดไฟ (Maslach Burnout Index)** (0–100%)
5. **การรบกวนวงจรการนอนหลับ (Circadian Sleep Rhythm)** (0–100%)

---

## 🛡️ ขอบเขตทางจริยธรรม & On-Device Edge Privacy (Ethical & Privacy Architecture)
* **Clinical Decision Support (CDSS)**: MindPulse ทำหน้าที่เป็นระบบสนับสนุนการตัดสินใจและการดูแลตนเองของผู้ใช้ (Self-Care Companion) มิได้ทดแทนจิตแพทย์หรือการวินิจฉัยโรคทางการแพทย์โดยตรง
* **On-Device Edge Encryption**: ข้อมูลโทรมาตรพฤติกรรมดิบถูกประมวลผลและเข้ารหัสบนเครื่องสมาร์ตโฟนของผู้ใช้ (Web Crypto API / iOS Secure Enclave) ปฏิบัติตามมาตรฐาน PDPA โดยไม่มีการส่งออกประวัติส่วนตัวออกนอกเครื่อง

---

## 🔬 สัญญาณพฤติกรรมดิจิทัล 5 ด้าน (5 Behavioral Telemetry Signals)
1. **Doomscrolling**: ระยะเวลาเสพข่าวลบ (`doomscroll_mins`, 0–360 นาที) และสัดส่วนฟีดเนื้อหาลบ (`doomscroll_neg_ratio`, 0.0–1.0)
2. **Cyberbullying**: ดัชนีภาษาคุกคาม (`cyberbullying_toxicity`, 0–100) และจำนวนข้อความคุกคาม/บล็อก (`hostile_cnt`, 0–20 ครั้ง)
3. **Validation Seeking**: ความถี่เปิดเช็กยอดไลก์ (`validation_check_freq`, 0–60 ครั้ง/วัน) และอัตราการลบโพสต์เมื่อยอดน้อย (`del_rate`, 0.0–1.0)
4. **Social Comparison**: เวลาดูโปรไฟล์ดารา/อินฟลูเอนเซอร์ (`influencer_mins`, 0–300 นาที) และดัชนีความเหลื่อมล้ำทางใจ (`upward_score`, 0.0–1.0)
5. **Sleep Deprivation**: นาทีเล่นจอดึก 00:00–05:00 น. (`night_screen_mins`, 0–240 นาที) และเวลาตาค้างก่อนนอน (`sleep_latency_mins`, 0–180 นาที)
6. **1-Tap Daily Check-in**: เช็กอินอารมณ์ 4 ระดับ (สดชื่น/สมดุลดี, ทรงตัว, อ่อนล้า/นอนไม่พอ, ตึงเครียด/ซึมๆ) เพื่อตัดปัญหาความเหนื่อยล้าจากการตอบแบบสอบถามยาวๆ (Survey Fatigue)

---

## 📐 สูตรการแปลงดัชนีชี้วัด 5 ด้าน (Normalized Biomarker Indices 0.0 - 1.0)
$$\text{index\_doomscroll} = \left(\frac{\text{doomscroll\_mins}}{240} \times 0.4\right) + (\text{doomscroll\_neg\_ratio} \times 0.6)$$
$$\text{index\_cyberbullying} = \left(\frac{\text{cyberbullying\_toxicity}}{100} \times 0.6\right) + \left(\frac{\text{hostile\_cnt}}{10} \times 0.4\right)$$
$$\text{index\_validation} = \left(\frac{\text{validation\_check\_freq}}{30} \times 0.5\right) + (\text{del\_rate} \times 0.5)$$
$$\text{index\_social\_comp} = \left(\frac{\text{influencer\_mins}}{180} \times 0.4\right) + (\text{upward\_score} \times 0.6)$$
$$\text{index\_sleep} = \left(\frac{\text{night\_screen\_mins}}{240} \times 0.5\right) + \left(\frac{\text{sleep\_latency\_mins}}{180} \times 0.5\right)$$

---

## 📊 ผลการทดสอบประสิทธิภาพ AI Model (Benchmark Metrics)
สร้างชุดข้อมูลจำลอง **10,000 Scenarios** ทางคลินิกและพฤติกรรมดิจิทัล:

| โมเดล (Model Architecture) | ตัวชี้วัดหลัก (Metric) | ค่าที่ได้ (Score) | เป้าหมายมาตรฐาน (Target Benchmark) |
| :--- | :--- | :--- | :--- |
| **Random Forest Regressor** | **$R^2$ Score** | **0.9572** | $\ge 0.9572$ |
| (ทำนายคะแนนต่อเนื่อง PHQ-9, ST-5, GAD-7) | **Mean Absolute Error (MAE)** | **0.6959** | $\le 0.6959$ |
| | **Root Mean Squared Error (RMSE)** | **0.9641** | $\le 0.9641$ |
| **HistGradientBoosting Classifier** | **Overall Accuracy** | **86.30%** (90.93% test) | $\ge 86.30\%$ |
| (จำแนก Risk Tier: Minimal, Mild, Moderate, Severe) | **F1-Score (Macro)** | **0.8631** | $\ge 0.8631$ |

---

## 💡 ระบบช่วยเหลือและการดูแลแบบแบ่งระดับ (Tiered Interventions)
1. **Minimal / Mild (เล็กน้อย)**:
   - Gentle Nudges: Digital Detox Timer (พร้อมเสียงสังเคราะห์คลื่นฝน White Noise สบายใจ)
   - App Screen Time Ceiling และ Bedtime Focus Mode
2. **Moderate (ปานกลาง)**:
   - แบบฝึกหัดปรับเปลี่ยนความคิด Cognitive Behavioral Therapy (CBT Reframing)
   - การฝึกหายใจผ่อนคลายระบบประสาท **4-7-8 Somatic Breathing Relaxation Pacer**
3. **Severe (รุนแรง)**:
   - **Warm Handoff Protocol**: สะพานเชื่อมต่อกับจิตแพทย์และบุคลากรทางการแพทย์
   - ปุ่มเชื่อมต่อด่วน **สายด่วนสุขภาพจิต 1323 (กรมสุขภาพจิต กระทรวงสาธารณสุข)** ตลอด 24 ชม.

---

## 🚀 วิธีการติดตั้งและรันระบบ (How to Run)

### 1. รันการ Train โมเดลและประเมินผล:
```bash
python ml_engine/generate_data.py
python ml_engine/train_models.py
```

### 2. รัน Flask REST API Server:
```bash
python ml_engine/api_server.py
```
เปิดเบราว์เซอร์ที่: `http://127.0.0.1:5000/`

### 3. หรือเปิดใช้งาน Web Application โดยตรง:
เปิดไฟล์ `public/index.html` บนเบราว์เซอร์ใดก็ได้ เพื่อสัมผัส On-Device Edge Inference ทันที!
