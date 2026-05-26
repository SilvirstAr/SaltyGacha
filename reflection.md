# Short Reflection - Slaty Gacha Simulator

## ทำจริงเป็นอย่างไร

งานนี้เริ่มจากอ่านโจทย์ให้ครบก่อน แล้วแยก requirements เป็น Must, Advanced และ Bonus เพื่อไม่ให้หลุดส่วนสำคัญ จากนั้นออกแบบเว็บเป็นไฟล์ HTML เดียว ใช้ Vanilla HTML/CSS/JavaScript ทั้งหมด ไม่มี backend ไม่มี build step และฝังภาพพื้นหลังที่ผู้ใช้เลือกไว้ในไฟล์โดยตรง

## จุดที่ทำได้ดี

- Logic สุ่มแยกเป็น 2 ขั้น: สุ่ม rarity ตาม rate ก่อน แล้วค่อยสุ่ม item ใน rarity นั้น
- มี validation ตรวจ rate รวม 100%, ค่าติดลบ, item pool ว่าง และ simulation ที่มากเกินไป
- มี Player POV Monte Carlo เพื่อดูโอกาสจากมุมผู้เล่น เช่น chance ได้ SSR อย่างน้อย 1, chance ได้ 0 SSR, average SSR
- มี Free Roll Rule ที่นับจาก paid rolls เท่านั้น และ free rolls ไม่สร้าง free rolls ซ้ำ
- มี Pity System, History, Chart/Visual และ CSV Export
- UI เป็นธีม fantasy adventure 8-bit พร้อมสกุลเงิน Leaf, ภาพพื้นหลังป่าแฟนตาซี, และตัวละคร original ไม่ใช้ตัวละครจากเกมอื่น

## ติดปัญหาตรงไหน

จุดที่ต้องระวังคือการทำ free roll และ pity ให้ใช้ logic เดียวกันทั้ง Single Simulation และ Player POV ถ้าแยก logic คนละชุดจะมีโอกาสคำนวณไม่ตรงกัน เลยแก้ด้วยการทำ `runRollSequence()` เป็น function กลาง

## AI แนะนำผิดแล้วแก้ยังไง

ระหว่างออกแบบ logic ต้องระวังไม่ให้ free roll สร้าง free roll ซ้ำ เพราะจะทำให้จำนวน roll ผิดจาก requirement จึงแก้เป็นการคำนวณ free rolls จาก paid rolls เท่านั้น:

`freeRolls = floor(paidRolls / paidRollsRequired) * freeRollsGranted`

อีกจุดคือ item pool validation ถ้า rarity มี rate มากกว่า 0 แต่ไม่มี item ระบบจะสุ่มไม่ได้ จึงเพิ่ม validation บังคับก่อนกด simulation

## ข้อจำกัด

ผลลัพธ์เป็น simulation ด้วย `Math.random()` จึงมีความแปรผันตามจำนวนรอบ ยิ่งจำนวน roll หรือ simulation runs มาก ผลเฉลี่ยจะเข้าใกล้ rate ที่ตั้งไว้มากขึ้น แต่ยังไม่ใช่การการันตีผลเฉพาะรายบุคคล

## สิ่งที่เรียนรู้

การใช้ AI ให้ดีไม่ใช่แค่ให้เขียนโค้ด แต่ต้องใช้ช่วยแยก requirement, ตรวจ edge case, อธิบาย logic และทำ validation ให้ตรวจสอบได้ งานนี้จึงเน้นทั้งความถูกต้องของ simulation และการสื่อสารผลลัพธ์ให้คนทั่วไปเข้าใจ
