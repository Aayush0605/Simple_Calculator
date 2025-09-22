🧮 Simple Mobile Calculator: Line-by-Line Code Explanation
This document provides a detailed, line-by-line breakdown of the index.html file, which contains the entire Simple Mobile Calculator app (HTML structure, embedded CSS, and embedded JS). The app is a mobile-optimized calculator supporting basic arithmetic (+, -, ×, ÷), decimals, sign toggle, percentage, history logging, and light/dark theme switching.
The explanations are organized into interactive sections using collapsible Markdown details for easy reading on GitHub. Each section includes:

Code Snippet: Relevant lines with approximate line numbers (based on the ~275-line file).
Line-by-Line Details: What each line does, why it’s included, and how it contributes.
Tips & Insights: Design decisions, potential extensions, or debugging notes.

This is ideal for contributors, learners, or anyone exploring vanilla HTML/CSS/JS apps. Click the section headers to expand! See the live app at https://aayush0605.github.io/Simple_Calculator/.

📜 File Overview

File: index.html (~275 lines, single file).
Structure:
Lines 1-7: HTML Doctype and <head> (metadata, favicon).
Lines 8-145: Embedded CSS in <style> (layout, styles, themes).
Lines 146-192: HTML <body> (UI: display, buttons, history).
Lines 193-324: Embedded JS in <script> (logic, events, calculations).
Lines 325-326: Closing tags.


Purpose: Self-contained, lightweight (~10KB), mobile-first, no dependencies.



🛠️ Section 1: HTML Doctype and Head (Lines 1-7)

Sets up the document type, language, metadata, and favicon for browser compatibility and mobile responsiveness.
1: <!DOCTYPE html>
2: <html lang="en">
3: <head>
4:     <meta charset="UTF-8">
5:     <meta name="viewport" content="width=device-width, initial-scale=1.0">
6:     <title>Simple Mobile Calculator</title>
7:     <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🧮</text></svg>">


Line 1: <!DOCTYPE html> - Declares HTML5 standard. Why? Ensures modern browser rendering, avoiding quirks mode for consistent styling.
Line 2: <html lang="en"> - Root element, sets language to English. Why? Enhances accessibility (e.g., screen readers) and SEO; supports emoji rendering.
Line 3: <head> - Starts metadata section (not visible on page).
Line 4: <meta charset="UTF-8"> - Uses UTF-8 encoding. Why? Supports special characters (e.g., ×, ÷) and emojis (e.g., 🧮 in favicon).
Line 5: <meta name="viewport" content="width=device-width, initial-scale=1.0"> - Scales app to device width, no initial zoom. Why? Mobile-first design; ensures buttons/display fit phones without pinching.
Line 6: <title>Simple Mobile Calculator</title> - Browser tab title. Why? Clear app identity in tabs/bookmarks.
Line 7: <link rel="icon" href="data:image/svg+xml,..."> - Inline SVG favicon with 🧮 emoji. Why? No external file; adds visual flair to tabs.

Tips & Insights: Minimal head ensures fast load. For PWA support (installable app), add <meta name="theme-color" content="#f5f7fa"> for status bar color.




🎨 Section 2: Embedded CSS (Lines 8-145)

Embedded in <style> tag, this CSS defines the visual layout, styling, animations, and light/dark themes using Grid/Flexbox for responsiveness and touch-friendly design.
8:     <style>
9:         * {
10:             margin: 0;
11:             padding: 0;
12:             box-sizing: border-box;
13:         }
14:
15:         body {
16:             font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
17:             background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
18:             display: flex;
19:             justify-content: center;
20:             align-items: center;
21:             min-height: 100vh;
22:             transition: background 0.3s ease;
23:         }
24:
25:         .calculator {
26:             background: white;
27:             border-radius: 20px;
28:             box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
29:             padding: 20px;
30:             width: 100%;
31:             max-width: 300px;
32:             transition: all 0.3s ease;
33:         }
34:
35:         header {
36:             display: flex;
37:             justify-content: space-between;
38:             align-items: center;
39:             margin-bottom: 10px;
40:         }
41:
42:         header h1 {
43:             font-size: 1.2em;
44:             color: #333;
45:         }
46:
47:         .theme-btn {
48:             background: none;
49:             border: none;
50:             font-size: 1.5em;
51:             cursor: pointer;
52:         }
53:
54:         .display {
55:             margin-bottom: 10px;
56:         }
57:
58:         #screen {
59:             width: 100%;
60:             height: 60px;
61:             font-size: 2em;
62:             text-align: right;
63:             padding: 0 15px;
64:             border: none;
65:             background: #f8f9fa;
66:             border-radius: 10px;
67:             box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
68:         }
69:
70:         .history {
71:             margin-bottom: 15px;
72:             background: #f8f9fa;
73:             border-radius: 10px;
74:             padding: 10px;
75:         }
76:
77:         .history h3 {
78:             font-size: 0.9em;
79:             color: #666;
80:             margin-bottom: 5px;
81:         }
82:
83:         #history-list {
84:             font-family: monospace;
85:             font-size: 0.8em;
86:             color: #333;
87:             min-height: 40px;
88:             word-break: break-all;
89:         }
90:
91:         .history-controls {
92:             display: flex;
93:             gap: 5px;
94:             margin-top: 5px;
95:         }
96:
97:         .history-controls button {
98:             flex: 1;
99:             padding: 5px;
100:            border: none;
101:            background: #e9ecef;
102:            border-radius: 5px;
103:            cursor: pointer;
104:            font-size: 0.7em;
105:        }
106:
107:        .buttons {
108:            display: grid;
109:            grid-template-columns: repeat(4, 1fr);
110:            gap: 10px;
111:        }
112:
113:        .btn {
114:            height: 50px;
115:            border: none;
116:            border-radius: 10px;
117:            font-size: 1.2em;
118:            cursor: pointer;
119:            transition: all 0.1s ease;
120:        }
121:
122:        .num { background: #e9ecef; color: #333; }
123:        .op { background: #ff9500; color: white; }
124:        .equals { background: #007aff; color: white; }
125:        .span-two { grid-column: span 2; }
126:
127:        .btn:hover { transform: scale(1.02); }
128:        .btn:active { transform: scale(0.98); }
129:
130:        body.dark {
131:            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
132:        }
133:
134:        body.dark .calculator { background: #34495e; color: white; }
135:        body.dark #screen { background: #2c3e50; color: white; }
136:        body.dark .num { background: #4a5568; color: white; }
137:        body.dark .history { background: #4a5568; }
138:        body.dark #history-list { color: #e2e8f0; }
139:
140:        /* Mobile Responsiveness */
141:        @media (max-width: 480px) {
142:            .calculator { margin: 10px; padding: 15px; }
143:            .btn { height: 45px; font-size: 1.1em; }
144:        }
145:    </style>


Line 8: <style> - Starts embedded CSS. Why? Single-file app; eliminates external file requests for faster loading.
Lines 9-13: * { margin: 0; padding: 0; box-sizing: border-box; } - Resets browser defaults, uses border-box for consistent sizing. Why? Ensures uniform layout across browsers like Chrome/Safari.
Lines 15-23: body { ... } - Sets cross-platform fonts, light gradient background, flex centering, full viewport height, transition for theme switching. Why? Centers calculator, adds visual appeal, supports smooth dark mode toggle.
Lines 25-33: .calculator { ... } - White card with rounded corners, shadow, padding, max-width 300px. Why? Clean, mobile-friendly container mimicking app UI.
Lines 35-40: header { ... } - Flex layout for title and theme button, spaced apart. Why? Aligns elements horizontally with spacing.
Lines 42-45: header h1 { ... } - Small, dark title. Why? Subtle branding without dominating UI.
Lines 47-52: .theme-btn { ... } - No background/border, large emoji, pointer cursor. Why? Minimalist theme toggle button.
Lines 54-56: .display { ... } - Margin below display. Why? Spaces it from header/history.
Lines 58-68: #screen { ... } - Full-width input: 60px tall, large font, right-aligned, no border, light gray background, rounded, inset shadow. Why? Mimics calculator screen; readonly (set in HTML) prevents manual edits.
Lines 70-75: .history { ... } - History panel with margin, light background, rounded, padding. Why? Visually distinct section for calculation logs.
Lines 77-81: .history h3 { ... } - Small, gray heading. Why? Clearly labels history section.
Lines 83-89: #history-list { ... } - Monospace font, small size, min-height, word-break for long numbers. Why? Readable equations; prevents text overflow.
Lines 91-95: .history-controls { ... } - Flex layout with gap for buttons. Why? Aligns Copy/Clear buttons side-by-side.
Lines 97-105: .history-controls button { ... } - Full-width, padded, no border, light background, rounded, small font. Why? Compact, touch-friendly controls.
Lines 107-111: .buttons { ... } - 4-column grid with gaps. Why? Creates 4x5 button layout, responsive to screen size.
Lines 113-120: .btn { ... } - Base button style: 50px height, no border, rounded, large font, pointer, 0.1s transition. Why? Touch-friendly, animated clicks.
Lines 122-125: .num, .op, .equals, .span-two - Colors for numbers (gray), operators (orange), equals (blue); zero spans two columns. Why? Visual distinction; wide zero for thumb taps.
Lines 127-128: .btn:hover, .btn:active - Scale up/down for hover/click. Why? Visual feedback; :active works for touch devices.
Lines 130-138: body.dark { ... } and children - Dark theme overrides: gradient background, dark calculator, screen, buttons, history. Why? Toggled via JS for night mode.
Lines 141-144: @media (max-width: 480px) { ... } - Reduces margins/padding, shrinks buttons for small screens. Why? Optimizes for mobile phones.
Line 145: </style> - Closes CSS block.

Tips & Insights: Vanilla CSS avoids preprocessors (e.g., Sass) for simplicity. Grid/Flexbox ensures responsiveness without frameworks. Add CSS variables (e.g., --primary-color) for easier theme customization.




🖼️ Section 3: HTML Body and UI Elements (Lines 146-192)

Defines the visible UI: calculator container, header, display, history panel, and button grid.
146: </head>
147: <body>
148:     <div class="calculator">
149:         <header>
150:             <h1>Simple Mobile Calculator</h1>
151:             <button id="theme-toggle" class="theme-btn">🌙</button>
152:         </header>
153:         
154:         <div class="display">
155:             <input type="text" id="screen" readonly value="0" maxlength="20">
156:         </div>
157:         
158:         <div class="history">
159:             <h3>History</h3>
160:             <div id="history-list">No calculations yet</div>
161:             <div class="history-controls">
162:                 <button id="copy-last">Copy Last</button>
163:                 <button id="clear-history">Clear</button>
164:             </div>
165:         </div>
166:         
167:         <div class="buttons">
168:             <button class="btn op" data-value="AC">AC</button>
169:             <button class="btn op" data-value="+/-">+/-</button>
170:             <button class="btn op" data-value="%">%</button>
171:             <button class="btn op" data-value="÷">÷</button>
172:             
173:             <button class="btn num" data-value="7">7</button>
174:             <button class="btn num" data-value="8">8</button>
175:             <button class="btn num" data-value="9">9</button>
176:             <button class="btn op" data-value="×">×</button>
177:             
178:             <button class="btn num" data-value="4">4</button>
179:             <button class="btn num" data-value="5">5</button>
180:             <button class="btn num" data-value="6">6</button>
181:             <button class="btn op" data-value="−">−</button>
182:             
183:             <button class="btn num" data-value="1">1</button>
184:             <button class="btn num" data-value="2">2</button>
185:             <button class="btn num" data-value="3">3</button>
186:             <button class="btn op" data-value="+">+</button>
187:             
188:             <button class="btn num span-two" data-value="0">0</button>
189:             <button class="btn num" data-value=".">.</button>
190:             <button class="btn op equals" data-value="=">=</button>
191:         </div>
192:     </div>


Line 146: </head> - Ends metadata section.
Line 147: <body> - Starts visible content.
Line 148: <div class="calculator"> - Main wrapper for app. Why? Applies card-like styling (shadow, rounded corners).
Lines 149-152: <header> ... </header> - Contains title and theme toggle button. Why? Top bar for branding and control.
Line 150: <h1>Simple Mobile Calculator</h1> - App title. Why? Clear identification.
Line 151: <button id="theme-toggle" class="theme-btn">🌙</button> - Theme switcher with moon emoji. Why? JS toggles to sun (☀️) in dark mode.
Lines 154-156: <div class="display"> <input ... > </div> - Readonly text input, starts at "0", max 20 chars. Why? Shows current value/result; readonly prevents manual typing; maxlength avoids overflow.
Lines 158-165: <div class="history"> ... </div> - History panel with heading, list div, and Copy/Clear buttons. Why? Logs calculations; IDs enable JS manipulation.
Lines 167-191: <div class="buttons"> ... </div> - Grid of buttons: Each has class="btn" (base style), num/op/equals for colors, data-value for JS (e.g., data-value="+"), and content (e.g., "7"). Zero has span-two. Why? Grid layout; data attributes simplify event handling; zero wider for mobile thumb taps.
Line 192: </div> - Closes calculator container.

Tips & Insights: Semantic classes (e.g., buttons, history) make styling/JS targeting clear. data-value allows flexibility (e.g., × for multiply). Add aria-label (e.g., aria-label="Add" on + button) for accessibility.




🧠 Section 4: Embedded JavaScript (Lines 193-324)

Embedded in <script> tag, this JS powers the calculator: state management, event handling, math operations, history, and theme toggling. Uses a Calculator class for modularity.
193:     <script>
194:         class Calculator {
195:             constructor() {
196:                 this.screen = document.getElementById('screen');
197:                 this.historyList = document.getElementById('history-list');
198:                 this.current = '0';
199:                 this.previous = null;
200:                 this.operation = null;
201:                 this.history = [];
202:
203:                 this.buttons = document.querySelectorAll('.btn');
204:                 this.buttons.forEach(btn => btn.addEventListener('click', (e) => this.handleInput(e.target.dataset.value)));
205:
206:                 document.getElementById('copy-last').addEventListener('click', () => this.copyLast());
207:                 document.getElementById('clear-history').addEventListener('click', () => this.clearHistory());
208:                 document.getElementById('theme-toggle').addEventListener('click', () => this.toggleTheme());
209:             }
210:
211:             handleInput(value) {
212:                 if (this.isNumber(value) || value === '.') {
213:                     this.appendNumber(value);
214:                 } else if (this.isOperation(value)) {
215:                     this.selectOperation(value);
216:                 } else if (value === '=') {
217:                     this.calculate();
218:                 } else if (value === 'AC') {
219:                     this.clear();
220:                 } else if (value === '+/-') {
221:                     this.toggleSign();
222:                 } else if (value === '%') {
223:                     this.percentage();
224:                 }
225:                 this.updateDisplay();
226:             }
227:
228:             appendNumber(num) {
229:                 if (this.current === '0' && num !== '.') {
230:                     this.current = num;
231:                 } else {
232:                     this.current += num;
233:                 }
234:             }
235:
236:             selectOperation(op) {
237:                 if (this.operation && this.previous !== null) {
238:                     this.calculate();
239:                 }
240:                 this.operation = op;
241:                 this.previous = this.current;
242:                 this.current = '0';
243:             }
244:
245:             calculate() {
246:                 if (!this.operation || !this.previous) return;
247:                 let result;
248:                 const prev = parseFloat(this.previous);
249:                 const curr = parseFloat(this.current);
250:                 switch (this.operation) {
251:                     case '+': result = prev + curr; break;
252:                     case '-': result = prev - curr; break;
253:                     case '×': result = prev * curr; break;
254:                     case '÷': result = curr === 0 ? 'Error' : prev / curr; break;
255:                 }
256:                 const entry = `${this.previous} ${this.operation} ${this.current} = ${result}`;
257:                 this.current = result.toString();
258:                 this.operation = null;
259:                 this.previous = null;
260:                 this.addToHistory(entry);
261:             }
262:
263:             clear() {
264:                 this.current = '0';
265:                 this.previous = null;
266:                 this.operation = null;
267:             }
268:
269:             toggleSign() {
270:                 this.current = (parseFloat(this.current) * -1).toString();
271:             }
272:
273:             percentage() {
274:                 this.current = (parseFloat(this.current) / 100).toString();
275:             }
276:
277:             updateDisplay() {
278:                 this.screen.value = this.current;
279:             }
280:
281:             addToHistory(entry) {
282:                 this.history.unshift(entry);
283:                 if (this.history.length > 10) this.history.pop(); // Limit to 10
284:                 this.updateHistory();
285:             }
286:
287:             updateHistory() {
288:                 if (this.history.length === 0) {
289:                     this.historyList.textContent = 'No calculations yet';
290:                 } else {
291:                     this.historyList.innerHTML = this.history.slice(0, 5).map(h => `<div>${h}</div>`).join(''); // Show last 5
292:                 }
293:             }
294:
295:             copyLast() {
296:                 if (this.history.length > 0) {
297:                     navigator.clipboard.writeText(this.history[0]);
298:                     alert('Last result copied!');
299:                 }
300:             }
301:
302:             clearHistory() {
303:                 this.history = [];
304:                 this.updateHistory();
305:             }
306:
307:             toggleTheme() {
308:                 document.body.classList.toggle('dark');
309:                 const btn = document.getElementById('theme-toggle');
310:                 btn.textContent = document.body.classList.contains('dark') ? '☀️' : '🌙';
311:             }
312:
313:             isNumber(value) {
314:                 return !isNaN(value) && value !== '';
315:             }
316:
317:             isOperation(value) {
318:                 return ['+', '-', '×', '÷'].includes(value);
319:             }
320:         }
321:
322:         // Initialize
323:         new Calculator();
324:     </script>


Line 193: <script> - Starts embedded JS, placed at body end for DOM readiness. Why? Ensures HTML elements exist before JS runs.
Lines 194-209: class Calculator { constructor() { ... } } - Defines Calculator class, grabs DOM elements (screen, historyList), sets initial state (current='0', previous/operation=null, history=[]), adds click listeners to buttons via data-value, and listeners for copy/clear/theme buttons. Why? Encapsulates state/logic; event delegation reduces code.
Lines 211-226: handleInput(value) { ... } - Routes button clicks: Checks if value is number/dot, operation, equals, AC, +/-, or %, calls relevant method, updates display. Why? Central hub for all interactions.
Lines 228-234: appendNumber(num) { ... } - Builds current string: Replaces "0" unless adding decimal, else appends. Why? Prevents leading zeros (e.g., "012" becomes "12").
Lines 236-243: selectOperation(op) { ... } - If prior operation exists, calculates first; stores operator, saves current as previous, resets current to "0". Why? Supports chained operations (e.g., 2+3+).
Lines 245-261: calculate() { ... } - Exits if no op/previous; parses floats, uses switch for math (+, -, ×, ÷), handles ÷0 ("Error"), logs entry (e.g., "2 + 3 = 5"), updates state, adds to history. Why? Safe math without eval(); logs for user review.
Lines 263-267: clear() { ... } - Resets current to "0", nulls previous/operation. Why? Implements AC (all clear) button.
Lines 269-271: toggleSign() { ... } - Negates current value (e.g., 5 to -5). Why? +/- feature for quick sign changes.
Lines 273-275: percentage() { ... } - Divides current by 100 (e.g., 50 to 0.5). Why? % feature for discounts/tips.
Lines 277-279: updateDisplay() { ... } - Sets screen.value to current. Why? Keeps UI in sync with state.
Lines 281-285: addToHistory(entry) { ... } - Adds entry to front of history array, limits to 10, updates display. Why? Shows recent calculations first; prevents memory bloat.
Lines 287-293: updateHistory() { ... } - If empty, shows "No calculations yet"; else, renders top 5 entries as <div>s. Why? Dynamic history UI; limits display for space.
Lines 295-300: copyLast() { ... } - Copies first history entry to clipboard, alerts user. Why? Allows sharing results (e.g., paste in notes).
Lines 302-305: clearHistory() { ... } - Empties history, updates UI. Why? Clears logs for privacy or reset.
Lines 307-311: toggleTheme() { ... } - Toggles dark class on body, switches button emoji (🌙 to ☀️). Why? Light/dark mode for user comfort.
Lines 313-315: isNumber(value) { ... } - Checks if value is numeric and non-empty. Why? Validates digit/decimal inputs.
Lines 317-319: isOperation(value) { ... } - Checks if value is +, -, ×, ÷. Why? Validates operator inputs.
Line 320: } - Ends Calculator class.
Lines 322-323: new Calculator(); - Instantiates class to start app. Why? Initializes event listeners and state.
Line 324: </script> - Closes JS block.

Tips & Insights: ES6 class structure is modular—add methods like sqrt() easily. switch avoids eval() for security. Debug issues (e.g., history not updating) by adding console.log(this.current) in methods.




🔗 Section 5: Closing Tags (Lines 325-326)

Closes the HTML document.
325: </body>
326: </html>


Line 325: </body> - Ends body content.
Line 326: </html> - Ends HTML document. Why? Completes valid HTML structure for browser parsing.

Tips & Insights: No trailing scripts—keeps app lightweight. Ensure no extra whitespace to avoid parsing issues.



🚀 How It All Connects

Load: Browser parses HTML (UI), applies CSS (styles), runs JS (logic).
Interaction: Button clicks (data-value) trigger handleInput, updating state (current, previous, operation).
Calculation: calculate() uses switch for safe math, logs to history.
UI Updates: updateDisplay/updateHistory sync DOM; toggleTheme switches styles.
Features: History copy/clear, theme toggle enhance UX.

🛠️ Debugging & Extending

Debug: Open browser console (F12), add console.log in JS methods (e.g., console.log(this.current) in appendNumber).
Extend: Add operations like square root:
HTML (in <div class="buttons">): <button class="btn op" data-value="√">√</button>
JS (in handleInput): if (value === '√') this.current = Math.sqrt(parseFloat(this.current)).toString();


Test: Use Chrome DevTools (Device Toolbar) for mobile view; test ÷0, long decimals.

This single-file app (~10KB) is lightweight, mobile-first, and ready for your repo at https://aayush0605.github.io/Simple_Calculator/. Fork, modify, or open issues for questions! 🚀

Contribute: Add features or fix bugs? See CONTRIBUTING.md (if added).Contact: Tweet @aayush0605 or open an issue on GitHub.
