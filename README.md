# รายวิชา CN210

## สรุปเนื้อหาวิชา

สรุปเนื้อหาวิชา

Computerนั้นจะประกอบไปด้วย

        1.หน่วยประมวลผลกลางหรือCPU(Central Processing Unit)

        2.main memory

        3.Input/Output

โดยในCPUนั้นจะประกอบไปด้วย

        1.ALU(Artimetric and logic unit) ใช้ในการคำนวณและหาตรรกะทางคณิตศาสตร์

        2.Register

        3.Control Unit

โดนรายวิชาCN210 ได้เลือกCPU MIPSมาศีกษา

ทุกคำสั่งของ MIPS จะมีขนาด 32 bits

MIPS Instruction Format จะแบ่งเป็น 3 แบบ

        1.R-Format ใช้ในการคำนวณ

        2.I-Format ใช้ในการย้ายข้อมูล

        3.J-Format การย้ายไปทำงานที่ตำแหน่งอื่น

![image](https://www.researchgate.net/profile/Flavio_Padua/publication/269463299/figure/fig1/AS:392119614230533@1470500009360/The-MIPS-instruction-format.png)



**ส่งการบ้านครั้งที่1**

[งานครั้งที่1](https://www.youtube.com/watch?v=wY9R6XCizwM&t=1s)

อธิบายคำสั่ง jump ใน cpu MIPS

        Ex. j 0x81fc084c

        1.เปลี่ยน81fc084cที่เป็นเลขฐาน16ให้เป็นเลขฐาน2 >>> 1000 0001 1111 1100 0000 1000 0100 1100

        2.นำbitที่5ถึง32 มาshiftingจากนั้นนำไปต่อกับopcode (j:000010)
        
        3.จะได้เลขฐาน2 3 bits คือ 0000 1000 0111 1111 0000 0010 0001 0011

        4.เเปลงจากฐาน2กลับมาเป็นฐาน16 จะได้เลข087f0213 ตัวเลขนี้คือตำแหน่งที่จะjumpไปทำงานคำสั่งต่อไป


**ส่งการบ้านครั้งที่2**

[งานครั้งที่2](https://www.youtube.com/watch?v=8CIgbwNDo-g&t=8s)

อธิบายการทำงานของระบบคอมพิวเตอร์

คำสั่งที่มนุษย์ป้อนให้คอมพิวเตอร์

        class Test { 

                public static void main(String[] args){

                         int a = 10;
    
                         int b = 20;
    
                         int c = a+b;
                 }
        }

=== Machine Language ===

    00000000:           08400000        //jumpไปที่ address  01000000 
    
    00000004:           1A000000        //data
    
     ...

    01000000:           8C090004        //lw $9,$0(4) ดึงข้อมูลจากaddressของregisterที่0 + 4 นำไปเก็บไว้ที่registerที่9
    
     01000004:           8D210000       //lw $1,$9(0) ดึงข้อมูลจากaddressของregisterที่9 + 0 นำไปเก็บไว้ที่registerที่1

    01000008:           8D220004       //lw $2,$9(4)  ดึงข้อมูลจากaddressของregisterที่9 + 4 นำไปเก็บไว้ที่registerที่2

    0100000C:           00221820        //add $3,$1,$2 register3 = register1 + register2

    01000010:           AD230008        //sw $9,$0(4)  นำข้อมูลจากaddressของregisterที่9 นำไปเก็บไว้ที่registerที่0 + 4 

    ...

    1A000000:           0000000A        //a = 10

    1A000004:           00000014        //b = 20

    1A000008:           0000001E        //c = 30

**ส่งการบ้านครั้งที่3**

[งานครั้งที่3](https://www.youtube.com/watch?v=0poRS1BtJsE)

ความแตกต่างระหว่างsingle-clock-cycleกับmulti-clock-cycle

ลักษณะของ Single Cycle 
        
        มี ALU 3 ตัว   
        
        มี Memory 2 ตัว 
       
        1 คำสั่ง = 1 Cycle  
        
        ในทุกๆคำสั่งใช้เวลาเท่ากันทำให้ใช้เวลามากเนื่องจากจะใช้เวลาของคำสั่งที่ทำงานใช้เวลามากสุด

![image](https://cseweb.ucsd.edu/~j2lau/cs141/single_cycle_cpu_datapath.png)

ลักษณะของ Multi Cycle มีดังนี้

        มี ALU เพียงตัวเดียว
        
        มี Memory เพียงตัวเดียว
        
        มีการพักข้อมูลที่ตำแหน่ง a และ b ในรูป
        
        ใช้เวลาแต่ละคำสั่งไม่เท่ากัน
        
        มี ALUout ที่เก็บค่าหลังจากคำนวณ

![image](https://cseweb.ucsd.edu/~j2lau/cs141/multi_cycle_cpu_datapath.png)

**ส่งการบ้านครั้งที่4**

[งานครั้งที่4](https://www.youtube.com/watch?v=yYKce5W6ZwY)

อธิบายคำสั่งlw ในmulti-clock-cycle

        คำสั่ง lw ใน Multi Cycle นั้นมีทั้งหมด 5 ขั้นตอน
        
        1.อ่านคำสั่งจาก Memory มาเก็บใน IR (Instruction Register) และนำ PC = PC + 4 พร้อมๆกัน
        
        2.นำ ค่าจาก $rs และ $rt ไปเก็บไว้ที่ A,B ตามลำดับ นำค่า offset มาแปลงเป็น 32 บิท
          แล้วนำไปที่ ALU เพื่อบวกกับ PC แล้วนำไปเก็บที่ ALUout (A = Reg[IR[25-21]]) (B = Reg[IR[20-16]])
       
        3.นำค่า จาก A เข้ามาบวกกับ offset และนำค่าไปไว้ที่ ALUout (ALUOut = A + sign-extend(IR[15-0])
        
        4.ค่าที่ได้จาก ALUout คือ ค่าของ Address ของ Memory ที่จะถูกอ่านค่าออกมา (MDR = Memory[ALUout])
        
        5.นำค่าที่อ่านมาจาก Memory ไปเก็บไว้ใน $rt (Reg[IR[20-16]] = MDR)

**ส่งการบ้านครั้งที่5**

[งานครั้งที่5](https://www.youtube.com/watch?v=s8lwbWAGc94)

อธิบายคำสั่งbeq ในmulti-clock-cycle
        
        beq (branch on equal) เป็นคำสั่งประเภท I-Format ซึ่งคำสั่งนี้มีหน้าที่ JUMP โดยจะ JUMP อย่างมีเงื่อนไข 
        
        คือการดูว่าข้อมูลที่ $rs และ $rt เท่ากันหรือไม่ หากเท่ากันให้ JUMP ไปยังตำแหน่ง Address ต่อไป 
        
        มี 3 ขั้นตอน
        
        1.อ่านคำสั่งจาก Memory มาเก็บใน IR (Instruction Register) และนำ PC = PC + 4 พร้อมๆกัน
        
        2.นำค่า $rs และ $rt ไปเก็บไว้ที่ A,B ตามลำดับ (A = Reg[IR[25-21]]) (B = Reg[IR[20-16]])
       
        3.นำค่าจาก A และ B มาเปรียบเทียบกัน หากเท่ากันจะเก็บผลลัพธ์ที่ได้ไว้ใน ALUout แล้ว JUMP ไปยัง Address ต่อไป 
        
          หากไม่เท่ากันจะข้ามไปทำคำสั่งถัดไปทันที

**ส่งการบ้านครั้งที่6**

[งานครั้งที่6](https://www.youtube.com/watch?v=rXHOVZxnRus&t=13s)

อธิบายสัญญาณที่ใช้ควบคุมใน R-format

ประกอบด้วย 4 ขั้นตอน

![image](https://image1.slideserve.com/3211244/slide21-n.jpg)

        MemRead = 1 คือ ทำการอ่านค่าจาก Memory
        IorD = 1 คือ เช็คว่า PC นั้นชี้ไปที่ Address ใดใน Memory
        IRWrite = 1 คือ นำค่าจาก Address Memory ที่ถูกชี้ ไปเก็บไว้ใน IR
        ALUSrcA = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ PC ค่าที่ถูกเขียนใน IR จะมี ALUSrcA ทำการควบคุม
        ALUSrcB = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ 4 ค่าที่ถูกเขียนใน IR จะมี ALUSrcB ทำการควบคุม
        ALUOP = ADD คือ การนำค่า PC มาบวกกับ 4
        PCWrite = 1, PCSource = 1 นำผลลัพธ์การคำนวณเขียนทับที่ PC = PC + 4
        
![image](https://image1.slideserve.com/3211244/slide23-n.jpg)
       
        ALUSrcA = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ PC
        ALUSrcB = 3 คือ Mux เลือกค่าจาก 3 ซึ่งคือ Offset
        ALUop = 0 คือ ALUop จะทำการควบคุมคำสั่ง ADD
        
![image](https://image1.slideserve.com/3211244/slide25-n.jpg)

        ALUSrcA = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ $rs
        ALUSrcB = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ $rt
        ALUop = 2 คือ ALUop จะทำการควบคุมคำสั่งให้เป็นไปตามคำสั่งใน IR
 
![image](https://image1.slideserve.com/3211244/slide27-n.jpg)

        RegWrite = 1 คือ นำค่าจาก ALUout มาเขียนใน $rd
        MemtoReg = 0 คือ Mux เลือกค่าจาก 0 ซึ่งคือ ALUout
        RegDst = 1 คือ Mux เลือกค่าจาก 1 ซึ่งคือ $rd
        
**ส่งการบ้านครั้งที่7**

[งานครั้งที่7](https://www.youtube.com/watch?v=9rQ11iQQkxk)

อธิบายการทำงานของ Pipelining 

Pipelining เป็นวิธีการทำคำสั่งที่ช่วยให้ทำไวขึ้น หลักๆคือ 1 คำสั่ง จบในหลายๆ Cycle ถึงแม้ว่าจะทำคำสั่งแรกยังไม่เสร็จแต่สามารถนำคำสั่งถัดไปมาทำงานต่อได้เลย

โดยตัวอย่างเราจะแบ่งการทำงาน 1 set มี 4 ขั้นตอน ขั้นตอนละ 30นาที

![image](http://3.bp.blogspot.com/-6RQaYhlYk2k/UKTYQVX9csI/AAAAAAAAAGQ/0xF1OxF_N_Y/s1600/02-What-is-pipelining-01.png)

        จากตัวอย่าง การทำงาน 1 set ใช้เวลา 2ชั่วโมง เมื่อจบsetที่ 1 จึงเริ่มทำงาน set ที่ 2 
        
        ทำให้การทำงานทั้งหมด 4 set ใช้เวลาทั้งสิ้น 8 ชั่วโมง

![image](http://2.bp.blogspot.com/-4YXOlZ30iCQ/UKTYR4Y4FLI/AAAAAAAAAGk/pCdSkaaazVA/s1600/02-What-is-pipelining-02.png)

        จากตัวอย่าง  การทำงาน 1 set ใช้เวลา 2ชั่วโมง แต่เมื่อเราทำขั้นตอนที่ 2 ของsetที่1 เราเริ่มทำงานจะทำงานขั้นตอนที่1 ของsetที่ 2

        เมื่อเราทำขั้นตอนที่ 3 ของsetที่1 เราเริ่มทำงานจะทำงานขั้นตอนที่1 ของsetที่ 3

        เมื่อเราทำขั้นตอนที่ 4 ของsetที่1 เราเริ่มทำงานจะทำงานขั้นตอนที่1 ของsetที่ 4

        ทำให้การทำงานทั้งหมด 4 set ใช้เวลาทั้งสิ้น 3 ชั่วโมง 30 นาที

