# Hookup-spaces
Store 
html = """<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8">

<title>Online Quiz</title>

<meta name="viewport" content="width=device-width, initial-scale=1">

<style>

body{font-family:Arial, sans-serif;background:#f5f5f5;display:flex;justify-content:center;align-items:center;min-height:100vh;margin:0;}

.quiz-box{background:white;max-width:400px;width:100%;padding:20px;border-radius:10px;box-shadow:0 4px 10px rgba(0,0,0,0.1);}

h2{text-align:center;}

.question{font-size:18px;margin-bottom:15px;}

.option{display:block;background:#eee;margin:8px 0;padding:8px;border-radius:5px;cursor:pointer;}

.option:hover{background:#ddd;}

.option.correct{background:#b8f7b8;}

.option.wrong{background:#f7b8b8;}

button{margin-top:15px;width:100%;padding:10px;border:none;background:#007bff;color:white;font-size:16px;border-radius:5px;cursor:pointer;}

button:hover{background:#0056b3;}

.result{text-align:center;font-size:20px;display:none;}

</style>

</head>

<body>

<div class="quiz-box">

<h2>Online Quiz</h2>

<div id="quiz">

<div class="question" id="question"></div>

<div id="options"></div>

<button onclick="nextQuestion()">Next</button>

</div>

<div class="result" id="result"></div>

</div>



<script>

const quizData = [

 {q:"Which planet is known as the Red Planet?", options:["Earth","Mars","Jupiter","Venus"], answer:1},

 {q:"Capital of France?", options:["Rome","Paris","Berlin","Madrid"], answer:1},

 {q:"Which runs in browser?", options:["Python","Java","C++","JavaScript"], answer:3}

];



let index = 0;

let score = 0;



function loadQuestion(){

  const q = quizData[index];

  document.getElementById("question").innerHTML = q.q;

  const optionsHTML = q.options.map((opt,i)=>

    `<div class="option" onclick="checkAnswer(${i})">${opt}</div>`).join("");

  document.getElementById("options").innerHTML = optionsHTML;

}



function checkAnswer(i){

  const options = document.querySelectorAll(".option");

  if(i === quizData[index].answer){

    options[i].classList.add("correct");

    score++;

  } else {

    options[i].classList.add("wrong");

  }

  options.forEach(o=>o.onclick=null);

}



function nextQuestion(){

  index++;

  if(index < quizData.length){

    loadQuestion();

  } else {

    document.getElementById("quiz").style.display="none";

    document.getElementById("result").style.display="block";

    document.getElementById("result").innerHTML = "Quiz Finished!<br>Your Score: "+score+"/"+quizData.length;

  }

}



loadQuestion();

</script>

</body>

</html>

