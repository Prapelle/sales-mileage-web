# เบิกค่าเดินทาง — หน้าเว็บ Sales (PWA)

ไฟล์เดียว ไม่มี build ใช้คู่กับ Worker ใน repo `sales-mileage` ทำงานแบบออฟไลน์ได้ (เก็บคิวไว้ส่งเมื่อมีสัญญาณ)

## ตั้งค่า
1. สร้าง repo **public** ชื่อ `sales-mileage-web` (GitHub Pages ของ repo private ต้องใช้แพ็กเกจเสียเงิน; ไฟล์นี้ไม่มีความลับ) แล้วอัปโหลดไฟล์ทั้งหมดไว้ชั้นนอกสุด
2. Settings → Pages → Branch `main` / root → Save (ได้ลิงก์ `https://prapelle.github.io/sales-mileage-web/`)
3. แก้ `CONFIG` ที่หัว `<script>` ใน `index.html`:
   - `API_BASE` = URL ของ Worker (`https://....workers.dev`)
   - `GOOGLE_CLIENT_ID` = OAuth Client ID เดียวกับที่ตั้งใน Worker
4. Google Cloud → OAuth client → Authorized JavaScript origins ต้องมี `https://prapelle.github.io`
5. พนักงานเปิดลิงก์ในมือถือ → เมนูเบราว์เซอร์ → "เพิ่มลงหน้าจอหลัก" (iPhone: Safari → แชร์ → Add to Home Screen)

## การทำงาน
- เริ่มเดินทาง: ถ่ายภาพ + กรอกเลขไมล์ → กด "ถึงแล้ว" ทุกจุด → สิ้นสุดวัน: ถ่ายภาพ + กรอกเลขไมล์ → ส่งตรวจ
- ภาพถูกย่อบนเครื่องก่อนส่ง (ด้านยาวสุด 1280px, JPEG) เหลือราว 100–300 KB
- ทุกการกระทำถูกบันทึกในเครื่องก่อน แล้วส่งตามลำดับเมื่อออนไลน์ ถ้าเซิร์ฟเวอร์ปฏิเสธ (เช่น วันที่เก่าเกิน) จะแจ้งเตือนในหน้าแรก
- ข้อมูลที่ยังไม่ส่งไม่หายแม้ปิดแอปหรือเซสชันหมดอายุ
