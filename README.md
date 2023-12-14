<img src="img/Start_With_Git.png"/>

1 hours tutorial Git for Beginner 
by [LemonMints42BKK][lemonGit]

>Git คือ โปรแกรมระบบจัดการเวอร์ชั่นของเอกสารในสารบบ กล่าวง่ายๆคือ ตอบสนองความต้องการของโปรแกรมเมอร์ ในการปรับปรุง เปลี่ยนแปลงโปรแกรม
>โดยสามารถย้อนกลับไปเว่อร์ชั่นต่างๆได้โดยไม่สับสน ต่างจากการเซฟไฟล์หลายก็อปปี้ เพราะการทำเช่นนั้นเราไม่ได้ติดตามการแก้ไขก่อน-หลังและรายละเอียดของการเปลี่ยนแปลง
>ทำให้ไม่สามารถระบุได้ว่าก็อปปี้ไหนถูกแก้ไขล่าสุดและแก้ไขส่วนใดบ้าง  อีกทั้ง git ยังช่วยให้ทีมโปรแกรมเมอร์สามารถทำงานร่วมกัน สามารแตก brance เพื่อพัฒนาต่อ และนำกลับมาร่วมกับต้นฉบับได้อย่างเหมาะสม

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
