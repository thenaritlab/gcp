# BigQuery เบื้องต้น

> [!NOTE]
> บทความตัวอย่าง ใช้ข้อมูลของ "โรงงานตัวอย่าง" (Demo Plant)

## 🤔 BigQuery คืออะไร

BigQuery คือ Data Warehouse แบบ Serverless ของ Google Cloud
ไม่ต้องดูแลเซิร์ฟเวอร์ จ่ายตามปริมาณข้อมูลที่ query

| หัวข้อ | รายละเอียด |
|---|---|
| ประเภท | Data Warehouse (Serverless) |
| ภาษา | SQL มาตรฐาน |
| คิดเงิน | ตามข้อมูลที่สแกน หรือแบบเหมา (Capacity) |

> [!TIP]
> ใช้ `SELECT` เฉพาะคอลัมน์ที่ต้องการ แทน `SELECT *` จะประหยัดค่าใช้จ่ายได้มาก

## 🧪 ลอง Query แรก

```sql
SELECT plant_name, SUM(output_qty) AS total_output
FROM `demo_plant.production`
GROUP BY plant_name
ORDER BY total_output DESC;
```
