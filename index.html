<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Global Attendance Tracker</title>
    <style>
        body { font-family: -apple-system, sans-serif; background: #f4f7f6; margin: 0; padding: 15px; }
        .container { max-width: 600px; margin: 0 auto; background: white; padding: 20px; border-radius: 20px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); }
        .clock { font-size: 2.2rem; font-weight: 800; color: #1a73e8; text-align: center; margin-bottom: 15px; }
        .hidden { display: none !important; }
        input { width: 100%; padding: 15px; border: 1px solid #ddd; border-radius: 10px; box-sizing: border-box; margin-bottom: 10px; font-size: 16px; }
        button { width: 100%; padding: 15px; border: none; border-radius: 10px; font-weight: bold; font-size: 16px; color: white; cursor: pointer; margin-bottom: 10px; }
        .btn-login { background: #1a73e8; }
        .btn-in { background: #34a853; width: 48%; display: inline-block; }
        .btn-out { background: #ea4335; width: 48%; display: inline-block; }
        .btn-logout { background: #666; font-size: 14px; margin-top: 20px; }
        .table-wrapper { width: 100%; overflow-x: auto; margin-top: 20px; }
        table { width: 100%; border-collapse: collapse; font-size: 12px; min-width: 350px; }
        th, td { border-bottom: 1px solid #eee; padding: 10px 4px; text-align: center; vertical-align: middle; }
        th { color: #666; font-weight: 600; background: #f9f9f9; white-space: nowrap; }
        /* 링크를 버튼처럼 스타일링 */
        .map-link { display: inline-block; padding: 8px 10px; background: #e8f0fe; color: #1a73e8; border-radius: 5px; text-decoration: none; font-weight: bold; font-size: 11px; border: 1px solid #1a73e8; }
        .admin-tag { background: #e8f0fe; color: #1a73e8; padding: 2px 6px; border-radius: 4px; font-size: 10px; vertical-align: middle; }
    </style>
</head>
<body>

<div class="container">
    <div id="clock" class="clock">00:00:00</div>
    <div id="login-form">
        <input type="text" id="username" placeholder="이름을 입력하세요">
        <button class="btn-login" onclick="login()">접속하기</button>
    </div>
    <div id="main-ui" class="hidden">
        <p style="text-align:center; margin-bottom: 15px;"><strong id="user-display"></strong> <span id="admin-badge" class="admin-tag hidden">관리자</span></p>
        <div style="display: flex; justify-content: space-between;">
            <button class="btn-in" onclick="record('출근')">출근하기</button>
            <button class="btn-out" onclick="record('퇴근')">퇴근하기</button>
        </div>
        <div class="table-wrapper">
            <table>
                <thead><tr><th>성함</th><th>구분</th><th>기록 시간</th><th>위치</th></tr></thead>
                <tbody id="list-body"></tbody>
            </table>
        </div>
        <button class="btn-logout" onclick="logout()">로그아웃</button>
    </div>
</div>

<script>
    let currentUser = "";
    let isAdmin = false;
    const STORAGE_KEY = "attendance_records_v13";

    setInterval(() => { document.getElementById('clock').innerText = new Date().toLocaleTimeString('ko-KR'); }, 1000);

    function login() {
        const val = document.getElementById('username').value.trim();
        if(!val) return alert("이름을 입력하세요.");
        currentUser = val;
        isAdmin = (val.toLowerCase() === 'admin');
        document.getElementById('login-form').classList.add('hidden');
        document.getElementById('main-ui').classList.remove('hidden');
        document.getElementById('user-display').innerText = currentUser;
        if(isAdmin) document.getElementById('admin-badge').classList.remove('hidden');
        render();
    }

    function logout() { if(confirm("로그아웃 하시겠습니까?")) location.reload(); }

    function record(type) {
        if (!navigator.geolocation) return alert("GPS 미지원 브라우저입니다.");
        navigator.geolocation.getCurrentPosition((pos) => {
            const timeString = new Date().toLocaleString('ko-KR', { month: 'numeric', day: 'numeric', weekday: 'short', hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false });
            const data = { name: currentUser, type: type, time: timeString, lat: pos.coords.latitude, lon: pos.coords.longitude };
            const logs = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
            logs.push(data);
            localStorage.setItem(STORAGE_KEY, JSON.stringify(logs));
            alert(type + " 완료!");
            render();
        }, (err) => { alert("위치 정보를 가져올 수 없습니다."); }, { enableHighAccuracy: true, timeout: 10000 });
    }

    function render() {
        const tbody = document.getElementById('list-body');
        tbody.innerHTML = "";
        const allLogs = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
        const displayData = isAdmin ? allLogs : allLogs.filter(log => log.name === currentUser);

        [...displayData].reverse().forEach(log => {
            const row = tbody.insertRow();
            row.insertCell(0).innerText = log.name;
            row.insertCell(1).innerText = log.type;
            row.insertCell(2).innerText = log.time;
            const locCell = row.insertCell(3);
            if(log.lat && log.lon) {
                // 핵심 수정: JS window.open 대신 표준 <a> 태그를 사용하여 브라우저 차단 회피
                const url = `https://google.com{log.lat},${log.lon}`;
                locCell.innerHTML = `<a href="${url}" target="_blank" rel="noopener noreferrer" class="map-link">지도보기</a>`;
            } else { locCell.innerText = "-"; }
        });
    }
</script>
</body>
</html>

