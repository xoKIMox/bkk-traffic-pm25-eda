# 🏙️ Bangkok Urban Traffic & PM2.5 EDA
**Exploratory Data Analysis on Transportation and Environmental Impacts**

## 📌 Project Overview
การศึกษาเชิงสำรวจ (EDA) เพื่อวิเคราะห์ความสัมพันธ์ระหว่างความหนาแน่นของการจราจร สภาพอากาศ และระดับฝุ่นละออง PM 2.5 ในเขตกรุงเทพมหานคร ช่วงปี 2024 - 2025[cite: 3, 4] โปรเจกต์นี้มุ่งเน้นไปที่การค้นหา "จุดวิกฤต (Hotspots)" และปัจจัยแฝงทางอุตุนิยมวิทยาที่ส่งผลกระทบต่อคุณภาพอากาศ[cite: 3]

## 🛠️ Tech Stack & Tools
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Data Visualization:** Matplotlib (Sarabun font integrated), Seaborn[cite: 4]
* **Environment:** Google Colab

## 🚀 Data Processing Pipeline (QA & Data Quality Focus)
โปรเจกต์นี้ให้ความสำคัญกับความถูกต้องของข้อมูล (Data Integrity) โดยผ่านกระบวนการดังนี้:

1. **Multi-source Integration:** ผสานรวมชุดข้อมูล 3 แหล่ง ได้แก่ ข้อมูลปริมาณจราจร, ข้อมูลคุณภาพอากาศ (PM 2.5), และข้อมูลสภาพอากาศ[cite: 4]
2. **Spatial Interpolation:** ใช้เทคนิค Inverse Distance Weighting (IDW) ในการประมาณค่าฝุ่น PM 2.5 ให้ตรงกับพิกัดละติจูด/ลองจิจูดของสี่แยกจราจร[cite: 4]
3. **Data Cleansing & Missing Values:** ตรวจสอบความสมบูรณ์ของชุดข้อมูลระดับ Master Data ทั้งปี 2024 และ 2025 โดยไม่พบ Missing Values ในทุกคอลัมน์[cite: 4]
4. **Outlier Detection & Handling:** ตรวจจับความผิดปกติของเซ็นเซอร์ด้วย IQR Method และ Domain Knowledge โดยทำการตัดค่าที่เป็นไปไม่ได้ทางกายภาพ (เช่น PM 2.5 แบบติดลบ หรือค่าสูงเกิน 500 µg/m³) ซึ่งสามารถรักษาปริมาณข้อมูล (Data Preservation) ไว้ได้มากกว่า 99%[cite: 4]
5. **Feature Engineering:** 
   * คำนวณ `Traffic_Flow_per_Hour` เพื่อปรับมาตรฐานความหนาแน่นจราจรให้เปรียบเทียบกันได้ในทุกช่วงเวลา[cite: 4]
   * สร้าง `Traffic_Wind_Ratio_Log` เพื่อประเมินสภาวะ "รถหนาแน่นแต่ลมนิ่ง" และลดความเบ้ของข้อมูล (Skewness)[cite: 4]

## 📊 Key Findings & Actionable Insights
จากการวิเคราะห์แบบ Univariate และ Multivariate สรุปผลได้ดังนี้:
* **The Hidden Factor:** ตัวแปรหลักที่ควบคุมปริมาณ PM 2.5 คือ **สภาพอากาศ (อุณหภูมิ, ความเร็วลม, ความกดอากาศ)** ไม่ใช่ปริมาณรถยนต์โดยตรง[cite: 4]
* **Traffic vs. PM 2.5 Correlation:** ค่าความสัมพันธ์ (Pearson r) ระหว่างปริมาณรถยนต์รวมกับฝุ่น PM 2.5 มีค่าเข้าใกล้ศูนย์และไม่มีนัยสำคัญทางสถิติในทุกฤดูกาล[cite: 4]
* **Hotspots Mismatch:** เขตที่มีปัญหาการจราจรติดขัดสูงสุด ไม่จำเป็นต้องเป็นเขตที่มีค่าเฉลี่ยฝุ่น PM 2.5 สูงสุดเสมอไป[cite: 3, 4]

## 📂 Project Structure
* `final_final_code_(2).ipynb`: Source code หลักที่ใช้ในการทำ Data Cleaning, Feature Engineering และ Data Visualization[cite: 4] https://drive.google.com/drive/folders/1jIcGE6e0ny5n0R_bpGFjO6xWnkW9E7vA
* `EDA3_กลุ่มที่ 7.pdf`: สไลด์นำเสนอผลการวิเคราะห์และข้อค้นพบเชิงลึก[cite: 3] https://canva.link/p5si0oq8x7fa13b
