
```
command [options] [arguments]
```

*   **`command`**: คือชื่อคำสั่งหลัก (เช่น `ls`, `cp`, `mv`)
*   **`[options]`**: เป็นตัวเลือก (มักจะขึ้นต้นด้วย `-` หรือ `--`) ที่ปรับเปลี่ยนพฤติกรรมของคำสั่ง
    *   options มักจะมีตัวย่อ (เช่น `-l`) และตัวเต็ม (เช่น `--list`)
    *   บาง options ต้องการค่าเพิ่มเติม (เช่น `-n 5` ใน `head -n 5`)
*   **`[arguments]`**: คือสิ่งที่คำสั่งจะนำไปประมวลผล (เช่น ชื่อไฟล์, ชื่อไดเรกทอรี, ข้อความ)
    *   หลายคำสั่งรับ arguments ได้หลายตัว
    *   ลำดับของ arguments อาจมีความสำคัญ (ขึ้นอยู่กับคำสั่ง)

**ตัวอย่างการใช้ Options และ Arguments**

```bash
ls -l -a -h /home/user/documents
```

*   `command`: `ls`
*   `options`: `-l`, `-a`, `-h`
*   `argument`: `/home/user/documents`

**1. การจัดการไฟล์และไดเรกทอรี (File and Directory Management)**

*   **`ls` (list):**
    *   **วิธีใช้:**
        ```bash
        ls  # แสดงรายการไฟล์และไดเรกทอรีในตำแหน่งปัจจุบัน
        ls /path/to/directory  # แสดงรายการในไดเรกทอรีที่ระบุ
        ls -l /path/to/file  # แสดงรายละเอียดของไฟล์ที่ระบุ
        ls -alh /path/to/directory # แสดงทั้งหมด, ละเอียด, ขนาดอ่านง่าย
        ```
    *   **ตัวอย่าง:**
        ```bash
        ls -l  # ดูรายละเอียดไฟล์ใน directory ปัจจุบัน
        ls -a /tmp  # ดูไฟล์ทั้งหมด (รวม hidden files) ใน /tmp
        ```
*   **`head`**:
    *   **วิธีใช้:**
        ```bash
        head filename  # แสดง 10 บรรทัดแรกของไฟล์
        head -n 20 filename  # แสดง 20 บรรทัดแรก
        head -n -5 filename # แสดงทุกบรรทัด ยกเว้น 5 บรรทัดสุดท้าย.
        ```
*   **`cat` (concatenate):**
    *   **วิธีใช้:**
        ```bash
        cat filename  # แสดงเนื้อหาทั้งหมดของไฟล์
        cat file1.txt file2.txt  # เชื่อมเนื้อหาของสองไฟล์แล้วแสดง
        cat file1.txt file2.txt > combined.txt  # รวมสองไฟล์เป็นไฟล์เดียว
        ```
*   **`echo`**:
    *   **วิธีใช้:**
        ```bash
        echo "Hello, world!"  # แสดงข้อความ
        echo $HOME  # แสดงค่าของ environment variable ชื่อ HOME
        echo "This is a line" >> file.txt  # เพิ่มข้อความต่อท้ายไฟล์
        ```
*   **`tail`**:
    *    **วิธีใช้:**
        ```bash
          tail filename # default 10 บรรทัดสุดท้าย
          tail -f /var/log/syslog # จะคอยตามดูไฟล์ไปเรื่อยๆ
          tail -n 5 file.txt
        ```
*   **`mv` (move):**
    *   **วิธีใช้:**
        ```bash
        mv file1.txt file2.txt  # เปลี่ยนชื่อ file1.txt เป็น file2.txt
        mv file.txt /path/to/new/directory/  # ย้ายไฟล์ไปที่ใหม่
        mv file1.txt file2.txt /path/to/directory/  # ย้ายหลายไฟล์
        ```
*   **`cp` (copy):**
    *   **วิธีใช้:**
        ```bash
        cp file.txt newfile.txt  # คัดลอกไฟล์
        cp -r directory/ newdirectory/  # คัดลอกไดเรกทอรี (recursive)
        cp file1.txt file2.txt /path/to/destination/  # คัดลอกหลายไฟล์
        ```
*   **`rm` (remove):**
    *   **วิธีใช้:**
        ```bash
        rm file.txt  # ลบไฟล์
        rm -r directory/  # ลบไดเรกทอรี (recursive)
        rm -f file.txt  # ลบโดยไม่ถาม (force)
        rm -rf directory/  # ลบไดเรกทอรีโดยไม่ถาม (ระวัง!)
        ```
      * **คำเตือน rm -rf /** ห้ามพิมพ์คำสั่งนี้เด็ดขาด
*   **`pwd` (print working directory):**
    *   **วิธีใช้:**
        ```bash
        pwd  # แสดง path ปัจจุบัน
        ```
*   **`find`**:
    *   **วิธีใช้:**
        ```bash
        find /path/to/search -name "filename.txt"  # หาไฟล์ชื่อนี้
        find / -type d -name "mydir"  # หาไดเรกทอรีชื่อ mydir
        find . -type f -name "*.jpg"  # หาไฟล์ .jpg ใน directory ปัจจุบัน
        find /home -size +10M # หาไฟล์ที่ใหญ่กว่า 10เมก
        ```
*   **`tar` (tape archive):**
    *   **วิธีใช้:**
        ```bash
        tar -xvf archive.tar  # แตกไฟล์ archive.tar
        tar -xvf archive.tar.gz  # แตกไฟล์ .tar.gz
        tar -xvf archive.tar -C /path/to/extract/to/  # แตกไปที่อื่น
        tar -cvf archive.tar file1.txt file2.txt  # สร้าง archive
        tar -czvf archive.tar.gz file1.txt file2.txt  # สร้าง .tar.gz
        ```

**2. การจัดการข้อความ (Text Manipulation)**

*   **`sed` (stream editor):**
    *   **วิธีใช้ (ตัวอย่าง):**
        ```bash
        sed 's/oldtext/newtext/g' file.txt  # แทนที่ข้อความ (s=substitute)
        sed -n '10,20p' file.txt  # แสดงบรรทัดที่ 10-20
        sed '2d' file.txt # ลบบรรทัดที่ 2
        ```
        *   `s/oldtext/newtext/g`:
            *   `s`: คำสั่ง substitute (แทนที่)
            *   `oldtext`: ข้อความเดิมที่ต้องการแทนที่
            *   `newtext`: ข้อความใหม่ที่จะใช้แทนที่
            *   `g`: flag ที่บอกให้แทนที่ทุก occurrences (global) ถ้าไม่ใส่ `g` จะแทนที่แค่ occurrence แรกในแต่ละบรรทัด
*   **`grep` (global regular expression print):**
    *   **วิธีใช้:**
        ```bash
        grep "pattern" file.txt  # หาบรรทัดที่มีคำว่า pattern
        grep -i "pattern" file.txt  # ไม่สนตัวพิมพ์เล็ก/ใหญ่
        grep -r "pattern" directory/  # หาในไดเรกทอรี (recursive)
        grep -l "pattern" *.txt  # แสดงเฉพาะชื่อไฟล์ที่เจอ
        grep -n "pattern" file.txt  # แสดงเลขบรรทัดด้วย
        grep -v "pattern" file.txt # หาบรรทัดที่ไม่มี
        ```

**3. การจัดการ Processes (Process Management)**

*   **`ps` (process status):**
    *   **วิธีใช้:**
        ```bash
        ps  # แสดง processes ของคุณ
        ps aux  # แสดง processes ทั้งหมด
        ps aux | grep "processname"  # หา process ที่มีชื่อ
        ```
*   **`top`:**
    *   **วิธีใช้:**
        ```bash
        top  # แสดง processes แบบ real-time (กด q เพื่อออก)
        ```
*   **`pgrep` (process grep):**
    *   **วิธีใช้:**
        ```bash
        pgrep processname  # หา PID ของ process
        ```

**4. ข้อมูลระบบ (System Information)**

*   **`uname` (unix name):**
    *   **วิธีใช้:**
        ```bash
        uname -a  # แสดงข้อมูลระบบทั้งหมด
        ```
*   **`whoami`:**
    *   **วิธีใช้:**
        ```bash
        whoami  # แสดง username
        ```
*   **`df` (disk free):**
    *   **วิธีใช้:**
        ```bash
        df -h  # แสดงพื้นที่ว่าง (human-readable)
        ```
*   **`lscpu` (list CPU):**
    *   **วิธีใช้:**
        ```bash
        lscpu  # แสดงข้อมูล CPU
        ```
*   **`getent`**:
    *   **วิธีใช้:**
      ```
      getent passwd
      getent group
      ```

**5. การดาวน์โหลด (Downloading)**

*   **`wget` (web get):**
    *   **วิธีใช้:**
        ```bash
        wget https://example.com/file.zip  # ดาวน์โหลดไฟล์
        ```
*   **`curl` (client URL):**
    *   **วิธีใช้:**
        ```bash
        curl https://example.com  # แสดง HTML ของเว็บ
        curl -O https://example.com/file.zip  # ดาวน์โหลดไฟล์
        ```

**6. การจัดการผู้ใช้และกลุ่ม (User and Group Management)**

*   **`sudo` (superuser do):**
    *   **วิธีใช้:**
        ```bash
        sudo command  # รัน command ด้วยสิทธิ์ root
        ```
*   **`adduser`**:
    *   **วิธีใช้:**
        ```bash
        sudo adduser newuser  # สร้าง user ใหม่
        ```
*   **`passwd`**:
    *   **วิธีใช้:**
        ```bash
        passwd  # เปลี่ยนรหัสผ่านตัวเอง
        sudo passwd username  # เปลี่ยนรหัสผ่านของ user อื่น
        ```
*   **`usermod` (user modify):**
    *   **วิธีใช้:**
        ```bash
        sudo usermod -l newlogin oldlogin  # เปลี่ยน login name
        sudo usermod -u 1001 username  # เปลี่ยน user ID
        sudo usermod -g groupname username  # เปลี่ยน primary group
        sudo usermod -a -G group1,group2 username  # เพิ่ม secondary groups
        ```
*   **`userdel` (user delete):**
    *   **วิธีใช้:**
        ```bash
        sudo userdel username  # ลบ user
        sudo userdel -r username  # ลบ user และ home directory
        ```
*   **`groupadd`**:
    *   **วิธีใช้:**
        ```bash
        sudo groupadd newgroup  # สร้าง group ใหม่
        ```
*    **`groupmod`**:
      *   **วิธีใช้:**
        ```
        sudo groupmod -n newgroup oldgroup
        ```
*   **`gpasswd` (group password):**
    *   **วิธีใช้:**
        ```bash
        sudo gpasswd groupname  # ตั้ง/เปลี่ยนรหัสผ่านกลุ่ม
        sudo gpasswd -a username groupname  # เพิ่ม user เข้ากลุ่ม
        sudo gpasswd -d username groupname  # ลบ user ออกจากกลุ่ม
        ```
*   **`deluser`**:
    *   **วิธีใช้:**
        ```bash
        sudo deluser username groupname # ลบออกจากกลุ่ม
        ```
*  **compgen -g**:
    *    **วิธีใช้**:
       ```
       compgen -g
       ```

**7. Permissions (สิทธิ์)**

*   **`chmod` (change mode):**
    *   **วิธีใช้:**
        ```bash
        chmod 755 file.txt  # owner=rwx, group=rx, others=rx
        chmod u+x file.txt  # เพิ่ม execute ให้ owner
        chmod g-w file.txt  # เอา write ออกจาก group
        chmod o=r file.txt  # ให้ others แค่ read
        ```
        *   **สัญลักษณ์:**
            *   `u`: user (owner)
            *   `g`: group
            *   `o`: others
            *   `a`: all (u, g, and o)
            *   `+`: เพิ่มสิทธิ์
            *   `-`: ลดสิทธิ์
            *   `=`: กำหนดสิทธิ์
            *   `r`: read (4)
            *   `w`: write (2)
            *   `x`: execute (1)
*   **`chown` (change owner):**
    *   **วิธีใช้:**
        ```bash
        sudo chown newowner file.txt  # เปลี่ยน owner
        sudo chown :newgroup file.txt  # เปลี่ยน group
        sudo chown newowner:newgroup file.txt  # เปลี่ยนทั้งคู่
        sudo chown -R user:group directory/ # เปลี่ยน owner/group ของทุกอย่างใน directory
        ```

