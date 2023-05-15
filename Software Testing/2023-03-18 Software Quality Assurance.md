
พี่วิว (ธ.กรุงไทย) - manual QA - test case
(เงินติดล้อ) - rebot framework

# Software Quality Assurance

## Manual Test
พี่วิว

- dev
	- unit test (module)
- tester
	- functional testing - ดูว่า func ทำตาม bussiness
	- system integration test
	- End to end testing
	- --- UAT
	- Sanity testing - test ตอน deploy v ใหม่ เป็นจุดย่อยๆ
	- Regression testing - เทสการทำงานระบบใหม่ ทำงานร่วมกันสมบูรณ์
	- Beta testing / Pilot testing - เทสบน prod ใช้ข้อมูลจริงของ user ก่อนส่งงาน
- user
	- UAT ดูความพึงพอใจ ตรง business req

### Defect Tracking


### TCM - Test Coverage Matrix

- Test - การทดสอบ
- Coverage - ความครอบคลุม
- Matrix - ตาราง

8 main 
1. Strory No.
2. Test Scenario (TS ID)
3. .
4. .
5. .
6. condition ก่อนทำ testcase นั้น
7. .
8. .
Additional
1. Channel - mobile, tablet
2. Device - iOS, and
3. . - ภาษาที่ใช้ในแอพ ภาษาของผู้ใช้ eng, th
4. .
5. .

#### Test Case
แตกออกมาจาก TCM เป็นขยายความ

1 - 18 headers

ดู ตย. ใน excel `R1_SP23_KMITLSHOP1001_TCM_SIT_V1.0`

### Defect
ใน Jira - ดู req (user story), track งาน, sprint board, defect
การเปิด defect - description บอกให้ละเอียด (ให้ dev ไม่ต้องมาถาม, +รูป, วิดีโอ ยิ่งดี) มี test data (ที่ทำให้เกิด defect)

### ac เขียน TCM
เป็น UI Test (cost เยอะสุด) สนใจที่ user จะเห็นอะไร
เขียนตาม user story เขียนออกมาทั้งหมดที่ทำได้ในหน้านั้นๆ

---

## Robot framwork


