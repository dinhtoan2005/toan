<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vòng Quay May Mắn</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <style>
        body { font-family: sans-serif; text-align: center; background: #f4f4f9; padding: 20px; }
        .container { max-width: 500px; margin: auto; background: white; padding: 20px; border-radius: 15px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
        #canvas { margin: 20px 0; max-width: 100%; height: auto; border: 5px solid #333; border-radius: 50%; }
        button { padding: 10px 20px; font-size: 16px; cursor: pointer; background: #28a745; color: white; border: none; border-radius: 5px; }
        button:disabled { background: #ccc; }
        .history { margin-top: 20px; text-align: left; max-height: 200px; overflow-y: auto; border-top: 1px solid #eee; padding-top: 10px; }
        .admin-view { background: #fff3cd; padding: 10px; margin-top: 20px; border-radius: 10px; display: none; }
    </style>
</head>
<body>

<div class="container">
    <h2>Vòng Quay May Mắn</h2>
    <div id="login-section">
        <input type="text" id="userCode" placeholder="Nhập mã của bạn...">
        <button onclick="login()">Vào chơi</button>
    </div>

    <div id="game-section" style="display:none;">
        <p>Chào: <strong id="displayName"></strong> | Lượt còn lại: <strong id="spinsLeft">0</strong></p>
        <canvas id="canvas" width="400" height="400"></canvas>
        <br>
        <button id="spinBtn" onclick="spin()">QUAY NGAY</button>
        
        <div class="history" id="personalHistory">
            <strong>Lịch sử của bạn:</strong>
            <ul id="historyList"></ul>
            <p><strong>Tổng điểm: <span id="totalScore">0</span></strong></p>
        </div>

        <div id="adminPanel" class="admin-view">
            <h3>Bảng Điều Khiển (Admin)</h3>
            <div id="allStats"></div>
        </div>
    </div>
</div>

<script>
    const prizes = [
        { n: "50", p: 20 }, { n: "100", p: 10 }, { n: "200", p: 13 },
        { n: "250", p: 7 }, { n: "1 chậu hoa", p: 5 }, { n: "Thêm lượt", p: 10 },
        { n: "500", p: 5 }, { n: "Không có gì", p: 10 }, { n: "100", p: 15 }, { n: "300", p: 5 }
    ];

    const usersData = {
        "16378": 6, "17385": 3, "18374": 3, "18246": 1, "19264": 1, "12345": 7, "12012008": 3, "99999": 999
    };

    let currentUser = null;
    let spins = 0;
    let history = [];
    let startAngle = 0;
    const arc = Math.PI / (prizes.length / 2);

    function drawWheel() {
        const canvas = document.getElementById("canvas");
        const ctx = canvas.getContext("2d");
        ctx.clearRect(0,0,400,400);
        prizes.forEach((prize, i) => {
            const angle = startAngle + i * arc;
            ctx.fillStyle = `hsl(${i * 36}, 70%, 60%)`;
            ctx.beginPath(); ctx.moveTo(200, 200);
            ctx.arc(200, 200, 180, angle, angle + arc);
            ctx.fill(); ctx.stroke();
            ctx.save(); ctx.fillStyle = "white"; ctx.translate(200, 200);
            ctx.rotate(angle + arc / 2); ctx.fillText(prize.n, 100, 5);
            ctx.restore();
        });
    }

    function login() {
        const code = document.getElementById("userCode").value;
        if (usersData[code] !== undefined) {
            currentUser = code;
            spins = usersData[code];
            document.getElementById("login-section").style.display = "none";
            document.getElementById("game-section").style.display = "block";
            document.getElementById("displayName").innerText = code;
            document.getElementById("spinsLeft").innerText = spins;
            if(code === "99999") document.getElementById("adminPanel").style.display = "block";
            drawWheel();
            loadGlobalData();
        } else { alert("Mã không hợp lệ!"); }
    }

    function spin() {
        if (spins <= 0) return alert("Hết lượt quay!");
        document.getElementById("spinBtn").disabled = true;
        
        // Tính toán tỉ lệ
        let rand = Math.random() * 100;
        let cumulative = 0;
        let winIndex = 0;
        for (let i = 0; i < prizes.length; i++) {
            cumulative += prizes[i].p;
            if (rand <= cumulative) { winIndex = i; break; }
        }

        const rotation = (360 * 5) + (360 - (winIndex * (360/10)));
        let currentRotation = 0;
        const interval = setInterval(() => {
            startAngle += 0.1; drawWheel();
            currentRotation += 5;
            if (currentRotation >= rotation) {
                clearInterval(interval);
                finishSpin(winIndex);
            }
        }, 10);
    }

    function finishSpin(idx) {
        const result = prizes[idx].n;
        if (result === "Thêm lượt") spins += 1;
        else spins -= 1;
        
        history.push(result);
        updateUI();
        saveResult(result);
        Swal.fire("Kết quả", "Bạn nhận được: " + result, "success");
        document.getElementById("spinBtn").disabled = false;
    }

    function updateUI() {
        document.getElementById("spinsLeft").innerText = spins;
        const list = document.getElementById("historyList");
        list.innerHTML = history.map(item => `<li>${item}</li>`).join('');
        const total = history.reduce((sum, item) => sum + (parseInt(item) || 0), 0);
        document.getElementById("totalScore").innerText = total;
    }

    // Giả lập lưu trữ (Vì không có server, dữ liệu này sẽ lưu vào LocalStorage của trình duyệt bạn)
    function saveResult(res) {
        let allData = JSON.parse(localStorage.getItem('luckydraw_data') || '{}');
        if (!allData[currentUser]) allData[currentUser] = [];
        allData[currentUser].push(res);
        localStorage.setItem('luckydraw_data', JSON.stringify(allData));
        if(currentUser === "99999") loadGlobalData();
    }

    function loadGlobalData() {
        if (currentUser !== "99999") return;
        const allData = JSON.parse(localStorage.getItem('luckydraw_data') || '{}');
        let html = "<ul>";
        for (let user in allData) {
            html += `<li>Mã ${user}: ${allData[user].join(', ')}</li>`;
        }
        document.getElementById("allStats").innerHTML = html + "</ul>";
    }
</script>
</body>
</html>
