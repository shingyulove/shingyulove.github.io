<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>女僕手繪 Chekki (最終手繪感版)</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dela+Gothic+One&family=RocknRoll+One&family=Yomogi&display=swap');

        :root {
            --bg-color: #fff0f5;
            --card-bg: #ffffff;
        }

        body {
            background-color: var(--bg-color);
            background-image: radial-gradient(#ffc2d1 15%, transparent 16%);
            background-size: 25px 25px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
            overflow: hidden;
            user-select: none;
            font-family: 'Yomogi', cursive;
        }

        .controls { margin-top: 20px; z-index: 100; }

        button {
            background: #ff6b8b;
            color: white;
            border: none;
            padding: 12px 35px;
            border-radius: 30px;
            font-size: 1.1rem;
            font-family: 'RocknRoll One', sans-serif;
            cursor: pointer;
            box-shadow: 0 5px 0 #d84060;
            transition: transform 0.1s;
        }
        button:active { transform: translateY(5px); box-shadow: none; }

        .instax {
            position: relative;
            width: 340px;
            height: 540px;
            background: var(--card-bg);
            border-radius: 10px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.1);
            overflow: hidden;
        }

        .photo-area {
            position: absolute;
            top: 30px;
            left: 20px;
            width: 300px;
            height: 380px;
            background-color: #eee;
            background-image: url('https://placehold.co/600x800/ffe6eb/ff8da1?text=Maid+Photo'); 
            background-size: cover;
            background-position: center;
            z-index: 1;
            border: 1px solid #eee;
        }

        .canvas-layer {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: 10;
            pointer-events: none;
        }

        /* 簽名組件 */
        .signature-group {
            position: absolute;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 50;
            /* 微微的旋轉，不要太正 */
            transform-origin: center;
        }

        .sig-name {
            font-family: 'RocknRoll One', sans-serif;
            font-size: 2.8rem;
            color: #ff4081;
            line-height: 1;
            white-space: nowrap;
            /* 簽名稍微透一點點，像麥克筆 */
            opacity: 0.9; 
        }

        .sig-date {
            font-family: 'Dela Gothic One', cursive;
            font-size: 1.2rem;
            color: #333;
            margin-top: 5px;
            opacity: 0.8;
        }

        /* 圖案組件 */
        .doodle-item {
            position: absolute;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 20;
            /* 默認混合模式，讓顏色像墨水一樣 */
            mix-blend-mode: multiply; 
            animation: pop 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        /* 特殊：白色描邊 (貼紙效果) */
        .sticker-effect {
            mix-blend-mode: normal !important; /* 貼紙不能透 */
            filter: drop-shadow(0px 0px 0px white) !important; /* CSS fallback */
        }

        /* 日文文字組件 */
        .text-item {
            position: absolute;
            z-index: 25;
            font-weight: bold;
            white-space: nowrap;
            mix-blend-mode: multiply;
            line-height: 1;
        }

        @keyframes pop {
            from { transform: scale(0) rotate(0deg); opacity: 0; }
            to { opacity: 0.9; } /* 結束狀態由 JS 設定 transform */
        }

    </style>
</head>
<body>

    <h1>🎨 女僕手繪 Chekki</h1>

    <div class="instax">
        <div class="photo-area"></div>
        <div class="canvas-layer" id="canvas"></div>
    </div>

    <div class="controls">
        <button onclick="generateArt()">✨ 生成簽名與塗鴉 ✨</button>
    </div>

    <script>
        // ================= 資料庫 =================

        // 顏色庫 (Posca 筆風格)
        const colors = ["#ff7eb3", "#ff6b6b", "#7afcff", "#feff9c", "#b39ddb", "#ffab91", "#81ecec"];
        const maidNames = ["Miku", "Rina", "Hana", "Momo", "Yuki", "Alice"];
        const jpTexts = ["大好き", "推し♡", "にゃん", "あざと", "LOVE", "神対応", "萌え", "Chu!"];

        // 手繪 SVG 庫 (重點：看起來要歪歪扭扭)
        // type: 'fill' (實心色塊), 'stroke' (線條塗鴉)
        const doodles = [
            // 歪歪扭扭的實心愛心
            { type: 'fill', path: 'M50,90 C20,60 0,40 20,20 C35,5 50,25 50,25 C50,25 65,5 80,20 C100,40 80,60 50,90 Z' },
            // 手繪五角星 (不規則)
            { type: 'fill', path: 'M50,5 L60,35 L95,35 L70,55 L80,90 L50,70 L20,90 L30,55 L5,35 L40,35 Z' },
            // 塗鴉螺旋 (線條)
            { type: 'stroke', path: 'M50,50 m-20,0 a20,20 0 1,1 40,0 a20,20 0 1,1 -40,0 a15,15 0 1,1 30,0', strokeWidth: 4 },
            // 閃光 (線條)
            { type: 'stroke', path: 'M50,10 L50,90 M10,50 L90,50 M25,25 L75,75 M75,25 L25,75', strokeWidth: 3 },
            // 貓耳朵輪廓 (實心)
            { type: 'fill', path: 'M20,80 Q10,10 50,30 Q90,10 80,80 Z' },
            // 蝴蝶結 (實心)
            { type: 'fill', path: 'M50,50 L10,30 Q5,50 10,70 L50,50 L90,70 Q95,50 90,30 Z' },
            // 小花 (線條)
            { type: 'stroke', path: 'M50,50 Q50,20 70,40 T90,50 T70,60 T50,80 T30,60 T10,50 T30,40 Z', strokeWidth: 3 },
            // 音符
            { type: 'fill', path: 'M30,60 L30,20 L70,10 L70,50 L30,60 M20,70 A10,10 0 1,1 40,70 A10,10 0 1,1 20,70' }
        ];

        let occupiedRects = [];

        // ================= 邏輯區 =================

        function generateArt() {
            const canvas = document.getElementById('canvas');
            canvas.innerHTML = '';
            occupiedRects = [];

            // 1. 畫手繪邊框 (背景層)
            drawWobblyBorder(canvas);

            // 2. 簽名 (最優先，隨機位置)
            drawSignature(canvas);

            // 3. 日文短語 (1-2個)
            const textCount = 1 + Math.floor(Math.random() * 2);
            for(let i=0; i<textCount; i++) drawText(canvas);

            // 4. 手繪圖案 (4-7個)
            const doodleCount = 4 + Math.floor(Math.random() * 4);
            for(let i=0; i<doodleCount; i++) drawDoodle(canvas);
        }

        function drawSignature(container) {
            const group = document.createElement('div');
            group.className = 'signature-group';
            
            const name = maidNames[Math.floor(Math.random() * maidNames.length)];
            const today = new Date();
            const dateStr = `${today.getFullYear()}.${today.getMonth()+1}.${today.getDate()}`;

            group.innerHTML = `
                <div class="sig-name">${name} <span style="font-size:0.6em">♡</span></div>
                <div class="sig-date">${dateStr}</div>
            `;

            container.appendChild(group); // 先加進去算大小

            const rect = group.getBoundingClientRect();
            const w = rect.width;
            const h = rect.height;
            
            // 隨機旋轉 (-10 ~ 10)
            const rot = (Math.random() - 0.5) * 20;
            group.style.transform = `rotate(${rot}deg)`;

            // 尋找位置 (優先嘗試上下兩端)
            placeItem(group, w, h, container, true);
        }

        function drawText(container) {
            const text = jpTexts[Math.floor(Math.random() * jpTexts.length)];
            const el = document.createElement('div');
            el.className = 'text-item';
            el.innerText = text;
            
            // 樣式隨機
            el.style.color = colors[Math.floor(Math.random() * colors.length)];
            el.style.fontSize = `${24 + Math.random() * 20}px`; // 24-44px
            el.style.fontFamily = Math.random() > 0.5 ? "'RocknRoll One'" : "'Yomogi'";
            
            // 隨機旋轉 (-20 ~ 20)
            const rot = (Math.random() - 0.5) * 40;
            el.style.transform = `rotate(${rot}deg)`;

            container.appendChild(el);
            
            // 獲取大小並放置
            // 這裡用估算大小，因為字體渲染可能慢
            const estW = text.length * 30;
            const estH = 40;
            
            placeItem(el, estW, estH, container);
        }

        function drawDoodle(container) {
            const data = doodles[Math.floor(Math.random() * doodles.length)];
            const color = colors[Math.floor(Math.random() * colors.length)];
            const size = 50 + Math.random() * 60; // 50 - 110px 隨機大小
            
            const el = document.createElement('div');
            el.className = 'doodle-item';
            el.style.width = `${size}px`;
            el.style.height = `${size}px`;

            // 10% 機率白色描邊 (貼紙效果)
            const isSticker = Math.random() < 0.1;
            
            let svgContent = '';
            
            if (isSticker) {
                // 貼紙模式：強制白色描邊，內部填充顏色，不透
                el.classList.add('sticker-effect');
                // 如果是 stroke 類型，貼紙化比較難看，這裡強制轉 fill 邏輯或加粗
                if (data.type === 'stroke') {
                    svgContent = `<path d="${data.path}" stroke="${color}" stroke-width="${(data.strokeWidth||3)+4}" stroke-linecap="round" fill="none"/>
                                  <path d="${data.path}" stroke="white" stroke-width="${data.strokeWidth||3}" stroke-linecap="round" fill="none" stroke-dasharray="none"/>`;
                } else {
                    // Fill 類型：加一圈粗白邊
                    svgContent = `<path d="${data.path}" fill="${color}" stroke="white" stroke-width="8" stroke-linejoin="round"/>`;
                }
            } else {
                // 普通手繪模式
                if (data.type === 'fill') {
                    // 實心：無描邊
                    svgContent = `<path d="${data.path}" fill="${color}" stroke="none"/>`;
                } else {
                    // 線條：只有線
                    svgContent = `<path d="${data.path}" stroke="${color}" stroke-width="${data.strokeWidth || 3}" fill="none" stroke-linecap="round" stroke-linejoin="round"/>`;
                }
            }

            el.innerHTML = `<svg viewBox="0 0 100 100" style="overflow:visible; width:100%; height:100%">${svgContent}</svg>`;

            // 隨機變換
            const rot = (Math.random() - 0.5) * 60; // -30 ~ 30度 旋轉 (隨機性增加)
            const scale = 0.8 + Math.random() * 0.5; // 0.8 - 1.3 倍縮放
            const flip = Math.random() > 0.5 ? -1 : 1; // 50% 機率左右翻轉 (如果是文字則不翻轉，這裡是圖案)
            
            // 我們將旋轉應用在 transform 上，位置應用在 left/top 上
            el.style.transform = `rotate(${rot}deg) scale(${scale}, ${scale})`;

            container.appendChild(el);
            placeItem(el, size, size, container);
        }

        function drawWobblyBorder(container) {
            // 生成一個不規則的手繪框
            const svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
            svg.style.position = 'absolute';
            svg.style.top = '0';
            svg.style.left = '0';
            svg.style.width = '100%';
            svg.style.height = '100%';
            svg.style.zIndex = '5';
            svg.style.pointerEvents = 'none';

            const color = colors[Math.floor(Math.random() * colors.length)];
            
            // 相片區域大約是 20,30 到 320,410
            // 我們畫在這個周圍
            const pathStr = generateWobblyRect(20, 30, 300, 380);
            
            // 畫兩遍，模仿來回塗
            const path = document.createElementNS("http://www.w3.org/2000/svg", "path");
            path.setAttribute("d", pathStr);
            path.setAttribute("fill", "none");
            path.setAttribute("stroke", color);
            path.setAttribute("stroke-width", "3");
            path.setAttribute("stroke-linecap", "round");
            path.setAttribute("opacity", "0.6"); // 半透明一點

            svg.appendChild(path);
            container.appendChild(svg);
        }

        function generateWobblyRect(x, y, w, h) {
            // 簡單的手繪矩形算法：每個邊多幾個控制點抖動
            const wiggle = () => (Math.random() - 0.5) * 8;
            return `
                M ${x + wiggle()} ${y + wiggle()}
                L ${x + w + wiggle()} ${y + wiggle()}
                L ${x + w + wiggle()} ${y + h + wiggle()}
                L ${x + wiggle()} ${y + h + wiggle()}
                Z
            `;
        }

        function placeItem(el, w, h, container, preferEdge = false) {
            const containerW = 340;
            const containerH = 540;
            const padding = 10;
            
            let bestX = 0, bestY = 0;
            let found = false;

            // 嘗試 30 次
            for(let i=0; i<30; i++) {
                const left = Math.random() * (containerW - w - padding);
                const top = Math.random() * (containerH - h - padding);
                
                const newRect = { left, top, right: left + w, bottom: top + h };

                // 碰撞檢測
                if (!checkCollision(newRect)) {
                    // 如果是簽名(preferEdge)，我們希望它盡量不要在中間擋臉
                    if (preferEdge) {
                        // 檢查是否在中間區域 (臉部區域)
                        // 簡單假設中間區域是 y=150 到 y=350
                        if (top > 100 && top < 400) {
                            // 如果在中間，只有 20% 機率接受 (允許少量遮擋)，否則重試
                            if (Math.random() > 0.2) continue;
                        }
                    }

                    el.style.left = `${left}px`;
                    el.style.top = `${top}px`;
                    occupiedRects.push(newRect);
                    found = true;
                    break;
                }
            }

            if (!found) {
                el.remove(); // 沒地方放就刪掉
            }
        }

        function checkCollision(r1) {
            // 碰撞緩衝區
            const buffer = 5;
            for (let r2 of occupiedRects) {
                if (r1.left < r2.right + buffer &&
                    r1.right > r2.left - buffer &&
                    r1.top < r2.bottom + buffer &&
                    r1.bottom > r2.top - buffer) {
                    return true;
                }
            }
            return false;
        }

        window.onload = generateArt;

    </script>
</body>
</html>
