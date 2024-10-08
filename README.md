# 🚀 Strapi คืออะไร?
Strapi คือโปรแกรม Headless CMS (Content Management System) ที่เป็นโอเพนซอร์ส ซึ่งนักพัฒนาสามารถนำไปใช้สร้าง API ด้วย Javascript ได้อย่างรวดเร็ว และยังเป็นบริการที่ใช้งานได้ฟรี มีความยืดหยุ่น บริหารจัดการได้ง่าย


## 📋 สารบัญ
- [วัตถุประสงค์](#-วัตถุประสงค์)
- [Use Cases](#-use-cases)
- [องค์ประกอบหลักของ Strapi](#-องค์ประกอบหลักของ-strapi)
- [การติดตั้ง Strapi บน Local Machine](#การติดตั้ง-strapi-บน-local-machine)
- [ไฟล์ .gitignore](#-ไฟล์-gitignore)
- [Deployment on AWS](#deployment-on-aws)
- [Configuring Security Groups](#-configuring-security-groups)
- [เรียนรู้เพิ่มเติม](#-เรียนรู้เพิ่มเติม)

## `🎯 วัตถุประสงค์`

- ช่วยในการสร้าง API โดย Strapi สร้าง RESTful API หรือ GraphQL API อัตโนมัติจาก Content Types ที่กำหนด
- จัดการเนื้อหาผ่านแผงผู้ดูแลระบบที่ใช้งานง่าย
- รองรับการเพิ่มฟีเจอร์ด้วย Plugins และสามารถปรับแต่งได้ตามความต้องการของโปรเจกต์
- เป็นโปรเจกต์ open source ที่เปิดรับการมีส่วนร่วมจากชุมชนในการพัฒนาและปรับปรุง

## `🛠 Use Cases`

   - จัดการเนื้อหาเว็บไซต์/แอปพลิเคชัน
   - ทำหน้าที่เป็นระบบ backend สำหรับเว็บหรือ mobile applications
   - สร้างและจัดการ API โดย สร้าง RESTful หรือ GraphQL API สำหรับข้อมูลต่างๆ
   - ปรับแต่ง Content Types ได้ตามโปรเจกต์
   - เขยายฟีเจอร์ด้วย Plugins และปรับแต่งได้ตามต้องการ
   - จัดการผู้ใช้และสิทธิ์
   - ใช้ APIs ติดต่อกับบริการภายนอก เช่น CRM หรือคลาวด์

## `🔧 องค์ประกอบหลักของ Strapi`

- **Content Type Builder** ใช้ในการสร้างและจัดการ content types
- **Admin Panel** หน้าจอสำหรับจัดการเนื้อหา
- **REST/GraphQL API** เป็น endpoints ที่สร้างจาก content types
- **Plugins** ใช้สำหรับเพิ่มฟีเจอร์พิเศษ

## 📚 แหล่งอ้างอิง

- [Strapi Documentation](https://docs.strapi.io/dev-docs/intro)
- [Morphos - What is Strapi and How It Will Dominate the World of Headless CMS](https://morphos.is/th/blog/what-is-strapi-and-how-it-will-dominate-the-world-of-headless-cms)


## ⚙️ การติดตั้ง Strapi บน Local Machine

### 1. ติดตั้ง Dependencies

- Node.js (v18.x ++)
- npm (v6.x --)
- Git

### 2. เปิดหน้าจอ Terminal

- ปุ่มลัด: Window + R
- หรือ เสิร์ชในช่อง Window ที่หน้าต่าง 'Command Prompt'

### 3. ใช้ CLI ติดตั้ง Strapi ด้วยคำสั่ง

```
npx create-strapi-app my-project --quickstart

```

### 4. รัน Strapi บนเครื่อง

```
cd my-project
npm run develop
```

### 5. เข้าสู่หน้า Admin Panel

- เมื่อ Strapi ทำงานจะให้เข้าถึงหน้าต่าง Admin Panel ด้วย

```
http://localhost:1337/admin/register
```

## แหล่งอ้างอิง
- [Strapi Installation](https://docs.strapi.io/dev-docs/installation) 

  
## ✨ ไฟล์ .gitignore

ไฟล์ `.gitignore` ใช้สำหรับระบุไฟล์หรือโฟลเดอร์ที่ไม่ต้องการให้ Git ติดตาม เช่น ไฟล์ที่เป็น output, log files, หรือไฟล์ที่มีข้อมูลส่วนบุคคล สามารถแก้ไขไฟล์ `.gitignore` เพื่อเพิ่มหรือเอาไฟล์ที่ไม่ต้องการออกจากการติดตามได้ตามที่จำเป็น

### Key Entries 

- `node_modules/`: ไดเร็กทอรีที่มีการใช้ npm ทั้งหมด
- `.tmp/`: ไฟล์ชั่วคราวที่สร้างโดย Strapi
- `.env`: Environment variables ที่อาจมีข้อมูลที่ละเอียดอ่อน


## ⚙️ Deployment on AWS

### 1. สร้าง EC2 Instance
- เลือก Amazon Linux 2 หรือ Ubuntu เป็น AMI
- เลือกประเภท instance (เช่น t2.midium สำหรับการทดสอบ)
- ใส่ key pair 
- ตั้งค่า network เพิ่มเติม โดยเพิ่มการอนุญาต HTTP/HTTPS/TCP (0.0.0.0) และพอร์ตที่ใช้โดย Strapi (ค่าเริ่มต้นคือ 1337)

### 2. ติดตั้ง Node.js, npm และ Git บน EC2

```
sudo apt update -y
sudo apt install -y git
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt install -y nodejs
sudo apt install npm -y
```

### 3. Clone Code จาก Git Repository และ ติดตั้ง Dependencies

```
git clone https://github.com/Yolwadee6509650070/my-strapi-project.git
cd my-strapi-project
npm install
```

### 4. Configuration

I. **Environment Variables**

  - สร้าง `API_TOKEN_SALT`, `ADMIN_JWT_SECRET`, `TRANSFER_TOKEN_SALT`, `JWT_SECRET`, `APPKEY1`, `APPKEY2` ด้วยคำสั่ง Node.js
    
    ```
    node -e "console.log(require('crypto').randomBytes(16).toString('base64'));"
    ```
  - เซ็ต environment
   
    ```
    nano ~/my-strapi-project/.env
    ```
  - Copy รหัสที่สร้างจากคำสั่ง Node.js มาใส่
    ```
    JWT_SECRET=YOURKEY
    API_TOKEN_SALT=YOURKEY
    TRANSFER_TOKEN_SALT=YOURKEY
    ADMIN_JWT_SECRET=YOURKEY
    ```

II. **Admin Configuration**
   
  - อัพเดท `config/admin.js` ตามด้านล่างนี้
  - เซ็ต Admin
   
    ```
    nano ~/my-strapi-project/my-strapi-project/config/admin.js
    ```
  - แทนค่า Yourkey ด้วย ADMIN_JWT_SECRET ที่สร้างขึ้น

    ```
    module.exports = ({ env }) => ({
    auth: {
    secret: env('ADMIN_JWT_SECRET','Yourkey'),
    },
    apiToken: {
    salt: env('API_TOKEN_SALT'),
    },
    transfer: {
    token: {
    salt: env('TRANSFER_TOKEN_SALT'),
    },
    },
    flags: {
    nps: env.bool('FLAG_NPS', true),
    promoteEE: env.bool('FLAG_PROMOTE_EE', true),
    },
    });
    ```

III. **Server Configuration**
   - อัพเดท `config/server.js` ตามด้านล่างนี้
   - เซ็ต Admin
   
  ```
    nano ~/my-strapi-project/my-strapi-project/config/server.js
  ```
   - ด้วย APPKEY1, APPKEY2  ที่สร้างขึ้น

  ```
    module.exports = ({ env }) => ({
    host: env('HOST', '0.0.0.0'),
    port: env.int('PORT', 1337),
    app: {
    keys: env.array('APP_KEYS', [
      'YourAppKey1',
      'YourAppKey2'
    ]),
    },
    });
  ```

### 4. รัน Strapi บนเครื่อง EC2

```
npm run build
npm run start
```

### 5. เข้าสู่หน้า Admin Panel

- เข้าถึง Strapi ผ่าน IP public ของ EC2 ที่ http://your-ec2-public-ip:1337/admin

## 🔒 Configuring Security Groups
- ตรวจสอบให้แน่ใจว่า security group ในการตั้งค่า EC2 instance อนุญาตการรับส่งข้อมูลขาเข้าบนพอร์ตที่จำเป็น 
- **Port 22 (TCP):** สำหรับ SSH access to the server.
- **Port 80 (TCP):** สำหรับ HTTP traffic.
- **Port 443 (TCP):** สำหรับ HTTPS traffic.
- **Port 1337 (TCP):** สำหรับ accessing the Strapi application.

## 📚 เรียนรู้เพิ่มเติม

- Strapi Documentation
- AWS Documentation
- FreeCodeCamp Guide on Writing README



