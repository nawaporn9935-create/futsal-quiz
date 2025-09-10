# futsal-quiz
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>แบบทดสอบฟุตซอล</title>
  <style>
    body {
      font-family: "Tahoma", sans-serif;
      margin: 0; padding: 0;
      background: linear-gradient(to bottom, #001f3f, #00509e);
      color: white;
    }
    .container {
      width: 95%; max-width: 600px;
      margin: 20px auto;
      background: rgba(0,0,0,0.5);
      padding: 15px 20px;
      border-radius: 12px;
    }
    h1,h2{text-align:center;margin-bottom:15px;}
    input[type=text]{width:90%;padding:8px;margin:5px 0;border-radius:5px;border:none;}
    button,a.download-link{
      width:90%; padding:10px; margin:10px auto; display:block;
      background-color:#0074d9; border:none; border-radius:8px; font-size:16px;
      color:white; text-align:center; text-decoration:none; cursor:pointer;
    }
    button:hover,a.download-link:hover{background-color:#00509e;}
    .question{margin-bottom:15px;padding:8px;border-bottom:1px solid #ccc;}
    label{display:block;margin:5px 0;}
    #result{margin-top:15px;padding:10px;background:rgba(0,0,0,0.3);border-radius:10px;}
    .correct{color:#00ffcc;} .wrong{color:#ff8080;}
    .futsal-ball{
      display:inline-block;width:30px;height:30px;
      background:url('https://upload.wikimedia.org/wikipedia/commons/6/6e/Soccerball.svg') no-repeat center center;
      background-size:contain; vertical-align:middle; margin-right:8px;
    }
  </style>
</head>
<body>
  <div class="container" id="quizPage">
    <h1><span class="futsal-ball"></span>แบบทดสอบฟุตซอล</h1>
    <h2>วิชาสุขศึกษาและพลศึกษา</h2>

    <div id="loginDiv">
      <p>กรุณากรอกรหัสนักเรียนและชื่อก่อนทำแบบทดสอบ</p>
      <input type="text" id="studentId" placeholder="รหัสนักเรียน"><br>
      <input type="text" id="studentName" placeholder="ชื่อ - สกุล"><br>
      <button onclick="startQuiz()">เริ่มทำแบบทดสอบ</button>
    </div>

    <form id="quizForm" style="display:none;">
      <div class="question">
        1. การยิงประตูฟุตซอลควรใช้ปลายเท้าเสมอ
        <label><input type="radio" name="q1" value="ผิด"> ผิด</label>
        <label><input type="radio" name="q1" value="ถูก"> ถูก</label>
      </div>
      <div class="question">
        2. ควรเล็งไปที่มุมประตูเพื่อเพิ่มโอกาสทำประตู
        <label><input type="radio" name="q2" value="ถูก"> ถูก</label>
        <label><input type="radio" name="q2" value="ผิด"> ผิด</label>
      </div>
      <div class="question">
        3. การยกเท้าสูงเกินไปอาจเป็นอันตรายต่อคู่ต่อสู้
        <label><input type="radio" name="q3" value="ถูก"> ถูก</label>
        <label><input type="radio" name="q3" value="ผิด"> ผิด</label>
      </div>
      <div class="question">
        4. การยิงประตูด้วยส้นเท้าเป็นทักษะพื้นฐานที่ต้องฝึกก่อน
        <label><input type="radio" name="q4" value="ผิด"> ผิด</label>
        <label><input type="radio" name="q4" value="ถูก"> ถูก</label>
      </div>
      <div class="question">
        5. การยิงประตูที่ดีควรมีสมาธิและมั่นใจ
        <label><input type="radio" name="q5" value="ถูก"> ถูก</label>
        <label><input type="radio" name="q5" value="ผิด"> ผิด</label>
      </div>
      <div class="question">
        6. ผู้เล่นสามารถใช้ทุกส่วนของเท้าในการยิงประตูได้
        <label><input type="radio" name="q6" value="ถูก"> ถูก</label>
        <label><input type="radio" name="q6" value="ผิด"> ผิด</label>
      </div>
      <div class="question">
        7. การส่งบอลและการยิงประตูคือทักษะเดียวกัน
        <label><input type="radio" name="q7" value="ผิด"> ผิด</label>
        <label><input type="radio" name="q7" value="ถูก"> ถูก</label>
      </div>
      <div class="question">
        8. การยิงบอลจากระยะใกล้มักได้ผลมากกว่าระยะไกล
        <label><input type="radio" name="q8" value="ถูก"> ถูก</label>
        <label><input type="radio" name="q8" value="ผิด"> ผิด</label>
      </div>
      <div class="question">
        9. ควรยิงประตูทันทีโดยไม่จำเป็นต้องประเมินตำแหน่งผู้รักษาประตู
        <label><input type="radio" name="q9" value="ผิด"> ผิด</label>
        <label><input type="radio" name="q9" value="ถูก"> ถูก</label>
      </div>
      <div class="question">
        10. การฝึกซ้อมยิงประตูบ่อย ๆ ช่วยเพิ่มประสิทธิภาพ
        <label><input type="radio" name="q10" value="ถูก"> ถูก</label>
        <label><input type="radio" name="q10" value="ผิด"> ผิด</label>
      </div>
      <button type="button" onclick="checkAnswers()">ส่งคำตอบ</button>
    </form>

    <div id="result"></div>
    <a href="#" class="download-link" id="downloadLink">📥 ดาวน์โหลดผลรวมทั้งหมด</a>
  </div>

<script>
const answers={q1:"ผิด",q2:"ถูก",q3:"ถูก",q4:"ผิด",q5:"ถูก",q6:"ถูก",q7:"ผิด",q8:"ถูก",q9:"ผิด",q10:"ถูก"};
let studentData={id:"",name:""};

function startQuiz(){
  let id=document.getElementById("studentId").value.trim();
  let name=document.getElementById("studentName").value.trim();
  if(id===""||name===""){alert("กรุณากรอกรหัสนักเรียนและชื่อก่อน");return;}
  studentData.id=id; studentData.name=name;
  document.getElementById("loginDiv").style.display="none";
  document.getElementById("quizForm").style.display="block";
}

function checkAnswers(){
  let score=0; let resultHTML="<h3>ผลการทำแบบทดสอบ</h3><ul>"; let answersGiven=[];
  for(let q in answers){
    let sel=document.querySelector(`input[name="${q}"]:checked`);
    if(sel){answersGiven.push(sel.value); if(sel.value===answers[q]){score++; resultHTML+=`<li class='correct'>ข้อ ${q.slice(1)} ✔️ ถูกต้อง</li>`;}
    else{resultHTML+=`<li class='wrong'>ข้อ ${q.slice(1)} ❌ คำตอบที่ถูกคือ: ${answers[q]}</li>`;}}
    else{answersGiven.push("-"); resultHTML+=`<li class='wrong'>ข้อ ${q.slice(1)} ❌ ไม่ได้เลือกคำตอบ</li>`;}
  }
  resultHTML+="</ul>"; resultHTML+=`<h3>คะแนนรวม: ${score}/10</h3>`;
  if(score>=8){resultHTML+="<p>👍 เยี่ยมมาก!</p>";}
  else if(score>=5){resultHTML+="<p>🙂 ทำได้ปานกลาง</p>";}
  else{resultHTML+="<p>⚽ ต้องปรับปรุง</p>";}
  document.getElementById("result").innerHTML=resultHTML;
  saveResult(studentData.id,studentData.name,score,answersGiven);
}

function saveResult(id,name,score,answersGiven){
  let allResults=JSON.parse(localStorage.getItem("quizResults"))||[];
  allResults.push({id,name,score,answers:answersGiven});
  localStorage.setItem("quizResults",JSON.stringify(allResults));
  updateDownloadLink();
}

function updateDownloadLink(){
  let allResults=JSON.parse(localStorage.getItem("quizResults"))||[];
  if(allResults.length===0)return;
  let csvContent="รหัสนักเรียน,ชื่อ,คะแนน,คำตอบ\\n";
  allResults.forEach(r=>{csvContent+=`${r.id},${r.name},${r.score},${r.answers.join(" ")}\\n`;});
  const blob=new Blob([csvContent],{type:"text/csv;charset=utf-8;"});
  const url=URL.createObjectURL(blob);
  let link=document.getElementById("downloadLink");
  link.href=url; link.download="futsal_quiz_results.csv";
}
</script>
</body>
</html>
