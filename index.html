<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>8面</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f2f5;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
            user-select: none;
        }

        h1 {
            color: #333;
            margin-bottom: 20px;
        }

        /* 六圍一梅花陣型外框 */
        .dice-layout {
            position: relative;
            width: 280px;
            height: 280px;
            margin-bottom: 30px;
        }

        /* 統一骰子基本樣式 */
        .dice {
            position: absolute;
            width: 70px;
            height: 70px;
            background-color: #ffffff;
            border: 3px solid #333;
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            font-weight: bold;
            color: #2c3e50;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            /* 移除可能導致文字模糊的 transform 全局動畫，改用個別定位 */
            backface-visibility: hidden;
        }

        /* 精確計算固定位置（確保滾動時位置不交疊，100% 可視） */
        .d0 { top: 105px; left: 105px; z-index: 10; background-color: #fff8db; } /* 中間 */
        .d1 { top: 15px;  left: 105px; }  /* 正上 */
        .d2 { top: 60px;  left: 183px; }  /* 右上 */
        .d3 { top: 150px; left: 183px; }  /* 右下 */
        .d4 { top: 195px; left: 105px; }  /* 正下 */
        .d5 { top: 150px; left: 27px; }   /* 左下 */
        .d6 { top: 60px;  left: 27px; }   /* 左上 */

        /* 微幅震動動畫，確保所有骰子數字在原地滾動且清晰可見 */
        @keyframes subtle-roll {
            0% { transform: translate(0, 0) rotate(0deg); }
            25% { transform: translate(2px, -2px) rotate(3deg); }
            50% { transform: translate(-2px, 2px) rotate(-3deg); }
            75% { transform: translate(-2px, -2px) rotate(2deg); }
            100% { transform: translate(0, 0) rotate(0deg); }
        }

        .rolling {
            animation: subtle-roll 0.1s infinite ease-in-out;
            background-color: #e8f4fd !important;
            border-color: #3498db;
            color: #3498db;
        }

        /* 總和顯示區域 */
        .result-container {
            font-size: 1.8rem;
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 20px;
            height: 40px;
        }

        .total-score {
            color: #e74c3c;
            font-size: 2.2rem;
        }

        .btn-roll {
            padding: 15px 40px;
            font-size: 1.2rem;
            font-weight: bold;
            color: white;
            background-color: #2ecc71;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(46, 204, 113, 0.4);
            transition: all 0.2s ease;
        }

        .btn-roll:hover {
            background-color: #27ae60;
            transform: translateY(-2px);
            box-shadow: 0 7px 20px rgba(46, 204, 113, 0.6);
        }

        .btn-roll:disabled {
            background-color: #95a5a6;
            box-shadow: none;
            cursor: not-allowed;
        }
    </style>
</head>
<body>

    <h1>8</h1>

    <div class="dice-layout" id="diceLayout">
        <div class="dice d0">0</div>
        <div class="dice d1">0</div>
        <div class="dice d2">0</div>
        <div class="dice d3">0</div>
        <div class="dice d4">0</div>
        <div class="dice d5">0</div>
        <div class="dice d6">0</div>
    </div>

    <div class="result-container">
        RESULT：<span class="total-score" id="totalResult">0</span>
    </div>

    <button class="btn-roll" id="rollBtn" onclick="rollDice()">START</button>

    <script>
        const rollBtn = document.getElementById('rollBtn');
        const totalResult = document.getElementById('totalResult');
        const diceElements = document.querySelectorAll('.dice');
        
        // 初始化 Web Audio API 用於生成模擬骰子碰撞聲
        let audioCtx = null;

        function initAudio() {
            if (!audioCtx) {
                audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            }
        }

        // 經由程式演算法即時產生短促的骰子撞擊聲
        function playClickSound() {
            initAudio();
            if (!audioCtx) return;

            const osc = audioCtx.createOscillator();
            const gainNode = audioCtx.createGain();
            
            osc.type = 'triangle'; // 三角波，聲音較溫和沉悶，接近骨質/塑膠骰子碰撞
            // 隨機微調頻率模擬不同骰子撞擊的角度
            osc.frequency.setValueAtTime(150 + Math.random() * 100, audioCtx.currentTime);
            
            // 快速衰減的音量（模擬敲擊聲短促特性）
            gainNode.gain.setValueAtTime(0.3, audioCtx.currentTime);
            gainNode.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.05);
            
            osc.connect(gainNode);
            gainNode.connect(audioCtx.destination);
            
            osc.start();
            osc.stop(audioCtx.currentTime + 0.06);
        }

        function rollDice() {
            rollBtn.disabled = true;
            totalResult.innerText = "搖晃中...";
            
            let counter = 0;
            // 縮短間隔至 60 毫秒，使滾動更流暢，所有骰子維持就地微幅震動（完全可視）
            const animationInterval = setInterval(() => {
                diceElements.forEach(die => {
                    die.innerText = Math.floor(Math.random() * 8);
                    die.classList.add('rolling');
                });

                // 每滾動一次同步播放一次骰子碰撞音效
                playClickSound();
                counter++;
                
                // 總共滾動 20 次（約 1.2 秒）後停止
                if (counter > 20) {
                    clearInterval(animationInterval);
                    finalizeResult();
                }
            }, 60);
        }

        function finalizeResult() {
            let sum = 0;

            diceElements.forEach(die => {
                const finalValue = Math.floor(Math.random() * 8);
                die.innerText = finalValue;
                die.classList.remove('rolling');
                sum += finalValue;
            });

            // 最終落定的大撞擊聲
            playClickSound();
            setTimeout(() => playClickSound(), 40);

            totalResult.innerText = sum;
            rollBtn.disabled = false;
        }
    </script>

</body>
</html>
