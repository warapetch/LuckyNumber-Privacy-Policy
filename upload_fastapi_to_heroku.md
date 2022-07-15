
# การนำไฟล์ FastAPI ขึ้นไปรันบน HeroKu
## Python #FastAPI #SQLite #HeroKu @Linux
project :: heroku-fastapi-luckynumbers<BR>
date :: 15/07/2565  (15/07/2022)

![image](https://user-images.githubusercontent.com/6521378/179192519-93959cc1-dd66-4240-94b3-33c135b030f3.png)


การนำไฟล์ FastAPI ขึ้น HeroKu<BR>
โปรแกรมเจคนี้ คือ พัฒนา FastAPI (Python) + SQLite<BR>
เพื่อทำให้ Http เป็น Https<BR>

---
![image](https://user-images.githubusercontent.com/6521378/179192640-bf6a0200-a17e-4d4d-8de0-8a49ba91339e.png)

หลังจากที่พัฒนา FastAPI สำเร็จ สามารถทำงานได้แล้ว
ก็ถึงเวลานำขึ้น HeroKu <BR>
ขั้นตอน
1. สร้าง ACCOUNT  HeroKu FREE ฟรีครับ
[คลิ๊ก >ไปเวบไซต์ HeroKu ](https://www.heroku.com)
<BR>

2. ติดตั้ง HeroKu CLI<BR>
เป็นโปรแกรม Bash command สำหรับ ติดต่อกับ HeroKu<BR>
** ถ้าไม่ถนัด ก็ใช้ GitHUB ดีกว่า สะดวกกว่า<BR>
เวลาอัพเดตโค้ด ง่ายกว่าเยอะ
<BR>

3. เริ่มทำตามขั้นตอน
โดยใช้ HeroKu CLI

3.1 login
	>$ heroku login

<BR>

3.2 download ต้นแบบ/ตัวอย่าง<BR>
	ไปโฟลเดอร์ที่ต้องการเก็บโค้ด<BR>
<BR>	

	> $ git clone https://github.com/heroku/python-getting-started.git
	> $ cd python-getting-started
<BR>

	> ถ้าเรามีโค้ดแล้ว และเก่งโปรแกรม GIT ก็สามารถ พิมพ์เองได้เลย
	** ทำตอนข้อ 6 **
	$ cd {my-project}/
	$ git init
	$ heroku git:remote -a {my-app}
	$ git push heroku main
	-- * ต้องสร้าง App ก่อน * --

<BR>

3.3 create app (Web Server)<BR>
	> $ heroku create
	
	> Creating app... done, 
	> {my-app}
	> https://{my-app}.herokuapp.com/ | 
	 	  https://git.heroku.com/{my-app}.git

<BR>
3.4 Upload 
	
	** กอปโค้ดของเรา ไปทับ 
	ในโฟลเดอร์  python-getting-started
	จากนั้น
	>> git push heroku main
	
<BR>
3.5 Run Server

	>> heroku ps:scale web=1
	>> Scaling dynos... done, now running web at 1:Free
<BR>
3.6 เริ่มใช้งาน  เปิดเวบ

	> heroku open	

<BR>

## อัพเดต + มีการแก้ไขโค้ด ผ่าน Github สะดวกง่าย<BR>
สามารถ Manual Deploy ได้ (ห้ามทำถี่เกินไป จะถูกบล็อคระยะเวลาหนึ่ง)	<BR>
![image](https://user-images.githubusercontent.com/6521378/179193097-8415c68e-7030-4468-a959-845a97bde7ec.png)


** ทำไม มันง่ายจัง **
## กว่าจะทำได้ หมดไปครึ่งวัน !!
## ข้อควรระวัง
1. ไฟล์ที่จำเป็นของการ รัน Python

1.1  requirements.txt
ใส่แพ็กเกจมาให้ครบ เอาไว้ในไฟล์นี้
อย่าลืม Gunicorn ตัวรัน Python และ FastAPI
		
	> gunicorn==20.1.0
<BR>
1.2 .env
ถ้ามีการกำหนด config ไว้ในไฟล์ .env นำขึ้นไปด้วย

	> ข้อควรระวัง ห้ามพลาด (ผมพลาดไปแล้ว) คือ
	> ไฟล์ .gitignore เอาไฟล์ .env ออกด้วย

<BR>
1.3 ไฟล์ฐานข้อมูล SQLite  *.db / *.sqlite3

	> ข้อควรระวัง ห้ามพลาด (ผมพลาดไปแล้ว) คือ
	> ไฟล์ .gitignore เอาไฟล์ .db / *.sqlite3 ออกด้วย
<BR>
1.4 คำสั่งในการรันระบบ
Procfile (ไม่มีนามสกุล)
พิมพ์คำสั่ง gunicorn  ตามด้วย พารามิเตอร์ <BR>
ตรวจสอบด้วยว่า HeroKu รองรับไหม

	> web: gunicorn -k uvicorn.workers.UvicornWorker main:app
<BR>
2. เมื่อ Upload ไป HeroKu ระบบจะทำการ รันและติดตั้งแพ็กเกจที่จำเป็น<BR>
ให้ตรวจสอบปัญหาจาก Log

	> ถ้าเซิฟเรารันไม่ได้ ให้อ่านจาก Log แก้ปัญหาตามที่ Log แจ้งไว้
ให้ ตั้งค่าใช้ Buildpacks เป็น แพ็กเกจ heroku/python ด้วย	
App >> Settings >> Buildpacks 
ถ้าไม่มีแพ็กเกจใดๆ ให้กดปุ่ม Add Buildpacks

![image](https://user-images.githubusercontent.com/6521378/179191996-b30235c0-6f31-4719-aa97-053b4ddcfad8.png)

<BR>
เวบข้อมูลการอัพโหลด <BR>
https://www.tutlinks.com/create-and-deploy-fastapi-app-to-heroku/

หวังว่าข้อมูลนี้ จะมีประโยชน์ กับผู้ที่สนใจ <BR>
วรเพชร  เรืองพรวิสุทธิ์<BR>
15/07/2565
