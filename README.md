import os, zipfile, textwrap, json

root = "/mnt/data/negin-aac"
zip_path = "/mnt/data/negin-aac-complete.zip"

files = {
"www/index.html": """<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <meta name="theme-color" content="#007f8b">
  <meta name="description" content="نگین AAC؛ سامانه ارتباط جایگزین و افزوده برای کودکان">
  <title>نگین AAC</title>
  <link rel="manifest" href="manifest.json">
  <link rel="stylesheet" href="style.css">
</head>
<body>
<header class="header">
  <div class="brand">
    <div class="logo">💎</div>
    <div>
      <h1>نگین AAC</h1>
      <p>هر کودک، یک صدا؛ هر صدا، یک نگین</p>
    </div>
  </div>
</header>

<main class="container">
  <section class="status-card">
    <span id="connectionStatus">🟢 آماده</span>
    <span>نسخه 1.0</span>
  </section>

  <section class="sentence-box">
    <div id="sentence" class="sentence" aria-live="polite">جمله خود را بسازید</div>
    <div class="sentence-actions">
      <button onclick="speakSentence()" class="speak-button">🔊 پخش</button>
      <button onclick="clearSentence()" class="clear-button">🗑️ پاک</button>
    </div>
  </section>

  <section class="search-box">
    <input id="searchInput" type="search" placeholder="🔎 جستجوی کلمه..." oninput="searchSymbols()" aria-label="جستجوی کلمه">
  </section>

  <section class="categories" aria-label="دسته‌بندی‌ها">
    <button onclick="filterCategory('همه')">🏠 همه</button>
    <button onclick="filterCategory('نوشیدنی')">💧 نوشیدنی</button>
    <button onclick="filterCategory('غذا')">🍎 غذا</button>
    <button onclick="filterCategory('افراد')">👨‍👩‍👧 افراد</button>
    <button onclick="filterCategory('نیازها')">🚻 نیازها</button>
    <button onclick="filterCategory('احساسات')">😊 احساسات</button>
    <button onclick="filterCategory('سلامت')">🩺 سلامت</button>
    <button onclick="filterCategory('مکان‌ها')">📍 مکان‌ها</button>
  </section>

  <section id="aacGrid" class="aac-grid" aria-label="واژه‌های ارتباطی"></section>

  <section class="quick-actions">
    <button onclick="showEmergency()">🚨 کمک فوری</button>
    <button onclick="showFavorites()">⭐ علاقه‌مندی‌ها</button>
    <button onclick="showRecent()">🕘 اخیر</button>
  </section>
</main>

<footer>
  <p>💎 مرکز آموزشی نگین</p>
  <small>Negin AAC</small>
</footer>

<script src="app.js"></script>
</body>
</html>
""",
"www/style.css": """* {
  box-sizing: border-box;
  -webkit-tap-highlight-color: transparent;
}

html {
  direction: rtl;
  scroll-behavior: smooth;
}

body {
  margin: 0;
  font-family: "Tajawal", "Noto Sans Arabic", Arial, sans-serif;
  background: linear-gradient(135deg, #f7fbfc, #eef7f8);
  color: #17212b;
  min-height: 100vh;
}

button, input { font-family: inherit; }
button { touch-action: manipulation; }

.header {
  padding: 18px;
  background: linear-gradient(135deg, #007f8b, #00b7c7);
  color: white;
  box-shadow: 0 4px 20px rgba(0,0,0,.12);
}

.brand {
  display: flex;
  align-items: center;
  gap: 14px;
  max-width: 950px;
  margin: auto;
}

.logo {
  width: 64px;
  height: 64px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  border-radius: 20px;
  font-size: 38px;
  box-shadow: 0 5px 15px rgba(0,0,0,.15);
}

.header h1 { margin: 0; font-size: 28px; }
.header p { margin: 5px 0 0; opacity: .92; }

.container {
  max-width: 950px;
  margin: auto;
  padding: 15px;
}

.status-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: white;
  padding: 12px 16px;
  margin-bottom: 12px;
  border-radius: 18px;
  box-shadow: 0 4px 15px rgba(0,0,0,.06);
  font-weight: bold;
}

.sentence-box {
  background: white;
  border-radius: 24px;
  padding: 18px;
  margin-bottom: 15px;
  box-shadow: 0 5px 20px rgba(0,0,0,.08);
}

.sentence {
  min-height: 70px;
  display: flex;
  align-items: center;
  padding: 14px;
  font-size: 25px;
  font-weight: bold;
  border-radius: 17px;
  background: #f3f8f9;
  overflow-wrap: anywhere;
}

.sentence-actions {
  display: flex;
  gap: 10px;
  margin-top: 12px;
}

.sentence-actions button {
  flex: 1;
  border: none;
  border-radius: 16px;
  padding: 15px;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
}

.speak-button { background: #00a884; color: white; }
.clear-button { background: #eeeeee; color: #222; }

.search-box { margin-bottom: 12px; }

.search-box input {
  width: 100%;
  border: none;
  outline: none;
  padding: 16px;
  border-radius: 18px;
  font-size: 17px;
  background: white;
  box-shadow: 0 4px 15px rgba(0,0,0,.06);
}

.categories {
  display: flex;
  gap: 8px;
  overflow-x: auto;
  padding-bottom: 14px;
}

.categories button {
  white-space: nowrap;
  border: none;
  border-radius: 15px;
  padding: 12px 16px;
  background: white;
  font-size: 15px;
  box-shadow: 0 3px 12px rgba(0,0,0,.06);
  cursor: pointer;
}

.aac-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
}

.symbol {
  min-height: 150px;
  border: none;
  border-radius: 22px;
  background: white;
  box-shadow: 0 5px 16px rgba(0,0,0,.08);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 9px;
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
  transition: transform .12s, box-shadow .12s;
}

.symbol:active { transform: scale(.93); }
.symbol-emoji { font-size: 55px; }

.quick-actions {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  margin-top: 18px;
}

.quick-actions button {
  border: none;
  padding: 15px;
  border-radius: 16px;
  background: white;
  font-size: 15px;
  font-weight: bold;
  box-shadow: 0 4px 15px rgba(0,0,0,.06);
  cursor: pointer;
}

.empty {
  grid-column: 1 / -1;
  text-align: center;
  background: white;
  padding: 30px;
  border-radius: 20px;
  font-size: 18px;
}

footer {
  text-align: center;
  padding: 25px;
  color: #65727b;
}

button:focus-visible, input:focus-visible {
  outline: 3px solid #ffb300;
  outline-offset: 3px;
}

@media (max-width: 600px) {
  .aac-grid { grid-template-columns: repeat(2, 1fr); }
  .quick-actions { grid-template-columns: 1fr; }
  .symbol { min-height: 145px; }
  .sentence { font-size: 22px; }
  .header h1 { font-size: 24px; }
}

@media (min-width: 1000px) {
  .aac-grid { grid-template-columns: repeat(5, 1fr); }
}
""",
"www/app.js": """const symbols = [
  {id:"water",title:"آب",category:"نوشیدنی",emoji:"💧"},
  {id:"milk",title:"شیر",category:"نوشیدنی",emoji:"🥛"},
  {id:"tea",title:"چای",category:"نوشیدنی",emoji:"🍵"},
  {id:"juice",title:"آبمیوه",category:"نوشیدنی",emoji:"🧃"},
  {id:"food",title:"غذا",category:"غذا",emoji:"🍲"},
  {id:"bread",title:"نان",category:"غذا",emoji:"🍞"},
  {id:"rice",title:"برنج",category:"غذا",emoji:"🍚"},
  {id:"apple",title:"سیب",category:"غذا",emoji:"🍎"},
  {id:"mother",title:"مادر",category:"افراد",emoji:"👩"},
  {id:"father",title:"پدر",category:"افراد",emoji:"👨"},
  {id:"brother",title:"برادر",category:"افراد",emoji:"👦"},
  {id:"sister",title:"خواهر",category:"افراد",emoji:"👧"},
  {id:"teacher",title:"معلم",category:"افراد",emoji:"👩‍🏫"},
  {id:"toilet",title:"تشناب",category:"نیازها",emoji:"🚻"},
  {id:"sleep",title:"خواب",category:"نیازها",emoji:"😴"},
  {id:"help",title:"کمک",category:"نیازها",emoji:"🆘"},
  {id:"yes",title:"بلی",category:"نیازها",emoji:"✅"},
  {id:"no",title:"نخیر",category:"نیازها",emoji:"❌"},
  {id:"happy",title:"خوشحال",category:"احساسات",emoji:"😊"},
  {id:"sad",title:"غمگین",category:"احساسات",emoji:"😢"},
  {id:"angry",title:"عصبانی",category:"احساسات",emoji:"😡"},
  {id:"afraid",title:"ترسیده",category:"احساسات",emoji:"😨"},
  {id:"pain",title:"درد",category:"سلامت",emoji:"🤕"},
  {id:"doctor",title:"دکتر",category:"سلامت",emoji:"👨‍⚕️"},
  {id:"medicine",title:"دوا",category:"سلامت",emoji:"💊"},
  {id:"hospital",title:"شفاخانه",category:"سلامت",emoji:"🏥"},
  {id:"home",title:"خانه",category:"مکان‌ها",emoji:"🏠"},
  {id:"school",title:"مکتب",category:"مکان‌ها",emoji:"🏫"},
  {id:"park",title:"پارک",category:"مکان‌ها",emoji:"🌳"}
];

let sentence = [];
let currentCategory = "همه";

function loadList(key) {
  try { return JSON.parse(localStorage.getItem(key) || "[]"); }
  catch { return []; }
}

function saveList(key, value) {
  localStorage.setItem(key, JSON.stringify(value));
}

let favorites = loadList("neginFavorites");
let recent = loadList("neginRecent");

function renderSymbols(list = symbols) {
  const grid = document.getElementById("aacGrid");
  grid.innerHTML = "";

  if (list.length === 0) {
    grid.innerHTML = '<div class="empty">کلمه‌ای پیدا نشد.</div>';
    return;
  }

  list.forEach(symbol => {
    const button = document.createElement("button");
    button.className = "symbol";
    button.type = "button";
    button.setAttribute("aria-label", symbol.title);
    button.innerHTML = `<span class="symbol-emoji" aria-hidden="true">${symbol.emoji}</span><span>${symbol.title}</span>`;
    button.onclick = () => addWord(symbol);
    button.ondblclick = () => toggleFavorite(symbol);
    grid.appendChild(button);
  });
}

function addWord(symbol) {
  sentence.push(symbol.title);
  updateSentence();
  speak(symbol.title);
  addRecent(symbol);
}

function updateSentence() {
  const element = document.getElementById("sentence");
  element.textContent = sentence.length ? sentence.join(" ") : "جمله خود را بسازید";
}

function speak(text) {
  if (!("speechSynthesis" in window)) {
    alert("دستگاه شما از پخش صدا پشتیبانی نمی‌کند.");
    return;
  }
  speechSynthesis.cancel();
  const utterance = new SpeechSynthesisUtterance(text);
  utterance.lang = "fa-IR";
  utterance.rate = 0.75;
  utterance.pitch = 1;
  speechSynthesis.speak(utterance);
}

function speakSentence() {
  if (sentence.length) speak(sentence.join(" "));
}

function clearSentence() {
  sentence = [];
  updateSentence();
}

function filterCategory(category) {
  currentCategory = category;
  searchSymbols();
}

function searchSymbols() {
  const query = document.getElementById("searchInput").value.trim().toLowerCase();
  let list = currentCategory === "همه"
    ? symbols
    : symbols.filter(symbol => symbol.category === currentCategory);

  if (query) {
    list = list.filter(symbol => symbol.title.toLowerCase().includes(query));
  }
  renderSymbols(list);
}

function toggleFavorite(symbol) {
  const exists = favorites.some(item => item.id === symbol.id);
  favorites = exists
    ? favorites.filter(item => item.id !== symbol.id)
    : [...favorites, symbol];
  saveList("neginFavorites", favorites);
}

function addRecent(symbol) {
  recent = recent.filter(item => item.id !== symbol.id);
  recent.unshift(symbol);
  recent = recent.slice(0, 10);
  saveList("neginRecent", recent);
}

function showFavorites() {
  if (!favorites.length) {
    alert("هنوز کلمه‌ای به علاقه‌مندی‌ها اضافه نشده است. برای افزودن، روی یک کلمه دوبار لمس کنید.");
    return;
  }
  currentCategory = "همه";
  renderSymbols(favorites);
}

function showRecent() {
  if (!recent.length) {
    alert("هنوز کلمه‌ای استفاده نشده است.");
    return;
  }
  currentCategory = "همه";
  renderSymbols(recent);
}

function showEmergency() {
  sentence = ["کمک", "لطفاً", "من به کمک نیاز دارم"];
  updateSentence();
  speak("کمک لطفاً من به کمک نیاز دارم");
}

function updateConnection() {
  const element = document.getElementById("connectionStatus");
  element.textContent = navigator.onLine ? "🟢 آنلاین" : "🟠 حالت آفلاین";
}

window.addEventListener("online", updateConnection);
window.addEventListener("offline", updateConnection);

if ("serviceWorker" in navigator) {
  window.addEventListener("load", () => {
    navigator.serviceWorker.register("sw.js")
      .catch(error => console.log("Service Worker:", error));
  });
}

renderSymbols();
updateConnection();
""",
"www/manifest.json": """{
  "name": "نگین AAC",
  "short_name": "نگین AAC",
  "description": "سامانه ارتباط جایگزین و افزوده برای کودکان",
  "start_url": "index.html",
  "display": "standalone",
  "background_color": "#f7fbfc",
  "theme_color": "#007f8b",
  "orientation": "portrait",
  "lang": "fa",
  "dir": "rtl",
  "icons": []
}
""",
"www/sw.js": """const CACHE_NAME = "negin-aac-v1";

const FILES = [
  "index.html",
  "style.css",
  "app.js",
  "manifest.json"
];

self.addEventListener("install", event => {
  event.waitUntil(
    caches.open(CACHE_NAME).then(cache => cache.addAll(FILES))
  );
  self.skipWaiting();
});

self.addEventListener("activate", event => {
  event.waitUntil(
    caches.keys().then(keys =>
      Promise.all(
        keys.filter(key => key !== CACHE_NAME).map(key => caches.delete(key))
      )
    )
  );
  self.clients.claim();
});

self.addEventListener("fetch", event => {
  event.respondWith(
    caches.match(event.request).then(cached => cached || fetch(event.request))
  );
});
""",
"config.xml": """<?xml version="1.0" encoding="UTF-8"?>
<widget id="org.negin.aac" version="1.0.0"
  xmlns="http://www.w3.org/ns/widgets"
  xmlns:cdv="http://cordova.apache.org/ns/1.0">

  <name>نگین AAC</name>
  <description>سامانه ارتباط جایگزین و افزوده نگین</description>
  <author email="qaishaidari.smart@gmail.com">Qais Haidari</author>
  <content src="index.html" />
  <access origin="*" />
  <allow-navigation href="*" />

  <preference name="Orientation" value="portrait" />
  <preference name="Fullscreen" value="false" />
  <preference name="DisallowOverscroll" value="true" />
  <preference name="AndroidInsecureFileModeEnabled" value="true" />

  <platform name="android">
    <preference name="android-minSdkVersion" value="24" />
    <preference name="android-targetSdkVersion" value="36" />
    <preference name="android-compileSdkVersion" value="36" />
  </platform>
</widget>
""",
"package.json": """{
  "name": "negin-aac",
  "version": "1.0.0",
  "description": "Negin AAC - Dari Augmentative and Alternative Communication",
  "main": "index.js",
  "scripts": {
    "build": "cordova build android",
    "android": "cordova build android"
  },
  "author": "Qais Haidari",
  "license": "MIT",
  "devDependencies": {
    "cordova": "^13.0.0",
    "cordova-android": "15.1.0"
  }
}
""",
".github/workflows/build-apk.yml": """name: 💎 Build Negin AAC APK

on:
  push:
    branches:
      - main
      - master
  workflow_dispatch:

jobs:
  build:
    name: 📱 Build Android APK
    runs-on: ubuntu-latest

    steps:
      - name: 📥 Checkout repository
        uses: actions/checkout@v4

      - name: ☕ Setup Java 17
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: "17"

      - name: 🟢 Setup Node.js 22
        uses: actions/setup-node@v4
        with:
          node-version: "22"
          cache: npm

      - name: 🤖 Setup Android SDK
        uses: android-actions/setup-android@v3

      - name: 📦 Install Android SDK 36
        run: |
          sdkmanager \
            "platform-tools" \
            "platforms;android-36" \
            "build-tools;36.0.0"
          yes | sdkmanager --licenses || true

      - name: 📦 Install dependencies
        run: npm install

      - name: 🤖 Add Cordova Android
        run: npx cordova platform add android@15.1.0

      - name: 🔨 Build APK
        run: npx cordova build android --debug

      - name: 📁 Find APK
        run: |
          find platforms/android/app/build/outputs/apk \
            -type f -name "*.apk" -print

      - name: 📦 Upload APK
        uses: actions/upload-artifact@v4
        with:
          name: negin-aac-debug-apk
          path: platforms/android/app/build/outputs/apk/debug/*.apk
          if-no-files-found: error
""",
"README.md": """# 💎 Negin AAC

## هر کودک، یک صدا؛ هر صدا، یک نگین

نگین AAC یک سامانه ارتباط جایگزین و افزوده (AAC) برای کودکان است که با تمرکز بر زبان دری افغانستان، رابط RTL، دسترسی آسان، Text-to-Speech و حالت آفلاین طراحی شده است.

## امکانات فعلی

- 🇦🇫 زبان دری
- ↔️ رابط RTL
- 🔊 Text-to-Speech
- 🧩 AAC Board
- 🗂 دسته‌بندی واژه‌ها
- 🔎 جستجوی واژه‌ها
- ⭐ علاقه‌مندی‌ها
- 🕘 واژه‌های اخیر
- 🚨 کمک فوری
- 📴 حالت آفلاین
- 📱 ساخت Android APK با Cordova و GitHub Actions
- 🌐 Web/PWA

## ساختار پروژه

```text
negin-aac/
├── www/
│   ├── index.html
│   ├── style.css
│   ├── app.js
│   ├── manifest.json
│   └── sw.js
├── .github/
│   └── workflows/
│       └── build-apk.yml
├── config.xml
├── package.json
└── README.md
```

## ساخت APK

پس از قرار دادن پروژه در GitHub، به بخش Actions بروید و workflow با نام:

**💎 Build Negin AAC APK**

را اجرا کنید. پس از موفقیت، Artifact با نام:

**negin-aac-debug-apk**

در دسترس خواهد بود.

## فناوری

HTML • CSS • JavaScript • PWA • Service Worker • Apache Cordova • GitHub Actions

## توسعه‌های آینده

Firebase Authentication، پروفایل کودک، پنل والدین، پنل درمانگر، اهداف و جلسات درمانی، گزارش پیشرفت، اعلان‌ها، همگام‌سازی ابری، تصاویر AAC، صدای بهتر دری، پیش‌بینی جمله با AI، Switch Access، Bluetooth Switch و Eye Gaze.

## توسعه‌دهنده

Qais Haidari — Negin Educational Center

## License

MIT
"""
}

os.makedirs(root, exist_ok=True)
for rel, content in files.items():
    path = os.path.join(root, rel)
    os.makedirs(os.path.dirname(path), exist_ok=True)
    with open(path, "w", encoding="utf-8", newline="\n") as f:
        f.write(content)

with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for rel in files:
        z.write(os.path.join(root, rel), arcname=os.path.join("negin-aac", rel))

print(f"Created: {zip_path}")
print(f"Files: {len(files)}")
print("ZIP contents:")
with zipfile.ZipFile(zip_path) as z:
    for name in z.namelist():
        print(" -", name)
