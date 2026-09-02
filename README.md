<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">

<meta name="viewport"
      content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

<meta name="theme-color" content="#087f8c">

<meta name="description"
      content="نگین AAC - سامانه ارتباط جایگزین و افزوده برای کودکان و افراد دارای نیازهای ارتباطی">

<title>💎 نگین AAC | هر کودک، یک نگین</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap"
      rel="stylesheet">

<style>

/* =========================================================
   Negin AAC
   Single File Edition
   HTML + CSS + JavaScript
   ========================================================= */

:root{

    --primary:#087f8c;
    --primary-dark:#075f69;

    --blue:#2563eb;
    --green:#16a34a;
    --yellow:#f59e0b;
    --orange:#ea580c;
    --purple:#7c3aed;
    --red:#dc2626;

    --background:#f4f8fa;
    --surface:#ffffff;

    --text:#172033;
    --muted:#64748b;

    --border:#e2e8f0;

    --shadow:
        0 12px 35px rgba(15,23,42,.08);

    --radius:22px;
}

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

html{
    scroll-behavior:smooth;
}

body{

    font-family:"Tajawal",sans-serif;

    background:
        radial-gradient(
            circle at top right,
            rgba(8,127,140,.08),
            transparent 30%
        ),
        var(--background);

    color:var(--text);

    min-height:100vh;

    line-height:1.7;
}

/* =========================================================
   HEADER
   ========================================================= */

.header{

    position:sticky;
    top:0;

    z-index:1000;

    background:rgba(255,255,255,.94);

    backdrop-filter:blur(18px);

    border-bottom:1px solid var(--border);

    padding:
        12px
        max(15px,calc((100% - 1200px)/2));

    display:flex;

    justify-content:space-between;

    align-items:center;
}

.brand{

    display:flex;

    align-items:center;

    gap:12px;
}

.logo{

    width:52px;
    height:52px;

    border-radius:17px;

    display:flex;

    justify-content:center;
    align-items:center;

    font-size:29px;

    background:
        linear-gradient(
            135deg,
            var(--primary),
            var(--blue)
        );

    color:white;

    box-shadow:
        0 8px 22px rgba(8,127,140,.25);
}

.brand-title{

    font-size:21px;

    font-weight:900;
}

.brand-subtitle{

    display:block;

    color:var(--muted);

    font-size:12px;
}

.header-buttons{

    display:flex;

    gap:8px;
}

.header-btn{

    width:44px;
    height:44px;

    border-radius:13px;

    border:1px solid var(--border);

    background:white;

    font-size:19px;

    cursor:pointer;

    transition:.2s;
}

.header-btn:hover{

    transform:translateY(-2px);

    background:#f1f5f9;
}

/* =========================================================
   MAIN
   ========================================================= */

.container{

    width:min(
        1200px,
        calc(100% - 28px)
    );

    margin:25px auto 60px;
}

/* =========================================================
   HERO
   ========================================================= */

.hero{

    background:
        linear-gradient(
            135deg,
            rgba(8,127,140,.12),
            rgba(37,99,235,.10)
        );

    border:
        1px solid
        rgba(8,127,140,.12);

    border-radius:28px;

    padding:28px;

    margin-bottom:20px;

    display:flex;

    justify-content:space-between;

    align-items:center;

    gap:20px;
}

.hero-label{

    color:var(--primary);

    font-weight:800;

    font-size:13px;
}

.hero h1{

    font-size:
        clamp(
            25px,
            5vw,
            40px
        );

    margin:5px 0;

    font-weight:900;
}

.hero p{

    color:var(--muted);

    font-size:15px;
}

.online{

    display:flex;

    align-items:center;

    gap:8px;

    background:white;

    padding:9px 15px;

    border-radius:50px;

    box-shadow:var(--shadow);

    white-space:nowrap;

    font-size:13px;
}

.online-dot{

    width:9px;
    height:9px;

    border-radius:50%;

    background:#22c55e;

    box-shadow:
        0 0 0 5px
        rgba(34,197,94,.12);
}

/* =========================================================
   SENTENCE
   ========================================================= */

.sentence-card{

    background:white;

    border-radius:var(--radius);

    padding:20px;

    box-shadow:var(--shadow);

    margin-bottom:20px;
}

.sentence-top{

    display:flex;

    justify-content:space-between;

    color:var(--muted);

    font-size:14px;

    margin-bottom:10px;
}

.sentence{

    min-height:115px;

    background:#f8fafc;

    border:
        2px dashed
        #d8e1e8;

    border-radius:18px;

    padding:18px;

    display:flex;

    flex-wrap:wrap;

    align-content:flex-start;

    gap:8px;

    font-size:23px;

    font-weight:800;
}

.placeholder{

    color:#94a3b8;

    font-size:16px;

    font-weight:500;
}

.word{

    background:#dff5f7;

    color:#075f69;

    padding:
        7px 13px;

    border-radius:13px;

    animation:
        wordIn .18s ease;
}

@keyframes wordIn{

    from{

        transform:scale(.8);

        opacity:0;
    }

    to{

        transform:scale(1);

        opacity:1;
    }
}

.sentence-actions{

    display:flex;

    gap:10px;

    margin-top:14px;
}

.btn{

    border:0;

    border-radius:13px;

    padding:
        12px 18px;

    font-family:inherit;

    font-size:15px;

    font-weight:800;

    cursor:pointer;

    transition:.2s;
}

.btn:hover{

    transform:translateY(-2px);
}

.btn-primary{

    background:var(--primary);

    color:white;

    flex:1;
}

.btn-secondary{

    background:#eef2f6;

    color:#334155;
}

/* =========================================================
   SEARCH
   ========================================================= */

.search-box{

    margin-bottom:16px;

    position:relative;
}

.search{

    width:100%;

    border:
        1px solid
        var(--border);

    background:white;

    border-radius:16px;

    padding:
        14px
        45px
        14px
        15px;

    font-family:inherit;

    font-size:16px;

    outline:none;

    box-shadow:
        0 5px 18px
        rgba(15,23,42,.04);
}

.search:focus{

    border-color:var(--primary);

    box-shadow:
        0 0 0 4px
        rgba(8,127,140,.10);
}

.search-icon{

    position:absolute;

    right:15px;

    top:50%;

    transform:translateY(-50%);

    font-size:20px;
}

/* =========================================================
   CATEGORIES
   ========================================================= */

.categories{

    display:flex;

    gap:9px;

    overflow-x:auto;

    padding:
        2px
        2px
        13px;

    scrollbar-width:thin;
}

.category{

    flex-shrink:0;

    padding:
        10px 16px;

    border-radius:50px;

    border:
        1px solid
        var(--border);

    background:white;

    color:#475569;

    font-family:inherit;

    font-weight:800;

    cursor:pointer;

    transition:.2s;
}

.category.active{

    background:var(--primary);

    color:white;

    border-color:var(--primary);

    box-shadow:
        0 5px 15px
        rgba(8,127,140,.20);
}

/* =========================================================
   AAC CARDS
   ========================================================= */

.cards{

    display:grid;

    grid-template-columns:
        repeat(
            auto-fit,
            minmax(145px,1fr)
        );

    gap:13px;
}

.aac-card{

    min-height:145px;

    background:white;

    border:
        1px solid
        var(--border);

    border-radius:20px;

    padding:15px;

    display:flex;

    flex-direction:column;

    align-items:center;

    justify-content:center;

    gap:7px;

    font-family:inherit;

    cursor:pointer;

    box-shadow:
        0 5px 18px
        rgba(15,23,42,.05);

    transition:.2s;

    color:var(--text);
}

.aac-card:hover{

    transform:translateY(-5px);

    border-color:
        rgba(8,127,140,.35);

    box-shadow:var(--shadow);
}

.aac-card:active{

    transform:scale(.95);
}

.card-icon{

    font-size:40px;

    line-height:1;
}

.card-name{

    font-size:17px;

    font-weight:900;
}

.card-type{

    color:var(--muted);

    font-size:11px;
}

/* =========================================================
   QUICK SENTENCES
   ========================================================= */

.quick{

    margin-top:35px;
}

.quick h2{

    font-size:21px;

    margin-bottom:14px;
}

.quick-grid{

    display:grid;

    grid-template-columns:
        repeat(
            auto-fit,
            minmax(210px,1fr)
        );

    gap:12px;
}

.quick-card{

    background:white;

    border:
        1px solid
        var(--border);

    border-radius:18px;

    padding:16px;

    display:flex;

    align-items:center;

    gap:12px;

    font-family:inherit;

    font-size:17px;

    font-weight:800;

    color:var(--text);

    cursor:pointer;

    transition:.2s;

    text-align:right;
}

.quick-card:hover{

    transform:translateY(-3px);

    box-shadow:var(--shadow);
}

.quick-icon{

    font-size:29px;
}

/* =========================================================
   ACCESSIBILITY
   ========================================================= */

.accessibility{

    margin-top:35px;

    background:
        linear-gradient(
            135deg,
            #0f172a,
            #1e293b
        );

    color:white;

    border-radius:24px;

    padding:22px;
}

.accessibility h2{

    font-size:20px;

    margin-bottom:12px;
}

.accessibility-grid{

    display:grid;

    grid-template-columns:
        repeat(
            auto-fit,
            minmax(160px,1fr)
        );

    gap:10px;
}

.access-btn{

    padding:13px;

    border-radius:13px;

    border:
        1px solid
        rgba(255,255,255,.12);

    background:
        rgba(255,255,255,.08);

    color:white;

    font-family:inherit;

    font-weight:700;

    cursor:pointer;
}

/* =========================================================
   FOOTER
   ========================================================= */

.footer{

    text-align:center;

    background:white;

    border-top:
        1px solid
        var(--border);

    padding:25px;

    color:var(--muted);

    font-size:13px;

    display:flex;

    flex-direction:column;

    gap:5px;
}

.footer strong{

    color:var(--primary);

    font-size:15px;
}

/* =========================================================
   TOAST
   ========================================================= */

.toast{

    position:fixed;

    bottom:25px;

    left:50%;

    transform:
        translate(-50%,20px);

    background:#0f172a;

    color:white;

    padding:
        12px 18px;

    border-radius:13px;

    opacity:0;

    pointer-events:none;

    transition:.3s;

    z-index:9999;

    font-size:14px;

    box-shadow:var(--shadow);
}

.toast.show{

    opacity:1;

    transform:
        translate(-50%,0);
}

/* =========================================================
   MOBILE
   ========================================================= */

@media(max-width:600px){

    .header{

        padding:
            9px 12px;
    }

    .logo{

        width:44px;
        height:44px;

        font-size:23px;
    }

    .brand-title{

        font-size:18px;
    }

    .brand-subtitle{

        font-size:10px;
    }

    .container{

        width:
            calc(100% - 18px);

        margin-top:15px;
    }

    .hero{

        padding:19px;

        flex-direction:column;

        align-items:flex-start;
    }

    .hero h1{

        font-size:27px;
    }

    .sentence{

        min-height:125px;

        font-size:20px;
    }

    .sentence-actions{

        flex-direction:column;
    }

    .btn{

        width:100%;
    }

    .cards{

        grid-template-columns:
            repeat(2,1fr);

        gap:9px;
    }

    .aac-card{

        min-height:130px;

        padding:10px;
    }

    .card-icon{

        font-size:34px;
    }

    .card-name{

        font-size:15px;
    }

    .quick-grid{

        grid-template-columns:1fr;
    }
}

/* =========================================================
   LARGE TEXT MODE
   ========================================================= */

body.large-text .card-name{

    font-size:21px;
}

body.large-text .sentence{

    font-size:29px;
}

body.large-text .quick-card{

    font-size:21px;
}

</style>
</head>

<body>

<!-- =======================================================
     HEADER
     ======================================================= -->

<header class="header">

<div class="brand">

<div class="logo">
💎
</div>

<div>

<div class="brand-title">
نگین AAC
</div>

<span class="brand-subtitle">
هر کودک، یک نگین
</span>

</div>

</div>

<div class="header-buttons">

<button
class="header-btn"
id="largeText"
title="اندازه متن">
🔠
</button>

<button
class="header-btn"
id="clearBtn"
title="پاک کردن جمله">
🗑️
</button>

<button
class="header-btn"
id="speakTop"
title="خواندن جمله">
🔊
</button>

</div>

</header>


<!-- =======================================================
     MAIN
     ======================================================= -->

<main class="container">


<!-- HERO -->

<section class="hero">

<div>

<div class="hero-label">
مرکز آموزشی و توانبخشی نگین
</div>

<h1>
نگین AAC
</h1>

<p>
ابزار ساده و قابل دسترس برای ارتباط بهتر
</p>

</div>

<div class="online">

<span class="online-dot"></span>

آماده استفاده

</div>

</section>


<!-- SENTENCE -->

<section class="sentence-card">

<div class="sentence-top">

<span>
جمله من
</span>

<span id="wordCount">
۰ کلمه
</span>

</div>

<div
id="sentence"
class="sentence">

<span class="placeholder">

برای ساختن جمله،
یک کلمه انتخاب کنید.

</span>

</div>

<div class="sentence-actions">

<button
class="btn btn-secondary"
id="deleteLast">

⌫ حذف آخرین کلمه

</button>

<button
class="btn btn-primary"
id="speakBtn">

🔊 خواندن جمله

</button>

</div>

</section>


<!-- SEARCH -->

<div class="search-box">

<span class="search-icon">
🔎
</span>

<input
id="search"
class="search"
type="search"
placeholder="جستجوی کلمه..."
autocomplete="off">

</div>


<!-- CATEGORIES -->

<section class="categories">

<button
class="category active"
data-category="all">
✨ همه
</button>

<button
class="category"
data-category="needs">
🙏 نیازها
</button>

<button
class="category"
data-category="feelings">
❤️ احساسات
</button>

<button
class="category"
data-category="people">
👨‍👩‍👧 افراد
</button>

<button
class="category"
data-category="places">
📍 مکان‌ها
</button>

<button
class="category"
data-category="activities">
🎮 فعالیت‌ها
</button>

<button
class="category"
data-category="social">
💬 اجتماعی
</button>

</section>


<!-- CARDS -->

<section
id="cards"
class="cards">
</section>


<!-- QUICK SENTENCES -->

<section class="quick">

<h2>
⚡ جمله‌های سریع
</h2>

<div class="quick-grid">

<button
class="quick-card"
data-text="من آب می‌خواهم">

<span class="quick-icon">
💧
</span>

<span>
من آب می‌خواهم
</span>

</button>


<button
class="quick-card"
data-text="من گرسنه هستم">

<span class="quick-icon">
🍎
</span>

<span>
من گرسنه هستم
</span>

</button>


<button
class="quick-card"
data-text="من خسته هستم">

<span class="quick-icon">
😴
</span>

<span>
من خسته هستم
</span>

</button>


<button
class="quick-card"
data-text="لطفاً کمکم کنید">

<span class="quick-icon">
🆘
</span>

<span>
لطفاً کمکم کنید
</span>

</button>


<button
class="quick-card"
data-text="من خوشحال هستم">

<span class="quick-icon">
😊
</span>

<span>
من خوشحال هستم
</span>

</button>


<button
class="quick-card"
data-text="من به خانه می‌روم">

<span class="quick-icon">
🏠
</span>

<span>
من به خانه می‌روم
</span>

</button>

</div>

</section>


<!-- ACCESSIBILITY -->

<section class="accessibility">

<h2>
♿ تنظیمات دسترسی
</h2>

<div class="accessibility-grid">

<button
class="access-btn"
id="repeatSpeech">

🔊 تکرار صدا
</button>

<button
class="access-btn"
id="slowSpeech">

🐢 صدای آهسته
</button>

<button
class="access-btn"
id="normalSpeech">

▶️ سرعت عادی
</button>

<button
class="access-btn"
id="stopSpeech">

⏹ توقف صدا
</button>

</div>

</section>

</main>


<!-- FOOTER -->

<footer class="footer">

<strong>
💎 مرکز آموزشی و توانبخشی نگین
</strong>

<span>
نگین AAC — هر کودک، یک نگین
</span>

<span>
نسخه 1.0
</span>

</footer>


<div
id="toast"
class="toast">
عملیات انجام شد
</div>


<script>

/* =========================================================
   Negin AAC JavaScript
   ========================================================= */


/* -------------------------
   WORD DATABASE
------------------------- */

const words = [

/* NEEDS */

{
text:"آب",
icon:"💧",
category:"needs"
},

{
text:"غذا",
icon:"🍎",
category:"needs"
},

{
text:"کمک",
icon:"🆘",
category:"needs"
},

{
text:"استراحت",
icon:"🛌",
category:"needs"
},

{
text:"دستشویی",
icon:"🚻",
category:"needs"
},

{
text:"لباس",
icon:"👕",
category:"needs"
},

{
text:"خواب",
icon:"😴",
category:"needs"
},

{
text:"گرسنه",
icon:"🍽️",
category:"needs"
},

{
text:"تشنه",
icon:"🥤",
category:"needs"
},

{
text:"درد",
icon:"🤕",
category:"needs"
},


/* FEELINGS */

{
text:"خوشحال",
icon:"😊",
category:"feelings"
},

{
text:"غمگین",
icon:"😢",
category:"feelings"
},

{
text:"عصبانی",
icon:"😠",
category:"feelings"
},

{
text:"خسته",
icon:"😴",
category:"feelings"
},

{
text:"ترسیده",
icon:"😨",
category:"feelings"
},

{
text:"نگران",
icon:"😟",
category:"feelings"
},

{
text:"دوست دارم",
icon:"❤️",
category:"feelings"
},

{
text:"دوست ندارم",
icon:"💔",
category:"feelings"
},


/* PEOPLE */

{
text:"مادر",
icon:"👩",
category:"people"
},

{
text:"پدر",
icon:"👨",
category:"people"
},

{
text:"برادر",
icon:"👦",
category:"people"
},

{
text:"خواهر",
icon:"👧",
category:"people"
},

{
text:"معلم",
icon:"👩‍🏫",
category:"people"
},

{
text:"دوست",
icon:"🧑‍🤝‍🧑",
category:"people"
},

{
text:"دکتر",
icon:"👨‍⚕️",
category:"people"
},


/* PLACES */

{
text:"خانه",
icon:"🏠",
category:"places"
},

{
text:"مکتب",
icon:"🏫",
category:"places"
},

{
text:"شفاخانه",
icon:"🏥",
category:"places"
},

{
text:"پارک",
icon:"🌳",
category:"places"
},

{
text:"بازار",
icon:"🛒",
category:"places"
},

{
text:"مسجد",
icon:"🕌",
category:"places"
},


/* ACTIVITIES */

{
text:"بازی",
icon:"🎮",
category:"activities"
},

{
text:"موسیقی",
icon:"🎵",
category:"activities"
},

{
text:"کتاب",
icon:"📚",
category:"activities"
},

{
text:"تلویزیون",
icon:"📺",
category:"activities"
},

{
text:"نقاشی",
icon:"🎨",
category:"activities"
},

{
text:"راه رفتن",
icon:"🚶",
category:"activities"
},


/* SOCIAL */

{
text:"سلام",
icon:"👋",
category:"social"
},

{
text:"خوب",
icon:"👍",
category:"social"
},

{
text:"بله",
icon:"✅",
category:"social"
},

{
text:"نه",
icon:"❌",
category:"social"
},

{
text:"تشکر",
icon:"🙏",
category:"social"
},

{
text:"لطفاً",
icon:"🤲",
category:"social"
},

{
text:"ببخشید",
icon:"🙇",
category:"social"
},

{
text:"خداحافظ",
icon:"👋",
category:"social"
}

];


/* -------------------------
   VARIABLES
------------------------- */

let sentenceWords = [];

let currentCategory = "all";

let speechRate = .85;

let lastSpokenText = "";


/* -------------------------
   ELEMENTS
------------------------- */

const cards =
document.getElementById("cards");

const sentence =
document.getElementById("sentence");

const wordCount =
document.getElementById("wordCount");

const search =
document.getElementById("search");

const toast =
document.getElementById("toast");


/* -------------------------
   CATEGORY NAMES
------------------------- */

const categoryNames = {

needs:"نیازها",

feelings:"احساسات",

people:"افراد",

places:"مکان‌ها",

activities:"فعالیت‌ها",

social:"اجتماعی"

};


/* -------------------------
   PERSIAN NUMBERS
------------------------- */

function persianNumber(number){

return String(number)
.replace(
    /\d/g,
    digit =>
    "۰۱۲۳۴۵۶۷۸۹"[digit]
);

}


/* -------------------------
   SHOW TOAST
------------------------- */

function showToast(message){

toast.textContent =
message;

toast.classList.add("show");

setTimeout(
()=>{
toast.classList.remove("show");
},
1800
);

}


/* -------------------------
   RENDER WORDS
------------------------- */

function renderWords(){

cards.innerHTML = "";

const query =
search.value.trim().toLowerCase();

let filtered =
words.filter(item=>{

const categoryMatch =
currentCategory === "all"
||
item.category === currentCategory;

const searchMatch =
!query
||
item.text
.toLowerCase()
.includes(query);

return categoryMatch && searchMatch;

});


if(filtered.length === 0){

cards.innerHTML = `

<div style="
grid-column:1/-1;
background:white;
padding:30px;
border-radius:20px;
text-align:center;
color:#64748b;
">

🔎 کلمه‌ای پیدا نشد.

</div>

`;

return;

}


filtered.forEach(item=>{

const button =
document.createElement("button");

button.className =
"aac-card";

button.innerHTML = `

<span class="card-icon">
${item.icon}
</span>

<span class="card-name">
${item.text}
</span>

<span class="card-type">
${categoryNames[item.category]}
</span>

`;

button.addEventListener(
"click",
()=>{

addWord(item.text);

}
);

cards.appendChild(button);

});

}


/* -------------------------
   ADD WORD
------------------------- */

function addWord(word){

sentenceWords.push(word);

renderSentence();

}


/* -------------------------
   RENDER SENTENCE
------------------------- */

function renderSentence(){

sentence.innerHTML = "";

if(sentenceWords.length === 0){

sentence.innerHTML = `

<span class="placeholder">

برای ساختن جمله،
یک کلمه انتخاب کنید.

</span>

`;

}

else{

sentenceWords.forEach(
(word,index)=>{

const element =
document.createElement("span");

element.className =
"word";

element.textContent =
word;

element.title =
"برای حذف این کلمه کلیک کنید";

element.style.cursor =
"pointer";

element.addEventListener(
"click",
()=>{

sentenceWords.splice(
index,
1
);

renderSentence();

}
);

sentence.appendChild(
element
);

}

);

}

wordCount.textContent =

persianNumber(
sentenceWords.length
)
+
" کلمه";

}


/* -------------------------
   GET SENTENCE
------------------------- */

function getSentence(){

return sentenceWords.join(" ");

}


/* -------------------------
   SPEECH
------------------------- */

function speak(text){

if(!text.trim()){

showToast(
"ابتدا یک جمله بسازید."
);

return;

}

if(
!("speechSynthesis" in window)
){

showToast(
"تبدیل متن به صدا در این دستگاه پشتیبانی نمی‌شود."
);

return;

}

speechSynthesis.cancel();

const utterance =
new SpeechSynthesisUtterance(
text
);

utterance.lang =
"fa-AF";

utterance.rate =
speechRate;

utterance.pitch =
1;

lastSpokenText =
text;

speechSynthesis.speak(
utterance
);

}


/* -------------------------
   CLEAR
------------------------- */

function clearSentence(){

sentenceWords = [];

renderSentence();

showToast(
"جمله پاک شد."
);

}


/* -------------------------
   DELETE LAST
------------------------- */

function deleteLast(){

if(
sentenceWords.length === 0
){

return;

}

sentenceWords.pop();

renderSentence();

}


/* -------------------------
   CATEGORIES
------------------------- */

document
.querySelectorAll(".category")
.forEach(button=>{

button.addEventListener(
"click",
()=>{

document
.querySelectorAll(".category")
.forEach(
item =>
item.classList.remove(
"active"
)
);

button.classList.add(
"active"
);

currentCategory =
button.dataset.category;

renderWords();

}
);

});


/* -------------------------
   SEARCH
------------------------- */

search.addEventListener(
"input",
renderWords
);


/* -------------------------
   BUTTONS
------------------------- */

document
.getElementById("speakBtn")
.addEventListener(
"click",
()=>{

speak(
getSentence()
);

}
);


document
.getElementById("speakTop")
.addEventListener(
"click",
()=>{

speak(
getSentence()
);

}
);


document
.getElementById("clearBtn")
.addEventListener(
"click",
clearSentence
);


document
.getElementById("deleteLast")
.addEventListener(
"click",
deleteLast
);


/* -------------------------
   QUICK SENTENCES
------------------------- */

document
.querySelectorAll(".quick-card")
.forEach(button=>{

button.addEventListener(
"click",
()=>{

const text =
button.dataset.text;

sentenceWords =
text.split(" ");

renderSentence();

speak(text);

}
);

});


/* -------------------------
   ACCESSIBILITY
------------------------- */

document
.getElementById("largeText")
.addEventListener(
"click",
()=>{

document.body
.classList.toggle(
"large-text"
);

showToast(
"اندازه متن تغییر کرد."
);

}
);


/* -------------------------
   REPEAT
------------------------- */

document
.getElementById("repeatSpeech")
.addEventListener(
"click",
()=>{

speak(
lastSpokenText ||
getSentence()
);

}
);


/* -------------------------
   SLOW
------------------------- */

document
.getElementById("slowSpeech")
.addEventListener(
"click",
()=>{

speechRate = .55;

showToast(
"سرعت صدا آهسته شد."
);

}
);


/* -------------------------
   NORMAL
------------------------- */

document
.getElementById("normalSpeech")
.addEventListener(
"click",
()=>{

speechRate = .85;

showToast(
"سرعت صدا به حالت عادی برگشت."
);

}
);


/* -------------------------
   STOP
------------------------- */

document
.getElementById("stopSpeech")
.addEventListener(
"click",
()=>{

if(
"speechSynthesis"
in window
){

speechSynthesis.cancel();

}

showToast(
"صدا متوقف شد."
);

}
);


/* -------------------------
   KEYBOARD
------------------------- */

document.addEventListener(
"keydown",
event=>{

if(
event.key === "Backspace"
&&
document.activeElement !== search
){

deleteLast();

}

if(
event.key === "Escape"
){

clearSentence();

}

}
);


/* -------------------------
   INITIALIZE
------------------------- */

renderWords();

renderSentence();


/* =========================================================
   PWA SERVICE WORKER
   =========================================================

   Service Worker فقط در فایل جداگانه قابل ثبت است.
   این نسخه تک‌فایلی بدون آن نیز کاملاً به‌صورت وب اجرا می‌شود.

   ========================================================= */

</script>

</body>
</html>
