# 🚀 Strapi คืออะไร ?

Strapi เป็น Headless CMS (Content Management System) ที่ช่วยให้นักพัฒนาสามารถสร้างและจัดการ API ได้อย่างรวดเร็วและง่ายดาย

## Table of Contents

### `Use cases`

ใช้ในการสร้างระบบจัดการเนื้อหาของเว็บแอปพลิเคชันที่สามารถขยายได้ง่าย
ทำหน้าที่เป็น backend สำหรับเว็บหรือ mobile applications
ใช้สำหรับการพัฒนา API ที่ต้องการจัดการข้อมูลหลายแบบ

### องค์ประกอบหลักของ Strapi

- Content Type Builder ใช้ในการสร้างและจัดการ content types
- Admin Panel หน้าจอสำหรับจัดการเนื้อหา
- REST/GraphQL API เป็น endpoints ที่สร้างจาก content types
- Plugins ใช้สำหรับเพิ่มฟีเจอร์พิเศษ

## ติดตั้ง Strapi บนเครื่องส่วนตัว
- ติดตั้ง Node.js [ version 18 ++ ]
- ติดตั้ง npm [ version 6 -- ]

### ใช้ CLI ติดตั้ง Strapi ด้วยคำสั่ง

```
npx create-strapi-app my-project --quickstart
```

### รัน Strapi บนเครื่อง

```
cd my-project
npm run develop
```

## ✨ไฟล์ .gitignore

ไฟล์ .gitignore ใช้สำหรับระบุไฟล์หรือโฟลเดอร์ที่ไม่ต้องการให้ Git ติดตาม เช่น ไฟล์ที่เป็น output, log files, หรือไฟล์ที่มีข้อมูลส่วนบุคคล
คุณสามารถแก้ไขไฟล์ .gitignore เพื่อเพิ่มหรือเอาไฟล์ที่ไม่ต้องการออกจากการติดตามได้ตามที่จำเป็น`

### `Key Entries`
- node_modules/: Directory containing all npm dependencies.
- .tmp/: Temporary files created by Strapi.
- .env: Environment variables that may contain sensitive information.

## ⚙️ Deployment on AWS

AWS Setup

### `Create an EC2 Instance`

Choose Amazon Linux 2 or Ubuntu as the AMI.
Select an instance type (e.g., t2.micro for testing).
Configure security groups to allow HTTP/HTTPS and the port used by Strapi (default is 1337).

### `Install Node.js and Git on EC2`

```
sudo yum update -y
sudo yum install -y git
curl -sL https://rpm.nodesource.com/setup_14.x | sudo bash -
sudo yum install -y nodejs
```

### `Clone the Repository and Install Dependencies`

```
git clone https://github.com/ํYolwadee6509650070/my-strapi-project.git
cd my-strapi-project
npm install
```

### `Start Strapi on EC2`

```
npm run build
npm run start
```

### `Access the Application`

Access Strapi through the EC2 public IP at http://your-ec2-public-ip:1337/admin.

## Configuring Security Groups

Ensure that the security group associated with your EC2 instance allows inbound traffic on the necessary ports (e.g., 1337 for Strapi, 22 for SSH).

## 📚 Learn more

- Strapi Documentation
- AWS Documentation
- FreeCodeCamp Guide on Writing README
