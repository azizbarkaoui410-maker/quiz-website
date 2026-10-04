<!DOCTYPE html>
<html lang="ar" dir="rtl">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>اختبار المعلومات</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #eef2ff;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 600px;
            margin: auto;
            background: white;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
        }

        h1 {
            text-align: center;
        }

        #question {
            font-size: 22px;
            font-weight: bold;
            margin: 25px 0;
        }

        .answer {
            width: 100%;
            padding: 14px;
            margin: 8px 0;
            border: none;
            border-radius: 10px;
            background: #e5e7eb;
            font-size: 17px;
            cursor: pointer;
        }

        .answer:hover {
            background: #d1d5db;
        }

        #next {
            width: 100%;
            padding: 14px;
            margin-top: 15px;
            border: none;
            border-radius: 10px;
            background: #2563eb;
            color: white;
            font-size: 17px;
            cursor: pointer;
        }

        #result {
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            margin-top: 25px;
        }
    </style>
</head>

<body>

<div class="container">

    <h1>🧠 اختبار المعلومات</h1>

    <div id="quiz">

        <div id="question"></div>

        <div id="answers"></div>

        <button id="next" onclick="nextQuestion()">
            السؤال التالي
        </button>

    </div>

    <div id="result"></div>

</div>


<script>

const questions = [

    {
        question: "ما هي عاصمة تونس؟",
        answers: [
            "صفاقس",
            "سوسة",
            "تونس",
            "قابس"
        ],
        correct: "تونس"
    },

    {
        question: "كم عدد أيام الأسبوع؟",
        answers: [
            "5",
            "6",
            "7",
            "8"
        ],
        correct: "7"
    },

    {
        question: "ما هو الكوكب المعروف بالكوكب الأحمر؟",
        answers: [
            "الأرض",
            "المريخ",
            "المشتري",
            "الزهرة"
        ],
        correct: "المريخ"
    },

    {
        question: "ما هي لغة إنشاء هيكل صفحات الويب؟",
        answers: [
            "HTML",
            "Python",
            "C++",
            "Java"
        ],
        correct: "HTML"
    },

    {
        question: "كم يساوي 5 × 5؟",
        answers: [
            "10",
            "15",
            "20",
            "25"
        ],
        correct: "25"
    }

];


let currentQuestion = 0;
let score = 0;


function showQuestion() {

    const question = questions[currentQuestion];

    document.getElementById("question").textContent =
        question.question;

    const answersDiv = document.getElementById("answers");

    answersDiv.innerHTML = "";


    question.answers.forEach(answer => {

        const button = document.createElement("button");

        button.className = "answer";

        button.textContent = answer;

        button.onclick = function() {

            checkAnswer(answer);

        };

        answersDiv.appendChild(button);

    });

}


function checkAnswer(answer) {

    const correctAnswer =
        questions[currentQuestion].correct;

    if (answer === correctAnswer) {

        score++;

        alert("✅ إجابة صحيحة!");

    } else {

        alert("❌ إجابة خاطئة!");

    }

}


function nextQuestion() {

    currentQuestion++;

    if (currentQuestion < questions.length) {

        showQuestion();

    } else {

        document.getElementById("quiz").style.display = "none";

        document.getElementById("result").innerHTML =
            "🎉 انتهى الاختبار!<br><br>" +
            "نتيجتك: " + score + " / " + questions.length;

    }

}


showQuestion();

</script>

</body>
</html>
