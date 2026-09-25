# Cloud Storage เบื้องต้น

> [!NOTE]
> ตัวอย่างในบทความใช้ข้อมูลของ "โรงงานตัวอย่าง" (Demo Plant)

## 🗄️ Cloud Storage คืออะไร

Cloud Storage คือที่เก็บไฟล์ (Object Storage) บน Google Cloud
เก็บได้ทุกชนิด เช่น CSV, รูปภาพ, ไฟล์ Backup และมักใช้เป็นจุดพักข้อมูลก่อนโหลดเข้า [BigQuery](bigquery-basics.md)

**คำศัพท์ที่ต้องรู้**

| คำศัพท์ | ความหมาย |
|---|---|
| Bucket | "ถัง" สำหรับเก็บไฟล์ ชื่อต้องไม่ซ้ำกับใครในโลก |
| Object | ไฟล์แต่ละไฟล์ที่อยู่ใน Bucket |
| Location | ที่ตั้งของข้อมูล เช่น `asia-southeast1` (สิงคโปร์) |

## 💰 เลือก Storage Class ให้เหมาะ

| Class | เหมาะกับ | เก็บขั้นต่ำ |
|---|---|---|
| Standard | ไฟล์ที่ใช้บ่อย | ไม่มี |
| Nearline | ใช้ประมาณเดือนละครั้ง | 30 วัน |
| Coldline | ใช้ประมาณไตรมาสละครั้ง | 90 วัน |
| Archive | เก็บยาว แทบไม่ได้เปิด | 365 วัน |

> [!WARNING]
> Class ที่ราคาเก็บถูก จะมีค่าดึงข้อมูลออก และถ้าลบก่อนครบระยะขั้นต่ำก็ยังถูกคิดเงินเต็มระยะ

## 🧪 ลองใช้งานด้วย gcloud

```bash
# 1. สร้าง Bucket
gcloud storage buckets create gs://demo-plant-raw-data --location=asia-southeast1

# 2. อัปโหลดไฟล์
gcloud storage cp production.csv gs://demo-plant-raw-data/

# 3. ดูรายการไฟล์
gcloud storage ls gs://demo-plant-raw-data/
```

> [!TIP]
> รันคำสั่งเหล่านี้ได้ทันทีใน **Cloud Shell** (ไอคอน `>_` มุมขวาบนของ Google Cloud Console) ไม่ต้องติดตั้งอะไรในเครื่อง

## ✅ สรุป

- Cloud Storage ใช้เก็บไฟล์ โดยจัดเป็น Bucket
- เลือก Storage Class ตามความถี่ในการใช้งาน
- ใช้ `gcloud storage` จัดการไฟล์ได้จาก Cloud Shell
