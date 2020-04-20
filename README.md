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

MIPS Instruction Format จะแบ่งเป็น 3 แบบ

1.R-Format ใช้ในการคำนวณ

|op 6bits |rs 5bits|rt 5bits|rd 5bits|shamt 5bits|func 6bits|

2.I-Format ใช้ในการย้ายข้อมูล

|op 6bits|rs 5bits|rt 5bits|offset 16bits|

3.J-Format การย้ายไปทำงานที่ตำแหน่งอื่น

|op 6bits|address 26 bits|

Ex. j 0x81fc084c

1.เปลี่ยน81fc084cที่เป็นเลขฐาน16ให้เป็นเลขฐาน2 >>> 1000 0001 1111 1100 0000 1000 0100 1100

2.นำbitที่5ถึง32 มาshiftingจากนั้นนำไปต่อกับopcode (j:000010)

3.จะได้เลขฐาน2 3 bits คือ 0000 1000 0111 1111 0000 0010 0001 0011

4.เเปลงจากฐาน2กลับมาเป็นฐาน16 จะได้เลข087f0213 ตัวเลขนี้คือตำแหน่งที่จะjumpไปทำงานคำสั่งต่อไป


**ส่งการบ้านครั้งที่1**


[งานครั้งที่1](https://www.youtube.com/watch?v=wY9R6XCizwM&t=1s)

อธิบายคำสั่ง jump ใน cpu MIPS

**ส่งการบ้านครั้งที่2**

[งานครั้งที่2](https://www.youtube.com/watch?v=8CIgbwNDo-g&t=8s)

อธิบายการทำงานของระบบคอมพิวเตอร์

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
