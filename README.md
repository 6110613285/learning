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

**ส่งการบ้านครั้งที่4**

[งานครั้งที่4](https://www.youtube.com/watch?v=yYKce5W6ZwY)

อธิบายคำสั่งlw ในmulti-clock-cycle

**ส่งการบ้านครั้งที่5**

[งานครั้งที่5](https://www.youtube.com/watch?v=s8lwbWAGc94)

อธิบานคำสั่งbeq ในmulti-clock-cycle

**ส่งการบ้านครั้งที่6**

[งานครั้งที่6](https://www.youtube.com/watch?v=rXHOVZxnRus&t=13s)

อธิบายสัญญาณที่ใช้ควบคุมใน R-format
