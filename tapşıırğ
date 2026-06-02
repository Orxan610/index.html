<!DOCTYPE html>
<html lang="az">
<head>
<meta charset="UTF-8">
<title>2-ci Sinif Riyaziyyat Testi</title>

<style>
body{
    font-family: Arial, sans-serif;
    margin:20px;
    background:#f5f5f5;
}

.question{
    background:white;
    padding:15px;
    margin:10px 0;
    border-radius:10px;
    box-shadow:0 0 5px rgba(0,0,0,0.1);
}

.correct{
    color:green;
    font-weight:bold;
}

.wrong{
    color:red;
    font-weight:bold;
}

label{
    display:block;
    margin:5px 0;
    cursor:pointer;
}
</style>
</head>
<body>

<h1>🧮 2-ci Sinif Riyaziyyat Testi</h1>

<div id="quiz"></div>

<script>

const quiz = document.getElementById("quiz");

let questions = [];

function shuffle(arr){
    return arr.sort(()=>Math.random()-0.5);
}

for(let i=1;i<=20;i++){

    let a=Math.floor(Math.random()*20)+1;
    let b=Math.floor(Math.random()*20)+1;

    questions.push({
        text:`${a} + ${b} = ?`,
        correct:a+b,
        options:shuffle([
            a+b,
            a+b+1,
            a+b-1,
            a+b+2
        ])
    });
}

for(let i=1;i<=15;i++){

    let a=Math.floor(Math.random()*20)+5;
    let b=Math.floor(Math.random()*5)+1;

    questions.push({
        text:`${a} - ${b} = ?`,
        correct:a-b,
        options:shuffle([
            a-b,
            a-b+1,
            a-b-1,
            a-b+2
        ])
    });
}

for(let i=1;i<=10;i++){

    let a=Math.floor(Math.random()*5)+1;
    let b=Math.floor(Math.random()*5)+1;

    questions.push({
        text:`${a} × ${b} = ?`,
        correct:a*b,
        options:shuffle([
            a*b,
            a*b+1,
            a*b-1,
            a*b+2
        ])
    });
}

const logicQuestions = [
{
text:"Aysunun 3 alması var idi. Ona daha 2 alma verdilər. İndi neçə alması var?",
correct:5,
options:[5,4,6,7]
},
{
text:"Masada 10 qələm var. 4-ü götürüldü. Neçə qaldı?",
correct:6,
options:[5,6,7,8]
},
{
text:"Bir həftədə neçə gün var?",
correct:7,
options:[5,6,7,8]
},
{
text:"2 onluq neçə vahiddir?",
correct:20,
options:[10,15,20,25]
},
{
text:"Saat 3-dən 5-ə qədər neçə saat keçir?",
correct:2,
options:[1,2,3,4]
}
];

questions.push(...logicQuestions);

questions = questions.slice(0,50);

const savedAnswers =
JSON.parse(localStorage.getItem("answers")) || {};

questions.forEach((q,index)=>{

    const div=document.createElement("div");
    div.className="question";

    div.innerHTML=`
        <h3>${index+1}. ${q.text}</h3>
        <div id="result${index}"></div>
    `;

    q.options.forEach(option=>{

        const label=document.createElement("label");

        label.innerHTML=`
        <input
        type="radio"
        name="q${index}"
        value="${option}">
        ${option}
        `;

        const radio=label.querySelector("input");

        if(savedAnswers[index]==option){

            radio.checked=true;

            if(option==q.correct){
                label.classList.add("correct");
            }else{
                label.classList.add("wrong");
            }
        }

        radio.addEventListener("change",()=>{

            document
            .querySelectorAll(`input[name="q${index}"]`)
            .forEach(r=>{

                r.parentElement.classList.remove(
                    "correct",
                    "wrong"
                );
            });

            if(option==q.correct){

                label.classList.add("correct");

                document.getElementById(
                `result${index}`
                ).innerHTML=
                "✅ Düz cavab";

            }else{

                label.classList.add("wrong");

                document.getElementById(
                `result${index}`
                ).innerHTML=
                "❌ Səhv cavab";
            }

            savedAnswers[index]=option;

            localStorage.setItem(
                "answers",
                JSON.stringify(savedAnswers)
            );
        });

        div.appendChild(label);
    });

    quiz.appendChild(div);
});

</script>

</body>
</html>
