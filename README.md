<img src="img/Start_With_Git.png"/>

1 hours tutorial Git for Beginner 
by [LemonMints42BKK][lemonGit]

>Git คือ โปรแกรมระบบจัดการเวอร์ชั่นของเอกสารในสารบบ กล่าวง่ายๆคือ ตอบสนองความต้องการของโปรแกรมเมอร์ ในการปรับปรุง เปลี่ยนแปลงโปรแกรม
>โดยสามารถย้อนกลับไปเว่อร์ชั่นต่างๆได้โดยไม่สับสน ต่างจากการเซฟไฟล์หลายก็อปปี้ เพราะการทำเช่นนั้นเราไม่ได้ติดตามการแก้ไขก่อน-หลังและรายละเอียดของการเปลี่ยนแปลง
>ทำให้ไม่สามารถระบุได้ว่าก็อปปี้ไหนถูกแก้ไขล่าสุดและแก้ไขส่วนใดบ้าง  อีกทั้ง git ยังช่วยให้ทีมโปรแกรมเมอร์สามารถทำงานร่วมกัน สามารแตก brance เพื่อพัฒนาต่อ และนำกลับมาร่วมกับต้นฉบับได้อย่างเหมาะสม

[การเปิดบัญชีบน git host][]
[เชื่อมต่อ Remote repo กับ Local repo][]
[4 ขั้นตอนการ commit# (ปรับปรุงเวอร์ชั่น)][]
[การแตกเวอร์ชั่น (branch)][]
[การรวมเวอร์ชั่น (Merge branch)][]

ความรู้พื้นฐานก่อนเริ่มใช้งาน
- Files system
- Terminal หรือ Command Line Interface (CLI)
- Git Application: Git Kraken, Github Desktop etc.
- Code Editor: VScode etc.
- Remote Repository และ Local Repository
  
### Host Repository Online: ผู้ให้บริการฝากสารบบออนไลน์

<a href="https://github.com"><img alt="GitHub Logo in Light or Dark." src="https://github.githubassets.com/assets/GitHub-Mark-ea2971cee799.png" width="50vw" hight="50vh"></a>
 <a href="https://gitlab.com"><img src="https://user-images.githubusercontent.com/40824677/205691219-5698063c-44bf-453a-b4df-365654641979.png"/></a>

- สมัครใช้งาน git โดยเลือก ผู้ให้บริการ [GitHub][github] หรือ [GitLab][gitlab] หรือผู้ให้บริการอื่นๆ
- สร้าง Repository ในบัญชีของเรา ต่อไปนี้จะเรียกสั้นสั้นว่า repo
- เราสามารถสร้างหนึ่ง repo ต่อหนึ่งโปรเจค หรือหนึ่งทีม แล้วแต่เรา ในหนึ่งบัญชีสามารถสร้างได้หลาย repo
- แต่ละคนในทีมควรมีบัญชีเป็นของตัวเอง เราสามารถไปร่วมงานใน repo ของเพื่อน แตก fork branch มาทำในบัญชีตัว และอื่นๆได้ โดยเนื้อหายังไม่มีในเอกสารนี้
- หลังจากสร้าง remote repo(ออนไลน์) จึงทำการติดตั้ง local repo (เครื่องคอมพิวเตอร์) โดยทำได้ 2 วิธี
  1) การสร้าง remote repo แล้วจึงนำมาสร้าง local repo ในเครื่อง 
  2) การนำโฟลเดอร์ในเครื่อง มาสร้างเป็น local repo แล้วเชื่อมต่อกับ remote repo

คำสั่งพื้นฐานการใช้งาน git ในเอกสารนี้ สามารถใช้งานได้เหมือนกันในทุกผู้ให้บริการฝากสารบบ
- เลือกหนึ่งในสองวิธี ขั้นต้น ทำตามลำดับดังนี้
  1) เปิด terminal ในเครื่อง ไปยังไดเรคทอรี่ที่ต้องการวาง local repo
     ```
     git clone {git@github...} {repo-name}
     ```
     แทนค่า {git@github...} ด้วยลิงค์ที่ได้จาก remote repo ที่สร้างขึ้น
     {repo-name} คือชื่อโฟลเดอร์ที่ต้องการเปลี่ยน **ไม่ต้องใส่หากอยากให้ชื่อโฟลเดอร์ใน local และ remote เหมือนกัน
     ```
     cd {repo-name}
     ls -la
     ```
     จะเข้าไปในโฟลเดอร์ของ local repo จะเห็นไฟลเดอร์ .git แสดงว่า repo ถูกติดดั้งเรียบร้อยแล้ว
  
  2) เปิด terminal ในเครื่อง สร้างโฟลเดอร์ หรือเลือกโฟลเดอร์ในเครื่องที่ต้องการสร้างเป็น local repo
     ```
     mkdir {repo-name}
     ```
     ในกรณีที่ต้องการสร้างโฟลเดอร์ใหม่
     ```
     cd {repo-name}
     ls -la
     ```
     เข้าไปในโฟล์เดอร์ จะเห็นว่ายังไม่มีโฟลเดอร์ .git อยู่ภายใน
     ```
     git init
     ls -la
     ```
     จะเห็นว่ายังมีโฟลเดอร์ .git อยู่ภายในแล้ว **ยกเว้นเครื่องระบบ window ที่ยังไม่เคยลงโปรแกรมgit ให้ไปที่นี้ [git] แล้วลงคำสั่งนี้อีกครั้ง
     แต่ local repo นี้จะยังไม่เชื่อมต่อกัน remote repo จึงต้องลงชุดคำสั่งต่อไปนี้
     ```
     git commit -m "First commit"
     git remote add origin {git@github...}
     git push -u origin master
     ```
     แทนค่า {git@github...} ด้วยลิงค์ที่ได้จาก remote repo ที่สร้างขึ้น
     **หลังจากเชื่อต่อกันแล้ว ยังมีปัญหาอีกว่าบน remote repo มีการแตกออกเป็น 2 คือ main branch และ master branch จำเป็นต้องย้ายมาร่วมกันและลบให้เหลือแค่ main
     ***ดังนั้นวิธีที่สองนี้ไม่แนะนำสำหรับผู้เรื่มใช้งานใหม่ หากมีโฟลเดอร์งานอยู่แล้วก็สามารถใช้วิธีแรก แล้วย้ายงานมาไว้ในโฟลเดอร์ของ local repo แทนจะดีกว่า

- ทำการปรับปรุง เพื่มหรือลบไฟล์ ใน local repo
- ทำการ commit# เทียบได้กับการ save point ในเกม เมื่อเราเล่นเกมไปถึงด่านหนึ่ง หากไปต่อแล้วแพ้ก็สามารถกลับมาเริ่มต้นที่จุดเดิมได้

  มีด้วยกัน 3-4 ขั้นตอน
    1) Add เพื่อ track file
    2) Commit เพื่อ save track ใน local repo
    3) Push เพื่อ update สถานะที่ commit ใน remote repo
    4) Merge *หาก local repo ไม่ใช่เจ้าของ remote repo ต้องมีการจัดการที่เรียกว่า pull request

  ```
  git status
  ```
  ดูสถานะไฟล์ที่ถูกเปลี่ยนแปลงใน local repo สถานะสีแดงคือ untrack สถานะสีเขียวคือ ได้รับการ trackแล้ว เมื่อมีสถานะสีแดงให้ใข้คำสั่ง
  ```
  git add .
  ```
  track ไฟล์ทั้งหมดให้เป็นสถานะสีเขียว
  ```
  git add {filename}
  ```
  ระบุเฉพาะ {filename} ที่ต้องการเปลี่ยนสถานะจาก untrack(แดง) -> track(เขียว)
  ```
  git reset HEAD {filename}
  ```
  ระบุเฉพาะ {filename} ที่ต้องการเปลี่ยนสถานะจาก track(เขียว) -> untrack(แดง)
  ```
  git commit -m "..."
  ```
  "..." รายละเอียดคร่าวๆเกี่ยวกับการเปลี่ยนแปลง เพื่มหรือลดชุดคำสั่งในโปรเจค หรือจุดประสงค์ในการแก้ไข
  ```
  git push
  ```
  อาจถูกปฎิเสธการ push หากเครื่อง local repo ยังไม่ได้พิสูจน์สิทธิ์การเข้าถึงด้วยการบันทึก ssh public key บน git Host
  
     
### How To Create Beautiful and Useful ReadMe Documents For GitHub :ตกแต่งเอกสารประกอบสารบบให้สวยงามและเกิดประโยชน์
README.md นอกจากจะสามารถเขียนเป็นคู่มือการใช้งานโปรแกรม และแหล่งข้อมูลสำคัญแล้ว การออกแบบให้สวยงามยังช่วยสร้างความน่าสนใจให้กับโค้ชของเราด้วย
YouTube:  <a href="https://www.youtube.com/watch?v=a8CwpGARAsQ">@thegitguild</a>

Helpful Resources:
- Awesome ReadMe: https://github.com/matiassingers/awes...
- Banner Maker: https://banner.godori.dev
- Shields.io: http://shields.io
- Carbon: https://carbon.now.sh

Cheat Sheets:
- Markdown Guide: https://www.markdownguide.org/cheat-s...
- Markdown Cheatsheet: https://guides.github.com/pdfs/markdo...

Markdown Editors:
- Dillinger.io: https://dillinger.io
- Editor.md: https://pandao.github.io/editor.md/en...
- Make A Readme: https://www.makeareadme.com

Mentioned Projects:
- Joe: https://github.com/karan/joe
- Stronghold: https://github.com/alichtman/stronghold
- Markdownify: https://github.com/amitmerchant1990/e...
- Clairvoyant: https://github.com/anfederico/clairvo...
- Colorls: https://github.com/athityakumar/colorls

[//]: # (ส่วนการระบุค่าตัวแปร ซึ่งไม่แสดงในเอกสาร)
[lemonGit]: <https://github.com/LemonMints42BKK>
[github]: <https://github.com>
[gitlab]: <https://gitlab.com>
