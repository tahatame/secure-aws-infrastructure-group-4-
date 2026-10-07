Week 1: Secure Network Core & Database Implementation
DEPI Team 4 - AWS Capstone Project
Implemented by: Taha Tamer

 ملخص مهام الأسبوع الأول (VPC, EC2, and Private RDS)
في هذا الأسبوع، تم بناء وتأمين البنية التحتية الأساسية للمشروع وتطبيق مبدأ الصلاحيات الأقل (Least Privilege) بنجاح من الصفر. تم تنفيذ المهام التالية:

1. إعداد تصريحات الأمان (IAM Role & SSM)

إنشاء Role مخصص (EC2-SSM-Role) وإرفاق سياسة AmazonSSMManagedInstanceCore.

الهدف: إدارة الخادم والتحكم فيه بأمان كامل من خلال خدمة (AWS Systems Manager) دون الحاجة لفتح منفذ SSH (Port 22) أو الاعتماد على مفاتيح التشفير التقليدية.

2. إطلاق سيرفر الويب (EC2 Instance)

إنشاء خادم متصل بالإنترنت (Ubuntu) داخل الشبكة العامة (Public Subnet).

ربط الخادم بـ Security Group مخصص للويب (Web-App-SG)، وتفعيل الـ IAM Role الخاص بالـ SSM للتحكم الآمن.

3. ضبط توجيه الشبكة (Route Table Configuration)

تحديث جدول التوجيه (Route Table) لضمان توجيه حركة المرور الخارجية 0.0.0.0/0 إلى بوابة الإنترنت (Internet Gateway)، مما سمح للموقع بالعمل بشكل سليم على المتصفح.

4. إعداد وتشغيل خادم الويب (Apache Web Server)

الدخول إلى السيرفر عبر الـ Terminal الخاص بـ Session Manager.

تثبيت خادم Apache، وتكوينه، ورفع صفحة ويب اختبارية لتوثيق عمل السيرفر باسم الفريق.

5. إنشاء قاعدة البيانات الآمنة (Private Amazon RDS)

إطلاق قاعدة بيانات MySQL داخل الشبكة الخاصة (Private Subnet) لعزلها تماماً.

تعطيل الوصول العام (Public Access = No).

ربط قاعدة البيانات بجدار الحماية المخصص (DB-SG) والذي يقيد أي وصول إلا من خلال سيرفر الويب الخاص بنا فقط.

6. اختبار الاتصال والأمان (Connectivity & Security Test)

تثبيت أداة mysql-client على سيرفر الويب.

تنفيذ اختبار اتصال ناجح بقاعدة البيانات المخفية (RDS) باستخدام الـ Endpoint الخاص بها من داخل خادم الـ EC2، مما يثبت صحة إعدادات الشبكة وقوة جدران الحماية.<img width="1600" height="712" alt="WhatsApp Image 2026-10-07 at 10 51 11 PM" src="https://github.com/user-attachments/assets/fe2e7827-6ac1-4fe7-ae29-c2f3dc945be4" />
