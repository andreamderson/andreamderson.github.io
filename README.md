<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Название теста</title>

<style>

/* =========================
   МЕСТО ДЛЯ ТВОИХ ШРИФТОВ
========================= */

/*
@font-face {
    font-family: 'MyFont';
    src: url('fonts/font.ttf');
}
*/

:root{
    --bg-color: #111;
    --text-color: white;
    --button-color: #222;
    --button-hover: #333;
    --input-color: #1a1a1a;
}

/* =========================
   ОСНОВА
========================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    background: var(--bg-color);

    /* МЕСТО ДЛЯ ТВОЕГО ФОНА */
    /*
    background-image: url("background.png");
    background-size: cover;
    background-position: center;
    */

    color: var(--text-color);

    /* МЕСТО ДЛЯ ТВОЕГО ШРИФТА */
    /*
    font-family: 'MyFont';
    */

    font-family: Arial, sans-serif;

    min-height:100vh;

    display:flex;
    justify-content:center;
    align-items:center;

    padding:20px;
}

/* =========================
   КОНТЕЙНЕР
========================= */

.container{
    width:100%;
    max-width:700px;

    text-align:center;
}

/* =========================
   СТРАНИЦЫ
========================= */

.page{
    display:none;
}

.page.active{
    display:block;
}

/* =========================
   ЗАГОЛОВОК
========================= */

.title{
    font-size:40px;
    margin-bottom:50px;
}

/* =========================
   INPUT
========================= */

input,
textarea{
    width:100%;
    padding:15px;

    background:var(--input-color);

    border:none;
    outline:none;

    color:white;

    margin-top:20px;

    font-size:18px;
}

textarea{
    min-height:150px;
    resize:vertical;
}

/* =========================
   КНОПКИ
========================= */

button{
    margin-top:30px;

    padding:15px 30px;

    border:none;

    background:var(--button-color);

    color:white;

    cursor:pointer;

    font-size:18px;

    transition:0.2s;
}

button:hover{
    background:var(--button-hover);
}

/* =========================
   ВОПРОСЫ
========================= */

.question{
    font-size:30px;
    margin-bottom:30px;
}

.answers{
    display:flex;
    flex-direction:column;
    gap:15px;
}

.answer-btn{
    width:100%;
}

/* =========================
   КАРТИНКИ
========================= */

.question-image{
    width:100%;
    max-height:400px;
    object-fit:cover;

    margin-bottom:25px;

    border-radius:10px;
}

/* =========================
   ВИДЕО
========================= */

.question-video{
    width:100%;
    height:400px;

    margin-bottom:25px;
}

</style>
</head>
<body>

<div class="container">

    <!-- =========================
         РЕГИСТРАЦИЯ
    ========================== -->

    <div class="page active" id="page-register">

        <div class="title">
            НАЗВАНИЕ ТЕСТА
        </div>

        <div class="question">
            Введите своё имя
        </div>

        <input
            type="text"
            id="username"
            placeholder="Ваше имя"
        >

        <button onclick="startTest()">
            Начать
        </button>

    </div>

    <!-- =========================
         ВОПРОС 1
    ========================== -->

    <div class="page" id="page-1">

        <div class="question">
            Ваш первый вопрос?
        </div>

        <div class="answers">

            <button class="answer-btn" onclick="nextPage(2)">
                Вариант 1
            </button>

            <button class="answer-btn" onclick="nextPage(2)">
                Вариант 2
            </button>

            <button class="answer-btn" onclick="nextPage(2)">
                Вариант 3
            </button>

            <button class="answer-btn" onclick="nextPage(2)">
                Вариант 4
            </button>

        </div>

    </div>

    <!-- =========================
         ВОПРОС С КАРТИНКОЙ
    ========================== -->

    <div class="page" id="page-2">

        <!-- МЕСТО ДЛЯ КАРТИНКИ -->
        <!--
        <img
            src="images/test.jpg"
            class="question-image"
        >
        -->

        <div class="question">
            Вопрос с картинкой
        </div>

        <div class="answers">

            <button class="answer-btn" onclick="nextPage(3)">
                Ответ 1
            </button>

            <button class="answer-btn" onclick="nextPage(3)">
                Ответ 2
            </button>

            <button class="answer-btn" onclick="nextPage(3)">
                Ответ 3
            </button>

        </div>

    </div>

    <!-- =========================
         ВОПРОС С ВИДЕО
    ========================== -->

    <div class="page" id="page-3">

        <!-- МЕСТО ДЛЯ ВИДЕО -->
        <!--
        <iframe
            class="question-video"
            src="https://www.youtube.com/embed/VIDEO_ID"
            frameborder="0"
            allowfullscreen>
        </iframe>
        -->

        <div class="question">
            Вопрос с видео
        </div>

        <div class="answers">

            <button class="answer-btn" onclick="nextPage(4)">
                Да
            </button>

            <button class="answer-btn" onclick="nextPage(4)">
                Нет
            </button>

        </div>

    </div>

    <!-- =========================
         РАЗВЁРНУТЫЙ ОТВЕТ
    ========================== -->

    <div class="page" id="page-4">

        <div class="question">
            Напишите свой ответ
        </div>

        <textarea
            placeholder="Введите текст..."
        ></textarea>

        <button onclick="nextPage(5)">
            Продолжить
        </button>

    </div>

    <!-- =========================
         ФИНАЛ
    ========================== -->

    <div class="page" id="page-5">

        <div class="title">
            Спасибо за прохождение
        </div>

        <div class="question">
            Ваши результаты вам сообщат позже.<br><br>

            Запомните имя, которое вы вводили.
        </div>

    </div>

</div>

<script>

/* =========================
   СТАРТ ТЕСТА
========================= */

function startTest(){

    const username = document.getElementById('username').value;

    if(username.trim() === ''){
        alert('Введите имя');
        return;
    }

    showPage('page-1');
}

/* =========================
   ПЕРЕКЛЮЧЕНИЕ СТРАНИЦ
========================= */

function nextPage(pageNumber){
    showPage('page-' + pageNumber);
}

/* =========================
   ПОКАЗАТЬ СТРАНИЦУ
========================= */

function showPage(id){

    const pages = document.querySelectorAll('.page');

    pages.forEach(page => {
        page.classList.remove('active');
    });

    document.getElementById(id).classList.add('active');
}

</script>

</body>
</html>
