# HikeGoOn - แพลตฟอร์มค้นหาและจองสถานที่แคมป์ปิ้ง

## 📋 รายละเอียดโปรเจ็ค

HikeGoOn เป็นแพลตฟอร์มสำหรับค้นหา จอง และแชร์สถานที่แคมป์ปิ้งในประเทศไทย รวมถึงซื้อขายอุปกรณ์แคมป์ปิ้ง

### ฟีเจอร์หลัก
- 🏕️ ค้นหาและจองสถานที่แคมป์ปิ้ง
- 🛒 ซื้อขายอุปกรณ์แคมป์ปิ้ง
- ⭐ รีวิวและให้คะแนนสถานที่แคมป์ปิ้ง
- 👤 ระบบสมาชิกและโปรไฟล์
- ❤️ บันทึกรายการโปรด

## 🚀 การติดตั้งและใช้งาน

### ความต้องการของระบบ
- Node.js 18.x หรือใหม่กว่า
- npm 9.x หรือใหม่กว่า

### ขั้นตอนการติดตั้ง

1. โคลนโปรเจ็ค
\`\`\`bash
git clone https://github.com/yourusername/hikegoon.git
cd hikegoon
\`\`\`

2. ติดตั้ง dependencies
\`\`\`bash
npm install
\`\`\`

3. ตั้งค่า environment variables
\`\`\`bash
cp .env.example .env.local
\`\`\`
แก้ไขไฟล์ .env.local และใส่ค่า API keys ที่จำเป็น

4. รันโปรเจ็คในโหมด development
\`\`\`bash
npm run dev
\`\`\`

5. เปิดเบราว์เซอร์และเข้าไปที่ http://localhost:3000

## 📁 โครงสร้างโปรเจ็ค

\`\`\`
/app                      # Next.js App Router
  /api                    # API Routes
  /(auth)                 # Authentication routes
  /(main)                 # Main public routes
  /(features)             # Feature-specific routes

/components               # Shared components
  /auth                   # Authentication components
  /campsite               # Campsite-related components
  /equipment              # Equipment-related components
  /layout                 # Layout components
  /reviews                # Review components
  /ui                     # UI components

/lib                      # Utility functions and libraries
  /actions                # Server actions
  /hooks                  # Custom React hooks
  /supabase               # Supabase client and utilities
  /utils                  # General utility functions

/public                   # Static assets
/styles                   # Global styles
\`\`\`

## 🧩 คอมโพเนนต์หลัก

### 1. คอมโพเนนต์สถานที่แคมป์ปิ้ง
- `CampsiteCard`: แสดงข้อมูลสถานที่แคมป์ปิ้งแบบย่อ
- `CampsiteDetail`: แสดงรายละเอียดสถานที่แคมป์ปิ้ง
- `CampsiteForm`: ฟอร์มสำหรับเพิ่มหรือแก้ไขสถานที่แคมป์ปิ้ง

### 2. คอมโพเนนต์อุปกรณ์แคมป์ปิ้ง
- `EquipmentCard`: แสดงข้อมูลอุปกรณ์แคมป์ปิ้งแบบย่อ
- `EquipmentDetail`: แสดงรายละเอียดอุปกรณ์แคมป์ปิ้ง
- `EquipmentForm`: ฟอร์มสำหรับเพิ่มหรือแก้ไขอุปกรณ์แคมป์ปิ้ง

### 3. คอมโพเนนต์ผู้ใช้
- `AuthForm`: ฟอร์มสำหรับลงทะเบียนและเข้าสู่ระบบ
- `ProfilePage`: หน้าโปรไฟล์ผู้ใช้
- `BookingHistory`: ประวัติการจอง

## 🔧 การใช้งาน API

### Supabase API
โปรเจ็คนี้ใช้ Supabase เป็นฐานข้อมูลและ authentication service โดยมีการเรียกใช้ API ผ่าน client libraries

\`\`\`javascript
// ตัวอย่างการใช้งาน Supabase client
import { createClient } from '@/lib/supabase/client';

const fetchData = async () => {
  const supabase = createClient();
  const { data, error } = await supabase
    .from('campsites')
    .select('*');
  
  if (error) console.error('Error fetching data:', error);
  return data;
};
\`\`\`

### Server Actions
โปรเจ็คนี้ใช้ Next.js Server Actions สำหรับการทำงานฝั่ง server

\`\`\`javascript
// ตัวอย่างการใช้งาน Server Action
import { addCampsite } from '@/lib/actions/campsite-actions';

// ในคอมโพเนนต์
const handleSubmit = async (formData) => {
  const result = await addCampsite(formData);
  if (result.success) {
    // จัดการเมื่อสำเร็จ
  }
};
\`\`\`

## 👨‍💻 การพัฒนาต่อ

### การเพิ่มฟีเจอร์ใหม่
1. สร้างคอมโพเนนต์ใหม่ในโฟลเดอร์ที่เหมาะสม
2. เพิ่ม Server Action ถ้าจำเป็น
3. เพิ่มหน้าใหม่ใน App Router ถ้าจำเป็น

### แนวทางการตั้งชื่อ
- ไฟล์คอมโพเนนต์: ใช้ kebab-case (เช่น `campsite-card.jsx`)
- ชื่อคอมโพเนนต์: ใช้ PascalCase (เช่น `CampsiteCard`)
- ไฟล์ utility และ action: ใช้ kebab-case (เช่น `date-utils.js`)
- ชื่อฟังก์ชัน: ใช้ camelCase (เช่น `formatDate()`)

## 📚 เทคโนโลยีที่ใช้

- **Frontend**: Next.js, React, Tailwind CSS
- **Backend**: Next.js API Routes, Server Actions
- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth
- **Storage**: Supabase Storage
- **Deployment**: Vercel

## 📝 License

MIT License
