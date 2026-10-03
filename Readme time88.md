<div align="center">

🌍 Time88

Le monde entier, sur un globe wireframe vert néon.

</div>

---

👋 Welcome

I've been fascinated by world clocks since I was a kid. My grandfather had one of those wooden ones on the wall — a dial with a dozen little cities etched around the rim, London, New York, Tokyo, each one with its own tiny hand, and I used to stand in front of it and try to figure out what time it was for my uncle in Senegal.

Modern world-clock apps, somehow, made that less interesting. A list of cities in a table. A dropdown. A little pill-shaped row of times that updates once a minute. Functionally fine, emotionally dead.

Time88 is my attempt to make it interesting again.

It's a wireframe globe, drawn in Three.js, floating on a dark grid like something out of an old science terminal. Neon green by default — the shade that used to glow on CRT monitors when the world felt like it was still about to become cyberspace. Around that wireframe sphere, 195 capital cities sit as small white points, each one exactly where it belongs on the planet.

You can drag the globe to spin it, and it keeps slowly rotating on its own when you let go. You can click any capital, and the panel at the bottom tells you what time it is there, right now, updating every second. Or if you'd rather not spin the globe to find Nouakchott, you can just type its name into the search field, press Enter, and it takes you there.

That's the whole app. A globe, a clock, and two colors of neon.

---

<!--
## 📸 Look Inside

<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/time88/raw/main/images/preview-1.png" alt="The wireframe globe with neon green theme" width="100%" />
  <br />
  <sub><b>① The globe, in green</b></sub>
</div>

<br />
<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/time88/raw/main/images/preview-2.png" alt="The blue theme with a city selected" width="100%" />
  <br />
  <sub><b>② Blue theme, city selected</b></sub>
</div>

<br />
<br />

<div align="center">
  <img src="https://github.com/mohamed005cheikh-rgb/time88/raw/main/images/preview-3.png" alt="Searching for a capital" width="100%" />
  <br />
  <sub><b>③ Searching for a capital</b></sub>
</div>
-->

---

✨ What you'll find

A wireframe globe you can actually spin.
The Earth is drawn as a low-opacity wireframe sphere with a thin green cube around it — an axis-aligned bounding box, like a piece of geometry you'd see in a CAD program. Drag anywhere on the screen and the globe rotates with your finger or your mouse. Let go, and it drifts back into a slow, gentle auto-rotation. The motion has easing, so nothing snaps. It feels like a physical object on a stand.

195 capitals, each in its exact place.
Every country's seat of government is on the globe, converted from latitude and longitude into 3D coordinates and pinned as a small white dot. It's not a curated list of a dozen famous cities — it's the whole world. Nouakchott, Ulaanbaatar, Funafuti, Yaren, Apia, Bissau. All of them, sitting quietly on the wireframe, waiting for you to find them.

Click any capital and the clock starts.
Tap a white point on the globe, and the panel at the bottom fills in: the city's name in white with a soft neon glow, and beneath it, a live clock ticking every second in that city's local time. Change to a different city and the clock switches to the new timezone immediately, no reload. It uses the browser's built-in Intl.DateTimeFormat, which means daylight saving is handled correctly, and every timezone in the list is real.

Search for anywhere, by name.
There's an input field at the top of the panel: "TYPE CAPITAL NAME & PRESS ENTER..." Type Paris or Tokyo or Dakar and press Enter. If the name matches a capital, the globe snaps the selection to that city and starts the clock. Exact matches win, then partial matches — so washington finds Washington D.C., and sri finds Sri Jayawardenepura Kotte. If nothing matches, the panel says NOT FOUND and moves on. No apology, no suggestions, no dropdown.

Two themes — the green of a terminal, and its opposite.
The default is the classic phosphor-green of a 1980s terminal: #00ff41, with a faint grid of the same color behind everything. Click BLUE THEME in the top-right and the whole app shifts to a cooler cyan #00d4ff — the globe, the panel, the borders, the text glow, all of it. The button label flips to GREEN THEME to switch back. The choice is not saved; each visit starts green, like a fresh boot.

A terminal panel at the bottom.
Three rows, each marked with a hollow square bracket. SEARCH at the top, EARTH in the middle for the current city's name, TIME at the bottom for the live clock. It sits on a translucent dark rectangle with a green border and a soft glow, and it doesn't move or animate. It's just there, at the bottom of the screen, quietly doing its job.

The globe autospins when you're not touching it.
The moment you release the mouse, a small amount of rotation is added to the target angle every frame — about a quarter-degree per second. Fast enough that you notice the movement, slow enough that it never becomes a distraction. It's the kind of detail that makes the whole thing feel alive rather than static.

Touch, on a phone.
The globe responds to touch exactly the same way as it does to the mouse. One finger to drag, tap to select. The hit detection uses Three.js raycasting with an oversized invisible hit area around each point, so you don't need pixel-perfect aim to select a city on a small screen. It's forgiving in the right way.

---

🧭 How it works

1. Open the file.
One HTML file. The globe loads in a moment, the panel appears at the bottom, and the auto-rotation begins. That's the whole startup.

2. Spin the globe, or click a point.
Drag anywhere on the screen to rotate the Earth. The panel updates as you click a white dot — the city name and its current local time appear in the EARTH and TIME rows.

3. Or search for a city by name.
Type a capital name into the search field. Press Enter. The clock starts for that city, immediately. If the name isn't in the list, the panel returns NOT FOUND.

4. Watch the clock, or come back later.
The time updates every second while the tab is open. When you close it, the app forgets everything — no localStorage, no saved city, no history. Each visit is a fresh look at the world, starting from a gentle default rotation and the green theme.

5. Switch to blue, if you want.
Click BLUE THEME in the top-right. The entire scene — including the Three.js materials — recolors to cyan. Click again to go back to green. Neither is saved.

---

🛠️ A few small helps

"Why doesn't my city show up when I search?"
The list contains capitals only, not every city. Nouakchott is there, but Nouadhibou isn't. Washington D.C. is there, but New York isn't. If the city you're looking for isn't a capital, it won't be found — that's a deliberate limit, so the globe doesn't become a wall of points.

"Some capitals are missing — like La Paz or Amsterdam."
A few countries have multiple capitals, contested capitals, or capitals that are more ceremonial than administrative. This list tries to be inclusive but follows a common convention: the seat of government. Bolivia shows as Sucre (constitutional capital), the Netherlands as Amsterdam (official capital), even though The Hague is where the government actually sits. If you disagree with a choice, the data is a plain array at the top of the script — edit it.

"The time is wrong for one city."
The times come from the browser's own timezone database via Intl.DateTimeFormat, so if a country recently changed its DST rules and your browser is out of date, the time will be off by an hour until you update. Some entries also use a proxy timezone — for example, Astana uses Asia/Almaty because the IANA database changed the canonical zone after the capital was renamed. These are honest, deliberate compromises, not bugs.

"The globe doesn't auto-rotate on my phone."
It should. The auto-rotation runs in the animate() loop, which is always active. If the globe feels stuck, try a slightly longer drag — the animation restarts after you let go, and the initial frame after a touch can feel sluggish on older devices.

"Why does the search field clear when I click it?"
So you can type a new city without having to select-and-delete the old one first. The moment the field gets focus, it empties itself and the panel resets to SELECT A CAPITAL. If you click away without pressing Enter, nothing changes.

"Can I save my favorite city?"
Not in this version. There's no localStorage, no bookmarking, no recent list. The design intent is that you open it, find what you want, and close it — like glancing at a physical globe on a shelf, not opening a weather app you'll come back to. If you want a persistent world clock, that's a different tool.

"The theme resets to green every time."
Correct, and it's deliberate. The green theme is the identity of the app — the phosphor terminal look. The blue is an alternate you can try, but each new visit starts fresh at green so the app always feels like itself.

"Does it work offline?"
Almost. The HTML file itself is entirely self-contained, but Three.js is loaded from a CDN (cdnjs.cloudflare.com). If you're offline when you open the file, the globe won't render — you'll see the panel and the header, but no 3D scene. Download three.min.js and change the <script src=...> line to point at the local copy, and it works fully offline.

"Why are some capital names spelled in English and others with accents?"
Names are in English with standard accents preserved where they exist in the common English form — Bogotá, São Tomé, Malé, Yaoundé. Apostrophes in names like N'Djamena, Saint John's, and Nuku'alofa are kept as typed. The search is case-insensitive and ignores accents only in that it matches the exact stored string. If you can't find a city, try typing just the first few letters — partial matching is supported.

"Can I add more cities?"
Yes. Near the top of the <script> there's a capitalsData array. Each entry is [name, latitude, longitude, timezone]. Add your own, and the globe rebuilds itself on next load. The timezone must be a valid IANA zone (like Europe/Paris or Africa/Nouakchott).

---

<div align="center">

📞 A question, an idea, a bug?

https://img.shields.io/badge/Email-mohamed005cheikh@gmail.com-d14836?style=flat-square&logo=gmail&logoColor=white
https://img.shields.io/badge/WhatsApp-+222_30_73_64_75-25D366?style=flat-square&logo=whatsapp&logoColor=white
https://img.shields.io/badge/GitHub-mohamed005cheikh--rgb-181717?style=flat-square&logo=github

<br />

The whole world, one wireframe at a time.

<sub>© 2026 Mohamed Cheikh — MC88</sub>

</div>