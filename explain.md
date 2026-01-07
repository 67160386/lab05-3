# การอธิบายการทำงาน JavaScript

เป็นการอธิบายขั้นตอนการทำงานและแสดงผลลัพธ์ของโค้ดในแต่ละไฟล์

# 2.1 ไฟล์ 01-variables.js

## 📘 6. Challenge: Create a Person Object

### 📝 โค้ด

```javascript
// ─────────────────────────────────
// 6. Challenge: Create a Person Object
// ─────────────────────────────────
console.log("\n=== Challenge: Person Object ===");
const student = {
  firstName: "Alice",
  lastName: "Smith",
  age: 20,
  gpa: 3.8,
  courses: ["HTML", "CSS", "JavaScript"],
  isActive: true,
  // Method (function in object)
  getFullName: function () {
    return `${this.firstName} ${this.lastName}`;
  },
  getInfo: function () {
    return `${this.getFullName()}, Age: ${this.age}, GPA: ${this.gpa}`;
  },
};
console.log("Student object:");
console.log(student);
console.log("Full name:", student.getFullName());
console.log("Info:", student.getInfo());
console.log("Courses:", student.courses.join(", "));
```

### 🛠️ ส่วนประกอบของโค้ด

- **Properties**: เก็บข้อมูลนักศึกษา (ชื่อ, อายุ, GPA, วิชาที่เรียน, สถานะ)
- **Methods**:
  - `getFullName()`: รวมชื่อ-นามสกุล
  - `getInfo()`: สรุปข้อมูล ชื่อ, อายุ และ GPA
- **Key Logic**: ใช้ `this` เพื่อดึงข้อมูลภายในตัวมันเอง และใช้ `.join()` จัดรูปแบบ Array

---

### 🚀 ขั้นตอนการทำงาน

1. **สร้าง Object**: กำหนดค่าเริ่มต้นให้ตัวแปร `student`
2. **เรียกใช้ Method**: ประมวลผลชื่อและข้อมูลผ่านฟังก์ชันภายใน
3. **แสดงผล**: พิมพ์ค่าทั้งหมดออกทาง Console โดยจัดรูปแบบวิชาเรียนให้เป็นข้อความที่อ่านง่าย

---

### 🖥️ ผลลัพธ์ (Output)

```
=== Challenge: Person Object ===
Student object:
{
  firstName: 'Alice',
  lastName: 'Smith',
  age: 20,
  gpa: 3.8,
  courses: [ 'HTML', 'CSS', 'JavaScript' ],
  isActive: true,
  getFullName: [Function: getFullName],
  getInfo: [Function: getInfo]
}
Full name: Alice Smith
Info: Alice Smith, Age: 20, GPA: 3.8
Courses: HTML, CSS, JavaScript
```

# 2.2 ไฟล์ 02-functions.js

## 📘 8. Returning Objects

### 📝 โค้ด

```javascript
// ─────────────────────────────────
// 8. Returning Objects
// ─────────────────────────────────
function createUser(firstName, lastName, age) {
  return {
    firstName, // shorthand for firstName: firstName -- สําคัญมาก
    lastName,
    age,
    email: `${firstName.toLowerCase()}.${lastName.toLowerCase()}@example.com`,
    getFullName() {
      // shorthand for getFullName: function() {}
      return `${this.firstName} ${this.lastName}`;
    },
    getAge() {
      return this.age;
    },
  };
}
console.log("\nReturning Objects:");
const newUser = createUser("John", "Doe", 30);
console.log(newUser);
console.log("Email:", newUser.email);
console.log("Full name:", newUser.getFullName());
```

### 🛠️ ความสามารถของโค้ด

- **Property Shorthand**: ลดรูปการเขียน `firstName: firstName` เหลือเพียง `firstName` (เมื่อชื่อตัวแปรและ Key เหมือนกัน)
- **Dynamic Property**: สร้าง `email` อัตโนมัติโดยใช้ชื่อและนามสกุลมาต่อกัน
- **Method Shorthand**: เขียนฟังก์ชันภายใน Object แบบสั้นได้ทันที เช่น `getFullName()`

---

### 🚀 ขั้นตอนการทำงาน

1. **รับค่า (Input)**: ฟังก์ชันรับ `firstName`, `lastName`, และ `age`
2. **สร้าง Object**: สร้างโครงสร้างข้อมูลใหม่พร้อมคำนวณ Email ให้เป็นตัวพิมพ์เล็กทั้งหมด
3. **ส่งออก (Return)**: ส่ง Object ที่สร้างเสร็จแล้วกลับไปให้ตัวแปร `newUser`
4. **เรียกใช้งาน**: ดึงข้อมูลและเรียกใช้ Method จากตัวแปร `newUser` ได้ทันที

---

### 🖥️ ผลลัพธ์ (Output)

```
Returning Objects:
{
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
  email: 'john.doe@example.com',
  getFullName: [Function: getFullName],
  getAge: [Function: getAge]
}
Email: john.doe@example.com
Full name: John Doe
```

## 📘 9. Function as Parameter (Callback)

### 📝 โค้ด

```javascript
// ─────────────────────────────────
// 9. Function as Parameter (Callback)
// ─────────────────────────────────
function processArray(arr, callback) {
  const result = [];
  for (const item of arr) {
    result.push(callback(item));
  }
  return result;
}
const numbers = [1, 2, 3, 4, 5];
const doubled = processArray(numbers, (x) => x * 2);
const squared = processArray(numbers, (x) => x * x);
console.log("\nCallback Function:");
console.log("Original:", numbers);
console.log("Doubled:", doubled);
console.log("Squared:", squared);
```

### 🛠️ ส่วนประกอบของโค้ด

- **`processArray` (Higher-Order Function)**: ฟังก์ชันหลักที่รับ Array และ "ฟังก์ชันอื่น" (Callback) เข้ามาทำงาน
- **Callback Function**: ฟังก์ชันเฉพาะกิจที่ส่งเข้าไปเพื่อกำหนดว่าอยากให้ทำอะไรกับข้อมูลแต่ละตัว (เช่น คูณสอง หรือ ยกกำลังสอง)
- **Logic**: ใช้การวนลูป `for...of` เพื่อนำทุกตัวใน Array ไปผ่านฟังก์ชัน Callback แล้วเก็บผลลัพธ์ใหม่ลงใน `result`

---

### 🚀 ขั้นตอนการทำงาน

1. **เตรียมข้อมูล**: มี Array `numbers = [1, 2, 3, 4, 5]`
2. **ส่งคำสั่ง**:
   - รอบที่ 1: ส่งฟังก์ชัน `(x) => x * 2` เข้าไปเพื่อ **คูณสอง**
   - รอบที่ 2: ส่งฟังก์ชัน `(x) => x * x` เข้าไปเพื่อ **หาค่าผลต่าง (ยกกำลังสอง)**
3. **ประมวลผล**: `processArray` วนลูปนำเลขแต่ละตัวไปคำนวณตามฟังก์ชันที่ได้รับมา
4. **คืนค่า**: ส่งกลับ Array ใหม่ที่มีค่าตามที่คำนวณเสร็จแล้ว

---

### 🖥️ ผลลัพธ์ (Output)

```
Callback Function:
Original: [ 1, 2, 3, 4, 5 ]
Doubled: [ 2, 4, 6, 8, 10 ]
Squared: [ 1, 4, 9, 16, 25 ]
```

# 2.3 ไฟล์ 03-control-flow.js

## 📘 5. Short-Circuit Evaluation

### 📝 โค้ด

```javascript
console.log("\nShort-Circuit Evaluation:");
const user = { name: "John", age: 25 };
const admin = null;
// OR: use default value
const userName = admin?.name || user.name || "Anonymous";
console.log("User name:", userName);
// ?. คือการใช ้Optional Chaining - เป็นวิธีที่ปลอดภัยในการเข้าถึง properties ของ object ที่อาจเป็น null หรือ undefined
// admin?.name ก็คือ ถ้า admin มีค่า ให้เข้าถึง .name ไม่เช่นนั้นให้คืนค่า undefined
// 1. admin?.name
// - admin คือ null ❌
// - ไม่ error, ส่งคืน undefined
// 2. undefined || user.name
// - user.name คือ "John" ✅
// - ใชค่านี้ → "John"
// 3. ผลลัพธ์: "John"
// AND: check before accessing.
const userProfile = user && user.profile;
console.log("User profile:", userProfile); // undefined
```

### 🛠️ เครื่องมือที่ใช้

1. **Optional Chaining (`?.`)**: ใช้เข้าถึง Property ของ Object อย่างปลอดภัย ถ้าตัวหน้าเป็น `null/undefined` จะหยุดทันทีและคืนค่า `undefined` (ไม่เกิด Error)
2. **OR Operator (`||`)**: ใช้สำหรับกำหนด **"ค่าเริ่มต้น" (Default Value)** จะเลือกใช้ค่าขวาถ้าค่าซ้ายเป็น False (เช่น null, undefined, 0)
3. **AND Operator (`&&`)**: ใช้สำหรับ **"ตรวจสอบก่อนทำ"** จะไปต่อที่ค่าขวาได้ก็ต่อเมื่อค่าซ้ายเป็น True เท่านั้น

---

### 🚀 อธิบายการทำงาน

- **กรณี `userName`**:
  - `admin?.name` พยายามเข้าถึงชื่อของ admin แต่เนื่องจาก admin เป็น `null` จึงได้ค่า `undefined`
  - จากนั้น `undefined || user.name` จึงขยับไปเลือกค่าที่ใช้งานได้จริงคือ `"John"`
- **กรณี `userProfile`**:
  - `user && user.profile` ตรวจสอบว่ามี `user` ไหม? (มี)
  - จึงไปเช็กต่อที่ `user.profile` ซึ่งไม่ได้ถูกกำหนดไว้ ผลลัพธ์จึงเป็น `undefined`

---

### 🖥️ ผลลัพธ์ (Output)

```
Short-Circuit Evaluation:
User name: John
User profile: undefined
```

## 📘 7. Form Validation

### 📝 โค้ด

```javascript
// ─────────────────────────────────
// 7. Form Validation
// ─────────────────────────────────
function validateRegistration(formData) {
  // Create validation result object
  const errors = [];
  // Validate name
  if (!formData.name || formData.name.trim() === "") {
    errors.push("Name is required");
  } else if (formData.name.length < 3) {
    errors.push("Name must be at least 3 characters");
  }
  // Validate email
  if (!formData.email || formData.email.indexOf("@") === -1) {
    errors.push("Valid email is required");
  }
  // Validate age
  if (!formData.age || formData.age < 18) {
    errors.push("Must be 18 or older");
  }
  // Validate password
  if (!formData.password || formData.password.length < 6) {
    errors.push("Password must be at least 6 characters");
  }
  // Check if agree to terms
  if (!formData.agreeToTerms) {
    errors.push("Must agree to terms");
  }
  return {
    isValid: errors.length === 0,
    errors: errors,
  };
}
console.log("\nForm Validation:");
const validUser = {
  name: "John Doe",
  email: "john@example.com",
  age: 25,
  password: "securepass123",
  agreeToTerms: true,
};
const invalidUser = {
  name: "Jo",
  email: "invalidemail",
  age: 15,
  password: "pass",
  agreeToTerms: false,
};
console.log("Valid user:", validateRegistration(validUser));
console.log("Invalid user:", validateRegistration(invalidUser));
```

### 🛠️ กฎการตรวจสอบ (Validation Rules)

- **Name**: ต้องไม่ว่างและต้องมีความยาวอย่างน้อย 3 ตัวอักษร
- **Email**: ต้องมีสัญลักษณ์ `@`
- **Age**: ต้องมีอายุตั้งแต่ 18 ปีขึ้นไป
- **Password**: ต้องมีความยาวอย่างน้อย 6 ตัวอักษร
- **Terms**: ต้องยอมรับเงื่อนไข (`agreeToTerms` เป็น true)

---

### 🚀 ขั้นตอนการทำงาน

1. **รับข้อมูล**: ฟังก์ชันรับ Object `formData` เข้ามาตรวจสอบ
2. **เช็กเงื่อนไข**: ตรวจสอบทีละหัวข้อ หากไม่ตรงตามกฎจะทำการ `.push()` ข้อความ Error ลงใน Array `errors`
3. **สรุปผล**: ส่งคืน Object ผลลัพธ์ที่มี:
   - `isValid`: เป็น `true` ถ้าไม่มี Error เลย
   - `errors`: รายการข้อผิดพลาดทั้งหมดที่พบ

---

### 🖥️ ผลลัพธ์ (Output)

```
Form Validation:
Valid user: { isValid: true, errors: [] }
Invalid user: {
  isValid: false,
  errors: [
    'Name must be at least 3 characters',
    'Valid email is required',
    'Must be 18 or older',
    'Password must be at least 6 characters',
    'Must agree to terms'
  ]
}
```

# 2.4 ไฟล์ 04-loops.js

## 📘 9. Chaining methods

### 📝 โค้ด

```javascript
// ─────────────────────────────────
// 9. Chaining methods -- สําคัญมาก
// ─────────────────────────────────
console.log("\nMethod chaining:");
const data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
// Filter even > map to string > join
const evenStrings = data
  .filter((n) => n % 2 === 0) // [2, 4, 6, 8, 10]
  .map((n) => `${n}²=${n * n}`) // ["2²=4", "4²=16", ...]
  .join(", "); // "2²=4, 4²=16, ..."
console.log("Even numbers squared:", evenStrings);
// Calculate average with reduce and length
const numbers2 = [10, 20, 30, 40, 50];
const average = numbers2.reduce((sum, n) => sum + n, 0) / numbers2.length;
console.log("Average:", average);
```

### 🛠️ เครื่องมือที่ใช้ (Array Methods)

- **`.filter()`**: คัดกรองเฉพาะข้อมูลที่ต้องการ (ในที่นี้คือเลขคู่)
- **`.map()`**: เปลี่ยนแปลงรูปแบบข้อมูลแต่ละตัว (ในที่นี้คือเปลี่ยนเลขเป็นข้อความสูตรยกกำลัง)
- **`.join()`**: รวม Array ให้กลายเป็น String ชุดเดียว
- **`.reduce()`**: ยุบรวมข้อมูลทั้ง Array ให้เหลือค่าเดียว (ในที่นี้คือการหาผลรวม `sum`)

---

### 🚀 ขั้นตอนการทำงาน

1. **การทำ Method Chaining**:
   - เริ่มจากตัวเลข `1-10`
   - **Filter**: คัดเอาเฉพาะเลขคู่ออกมาได้ `[2, 4, 6, 8, 10]`
   - **Map**: นำเลขที่เหลือมาแปลงเป็นข้อความ เช่น `2` กลายเป็น `"2²=4"`
   - **Join**: นำข้อความทั้งหมดมาเชื่อมกันด้วย `, `
2. **การหาค่าเฉลี่ย (Average)**:
   - ใช้ `reduce` เพื่อรวมตัวเลขทุกตัวใน Array เข้าด้วยกัน
   - นำผลรวมที่ได้มาหารด้วย `numbers.length` (จำนวนสมาชิก) เพื่อหาค่าเฉลี่ย

---

### 🖥️ ผลลัพธ์ (Output)

```
Method chaining:
Even numbers squared: 2²=4, 4²=16, 6²=36, 8²=64, 10²=100
Average: 30
```

## 📘 10. Challenge: Student Grades

### 📝 โค้ด

```javascript
// ─────────────────────────────────
// 10. Challenge: Student Grades
// ─────────────────────────────────
const students = [
  { name: "Alice", score: 95 },
  { name: "Bob", score: 75 },
  { name: "Charlie", score: 85 },
  { name: "Diana", score: 92 },
  { name: "Eve", score: 88 },
];
console.log("\nChallenge: Student Analysis");
console.log("Students:", students);
// 1. Get all names
const names = students.map((s) => s.name);
console.log("Names:", names.join(", "));
// 2. Filter high scorers (>= 85)
const highScorers = students.filter((s) => s.score >= 85);
console.log(
  "High scorers:",
  highScorers.map((s) => `${s.name} (${s.score})`).join(", ")
);
// 3. Calculate class average
const classAverage =
  students.reduce((sum, s) => sum + s.score, 0) / students.length;
console.log("Class average:", classAverage.toFixed(2));
// 4. Find top scorer
const topScorer = students.reduce((top, s) => (s.score > top.score ? s : top));
console.log("Top scorer:", `${topScorer.name} (${topScorer.score})`);
// 5. Create summary
const summary = students
  .map((s) => ({
    ...s,
    grade: s.score >= 90 ? "A" : s.score >= 80 ? "B" : "C",
  }))
  .sort((a, b) => b.score - a.score);
console.log("Summary (sorted):");
summary.forEach((s) => console.log(` ${s.name}: ${s.score} (${s.grade})`));
console.log("\n✅ Activity 4 completed!");
```

### 🛠️ เครื่องมือที่ใช้ (Methods)

- **`.map()`**: ใช้ดึงรายชื่อ และสร้าง Object ใหม่ที่มีการเพิ่ม `grade` (ใช้ Spread Operator `...s`)
- **`.filter()`**: คัดกรองเฉพาะนักเรียนที่ได้คะแนนสูง (>= 85)
- **`.reduce()`**: ใช้หาผลรวมคะแนนเพื่อคำนวณค่าเฉลี่ย และใช้เปรียบเทียบเพื่อหา "คนเก่งที่สุด" (Top Scorer)
- **`.sort()`**: จัดลำดับคะแนนจากมากไปน้อย (Descending Order)

---

### 🚀 ขั้นตอนการทำงาน

1. **Names**: ดึงเฉพาะ Property `name` ออกมาเป็นรายการชื่อ
2. **High Scorers**: คัดกรองคนที่มีคะแนนตั้งแต่ 85 ขึ้นไป
3. **Average**: รวมคะแนนทั้งหมดแล้วหารด้วยจำนวนนักเรียน (ใช้ `.toFixed(2)` เพื่อปัดทศนิยม 2 ตำแหน่ง)
4. **Top Scorer**: วนลูปเปรียบเทียบคะแนนทีละคู่เพื่อหาคนที่ได้คะแนนสูงสุด
5. **Summary & Sorting**:
   - สร้างข้อมูลชุดใหม่ที่มีการเพิ่ม `grade` (A, B, C) ตามเงื่อนไขคะแนน
   - เรียงลำดับข้อมูลทั้งหมดตามคะแนนจากสูงสุดลงมา

---

### 🖥️ ผลลัพธ์ (Output)

```
Challenge: Student Analysis
Names: Alice, Bob, Charlie, Diana, Eve
High scorers: Alice (95), Charlie (85), Diana (92), Eve (88)
Class average: 87.00
Top scorer: Alice (95)
Summary (sorted):
 Alice: 95 (A)
 Diana: 92 (A)
 Eve: 88 (B)
 Charlie: 85 (B)
 Bob: 75 (C)
```

# 2.5 ไฟล์ 05-integration.js

## 📘 Activity 5: Integration - Quiz Application

### 📝 โค้ด

```javascript
// ============================================
// Activity 5: Integration - Quiz Application
// ============================================
console.log("🎯🎯 === QUIZ APPLICATION === 🎯🎯\n");
// Quiz data
const quizzes = [
  {
    question: "What is 5 + 3?",
    options: ["8", "7", "6", "9"],
    correctAnswer: 0, // Index of correct option
  },
  {
    question: "What is the capital of Thailand?",
    options: ["Phuket", "Bangkok", "Chiang Mai", "Pattaya"],
    correctAnswer: 1,
  },
  {
    question: "What is the largest planet?",
    options: ["Mars", "Saturn", "Jupiter", "Neptune"],
    correctAnswer: 2,
  },
  {
    question: "What is 2^8?",
    options: ["128", "256", "64", "512"],
    correctAnswer: 1,
  },
  {
    question: "Which is NOT a JavaScript data type?",
    options: ["string", "class", "symbol", "boolean"],
    correctAnswer: 1,
  },
];
// Quiz results
let results = [];
// Process each quiz
quizzes.forEach((quiz, index) => {
  const userAnswer = Math.floor(Math.random() * 4); // จําลองการทํา quiz
  const isCorrect = userAnswer === quiz.correctAnswer;
  results.push({
    questionNum: index + 1,
    question: quiz.question,
    userAnswer: quiz.options[userAnswer],
    correctAnswer: quiz.options[quiz.correctAnswer],
    isCorrect: isCorrect,
  });
});
// Display results
console.log("QUIZ RESULTS:");
console.log("─".repeat(60));
results.forEach((result) => {
  const status = result.isCorrect ? "✅ CORRECT" : "❌ WRONG";
  console.log(`Q${result.questionNum}: ${result.question}`);
  console.log(` Your answer: ${result.userAnswer}`);
  if (!result.isCorrect) {
    console.log(` Correct answer: ${result.correctAnswer}`);
  }
  console.log(` ${status}`);
  console.log();
});
// Calculate score
const correctCount = results.filter((r) => r.isCorrect).length;
const score = (correctCount / results.length) * 100;
console.log("─".repeat(60));
console.log(
  `FINAL SCORE: ${correctCount}/${results.length} (${score.toFixed(1)}%)`
);
// Grade assignment
let grade;
if (score >= 90) {
  grade = "A";
} else if (score >= 80) {
  grade = "B";
} else if (score >= 70) {
  grade = "C";
} else if (score >= 60) {
  grade = "D";
} else {
  grade = "F";
}
console.log(`GRADE: ${grade}`);
// Feedback
console.log("\nFEEDBACK:");
if (score === 100) {
  console.log("🌟🌟 Perfect score! Excellent work!");
} else if (score >= 80) {
  console.log("👍👍 Great job! Keep practicing.");
} else if (score >= 60) {
  console.log("📚📚 Good effort. Review the material and try again.");
} else {
  console.log("💪💪 Keep practicing. You'll improve!");
}
// Statistics
console.log("\n📊📊 STATISTICS:");
console.log(`Total questions: ${results.length}`);
console.log(`Correct: ${correctCount}`);
console.log(`Incorrect: ${results.length - correctCount}`);
console.log(`Success rate: ${score.toFixed(1)}%`);
// Category breakdown (if applicable)
const byCorrectness = results.reduce(
  (acc, r) => {
    acc[r.isCorrect ? "correct" : "incorrect"]++;
    return acc;
  },
  { correct: 0, incorrect: 0 }
);
console.log("\nAnswer breakdown:");
console.log(` ✅ Correct: ${byCorrectness.correct}`);
console.log(` ❌ Incorrect: ${byCorrectness.incorrect}`);
console.log("\n✅ All activities completed!");
console.log("━".repeat(60));
```

### 🛠️ ฟีเจอร์หลักของโค้ด

- **Quiz Data Structure**: เก็บโจทย์ ตัวเลือก และดัชนีคำตอบที่ถูกต้องในรูปแบบ Array of Objects
- **Simulation Logic**: ใช้ `Math.random()` เพื่อจำลองการเลือกคำตอบของผู้ใช้
- **Evaluation System**: เปรียบเทียบคำตอบและจัดเก็บผลลัพธ์ลงใน Array `results`
- **Scoring & Grading**: คำนวณเปอร์เซ็นต์คะแนนและตัดเกรด (A-F) ด้วยเงื่อนไข `if-else`
- **Statistics & Feedback**: ใช้ `.reduce()` เพื่อสรุปภาพรวมจำนวนข้อที่ถูก/ผิด และแสดงข้อความให้กำลังใจตามคะแนนที่ได้

---

### 🚀 ขั้นตอนการทำงาน

1. **Processing**: วนลูป `quizzes` เพื่อจำลองการตอบคำถามทีละข้อ และบันทึกผลลัพธ์ (คำตอบที่เลือก, คำตอบที่ถูก, สถานะ)
2. **Display**: แสดงรายละเอียดผลลัพธ์ของแต่ละข้อ พร้อมสัญลักษณ์ ✅ หรือ ❌
3. **Calculation**:
   - ใช้ `.filter()` เพื่อนับจำนวนข้อที่ถูก
   - คำนวณคะแนนเป็นเปอร์เซ็นต์
4. **Analysis**: ใช้ `.reduce()` เพื่อแยกประเภทคำตอบ (Correct/Incorrect) ออกเป็นกลุ่มสถิติ

---

### 🖥️ ตัวอย่างผลลัพธ์ (Output Example)

```
🎯🎯 === QUIZ APPLICATION === 🎯🎯

QUIZ RESULTS:
────────────────────────────────────────────────────────────
Q1: What is 5 + 3?
 Your answer: 8
 ✅ CORRECT

Q2: What is the capital of Thailand?
 Your answer: Phuket
 Correct answer: Bangkok
 ❌ WRONG

... (ข้ออื่นๆ) ...

────────────────────────────────────────────────────────────
FINAL SCORE: 3/5 (60.0%)
GRADE: D

FEEDBACK:
📚📚 Good effort. Review the material and try again.

📊📊 STATISTICS:
Total questions: 5
Correct: 3
Incorrect: 2
Success rate: 60.0%

Answer breakdown:
 ✅ Correct: 3
 ❌ Incorrect: 2
```
