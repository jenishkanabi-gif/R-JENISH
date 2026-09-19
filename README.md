<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>R Jenish Dashboard</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: #0b1320;
            color: #ffffff;
            display: flex;
            justify-content: center;
        }

        .app-container {
            width: 100%;
            max-width: 414px;
            background-color: #0d1829;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            position: relative;
            padding-bottom: 70px;
        }

        /* Header */
        .header {
            padding: 15px 20px 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .brand-logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .brand-logo span {
            font-size: 24px;
            font-weight: 800;
            letter-spacing: 1px;
            color: #d1d5db;
        }

        .brand-logo .logo-r {
            color: #f59e0b;
            font-size: 28px;
            font-weight: 900;
        }

        .sub-nav {
            font-size: 12px;
            color: #9ca3af;
            margin-top: 2px;
        }

        .header-icons {
            display: flex;
            gap: 15px;
            align-items: center;
            cursor: pointer;
        }

        .notification-icon {
            position: relative;
        }

        .badge {
            position: absolute;
            top: -5px;
            right: -5px;
            background-color: #ef4444;
            color: white;
            border-radius: 50%;
            padding: 2px 5px;
            font-size: 10px;
            font-weight: bold;
        }

        /* Banner Section */
        .hero-section {
            position: relative;
            margin: 10px 15px;
            border-radius: 16px;
            overflow: hidden;
            height: 200px;
            background: linear-gradient(to right, rgba(0,0,0,0.7), transparent), url('https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&w=800&q=80') center/cover;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 20px;
        }

        .greeting {
            color: #e5e7eb;
            font-size: 14px;
        }

        .user-name {
            font-size: 22px;
            font-weight: bold;
            margin-top: 2px;
        }

        .tagline {
            font-size: 11px;
            color: #d1d5db;
            margin-top: 4px;
        }

        .date-badge {
            position: absolute;
            right: 15px;
            bottom: 15px;
            background: rgba(17, 24, 39, 0.85);
            backdrop-filter: blur(4px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 8px 12px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .date-text {
            font-size: 10px;
            color: #9ca3af;
        }

        .date-value {
            font-size: 12px;
            font-weight: bold;
            color: #fff;
        }

        /* Grid Options */
        .grid-container {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
            padding: 10px 15px;
        }

        .grid-card {
            background-color: #172337;
            border-radius: 12px;
            padding: 12px 5px;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            border: 1px solid rgba(255,255,255,0.05);
            cursor: pointer;
            transition: transform 0.2s, background-color 0.2s;
        }

        .grid-card:active {
            transform: scale(0.95);
            background-color: #1e2d47;
        }

        .icon-box {
            width: 42px;
            height: 42px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            margin-bottom: 8px;
        }

        .card-title {
            font-size: 11px;
            font-weight: 600;
            color: #f3f4f6;
        }

        .card-subtitle {
            font-size: 8px;
            color: #9ca3af;
            margin-top: 2px;
        }

        /* Icon Colors */
        .bg-green { background: #059669; color: white; }
        .bg-blue { background: #2563eb; color: white; }
        .bg-purple { background: #7c3aed; color: white; }
        .bg-orange { background: #d97706; color: white; }
        .bg-red { background: #dc2626; color: white; }
        .bg-teal { background: #0d9488; color: white; }
        .bg-indigo { background: #4f46e5; color: white; }
        .bg-sky { background: #0284c7; color: white; }

        /* Report Banner Card */
        .banner-card {
            margin: 10px 15px;
            background: linear-gradient(135deg, #1e1b4b 0%, #1e293b 100%);
            border-radius: 12px;
            padding: 15px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border: 1px solid rgba(255, 255, 255, 0.08);
            cursor: pointer;
        }

        .banner-left {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .banner-icon {
            background-color: #6366f1;
            width: 40px;
            height: 40px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
        }

        .banner-title {
            font-size: 14px;
            font-weight: bold;
            margin-bottom: 4px;
        }

        .banner-desc {
            font-size: 10px;
            color: #9ca3af;
            line-height: 1.4;
        }

        /* Bottom Nav */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            width: 100%;
            max-width: 414px;
            background-color: #0b1320;
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            z-index: 10;
        }

        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            color: #6b7280;
            font-size: 10px;
            gap: 4px;
            text-decoration: none;
            cursor: pointer;
        }

        .nav-item.active {
            color: #3b82f6;
        }

        .nav-item i {
            font-size: 18px;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 100;
            justify-content: center;
            align-items: flex-end;
        }

        .modal-content {
            width: 100%;
            max-width: 414px;
            background-color: #111827;
            border-top-left-radius: 20px;
            border-top-right-radius: 20px;
            padding: 20px;
            max-height: 80vh;
            overflow-y: auto;
            border-top: 1px solid rgba(255,255,255,0.1);
            animation: slideUp 0.3s ease-out;
        }

        @keyframes slideUp {
            from { transform: translateY(100%); }
            to { transform: translateY(0); }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            border-bottom: 1px solid #1f2937;
            padding-bottom: 10px;
        }

        .modal-title {
            font-size: 18px;
            font-weight: bold;
            color: #3b82f6;
        }

        .close-btn {
            font-size: 20px;
            color: #9ca3af;
            cursor: pointer;
        }

        .form-group {
            margin-bottom: 12px;
        }

        .form-group label {
            display: block;
            font-size: 12px;
            color: #9ca3af;
            margin-bottom: 5px;
        }

        .form-control {
            width: 100%;
            padding: 10px;
            background: #1f2937;
            border: 1px solid #374151;
            border-radius: 8px;
            color: white;
            font-size: 14px;
        }

        .btn-submit {
            width: 100%;
            padding: 12px;
            background-color: #2563eb;
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 10px;
        }

        .data-list {
            margin-top: 15px;
            max-height: 200px;
            overflow-y: auto;
        }

        .data-item {
            background: #1f2937;
            padding: 10px;
            border-radius: 6px;
            margin-bottom: 8px;
            font-size: 12px;
            display: flex;
            justify-content: space-between;
        }
    </style>
</head>
<body>

<div class="app-container">
    <!-- Header -->
    <div class="header">
        <div>
            <div class="brand-logo">
                <span class="logo-r">R</span>
                <span>JENISH</span>
            </div>
            <div class="sub-nav">Attendance • Salary • Reports • More</div>
        </div>
        <div class="header-icons">
            <div class="notification-icon" onclick="openModal('Notifications', 'તમારી પાસે 3 અગત્યની નોટિફિકેશન છે.')">
                <i class="fa-regular fa-bell" style="font-size: 20px;"></i>
                <span class="badge">3</span>
            </div>
            <i class="fa-solid fa-gear" style="font-size: 20px;" onclick="openModal('Settings', 'અહીંથી તમે એપ્લિકેશન સેટિંગ્સ બદલી શકો છો.')"></i>
        </div>
    </div>

    <!-- User Profile Banner -->
    <div class="hero-section">
        <div>
            <div class="greeting">Good Morning ☀️</div>
            <div class="user-name">R Jenish</div>
            <div class="tagline">Work Hard | Stay Positive | Grow Together</div>
        </div>
        <div class="date-badge">
            <i class="fa-regular fa-calendar-days" style="font-size: 20px; color: #3b82f6;"></i>
            <div>
                <div class="date-text">Today</div>
                <div class="date-value" id="currentDate">15 Sep 2026</div>
            </div>
        </div>
    </div>

    <!-- Grid Menu Options -->
    <div class="grid-container">
        <div class="grid-card" onclick="openAttendanceModal()">
            <div class="icon-box bg-green"><i class="fa-solid fa-calendar-check"></i></div>
            <div class="card-title">Attendance</div>
            <div class="card-subtitle">Mark / View</div>
        </div>
        <div class="grid-card" onclick="openEmployeeModal()">
            <div class="icon-box bg-blue"><i class="fa-solid fa-user-group"></i></div>
            <div class="card-title">Employees</div>
            <div class="card-subtitle">Manage Staff</div>
        </div>
        <div class="grid-card" onclick="openSalaryModal()">
            <div class="icon-box bg-purple"><i class="fa-solid fa-indian-rupee-sign"></i></div>
            <div class="card-title">Salary</div>
            <div class="card-subtitle">Calculate / View</div>
        </div>
        <div class="grid-card" onclick="openModal('Salary Slip', 'પગાર સ્લિપ જનરેટ કરવા માટે કર્મચારી પસંદ કરો.')">
            <div class="icon-box bg-orange"><i class="fa-solid fa-file-lines"></i></div>
            <div class="card-title">Salary Slip</div>
            <div class="card-subtitle">Generate / Share</div>
        </div>
        <div class="grid-card" onclick="openExpenseModal()">
            <div class="icon-box bg-red"><i class="fa-solid fa-wallet"></i></div>
            <div class="card-title">Expenses</div>
            <div class="card-subtitle">Add / View</div>
        </div>
        <div class="grid-card" onclick="openModal('Reports', 'અહીંથી તમામ રિપોર્ટ જોઈ અને PDF/Excel ડાઉનલોડ કરી શકાશે.')">
            <div class="icon-box bg-teal"><i class="fa-solid fa-chart-column"></i></div>
            <div class="card-title">Reports</div>
            <div class="card-subtitle">View / Export</div>
        </div>
        <div class="grid-card" onclick="openModal('Overtime', 'ઓવરટાઇમ ટ્રેક કરવા માટે અહીં કલાકો નોંધો.')">
            <div class="icon-box bg-indigo"><i class="fa-regular fa-clock"></i></div>
            <div class="card-title">Overtime</div>
            <div class="card-subtitle">Track Hours</div>
        </div>
        <div class="grid-card" onclick="openModal('Backup', 'તમારો તમામ ડેટા સલામત રીતે સેવ થઈ ગયો છે.')">
            <div class="icon-box bg-sky"><i class="fa-solid fa-cloud"></i></div>
            <div class="card-title">Backup</div>
            <div class="card-subtitle">Save Data</div>
        </div>
    </div>

    <!-- Reports Section Banner -->
    <div class="banner-card" onclick="openModal('Reports & Statement', 'તમામ પ્રકારના સ્ટેટમેન્ટ અને સમરી જોવા મળશે.')">
        <div class="banner-left">
            <div class="banner-icon"><i class="fa-solid fa-chart-line"></i></div>
            <div>
                <div class="banner-title">Reports & Statement</div>
                <div class="banner-desc">Date-wise • Employee-wise • Shift-wise • Job-wise<br>Name-wise • Monthly • Status-wise • PDF / Excel</div>
            </div>
        </div>
        <i class="fa-solid fa-chevron-right" style="color: #9ca3af;"></i>
    </div>

    <!-- Navigation Bar -->
    <div class="bottom-nav">
        <a class="nav-item active" onclick="closeModal()">
            <i class="fa-solid fa-house"></i>
            <span>Home</span>
        </a>
        <a class="nav-item" onclick="openAttendanceModal()">
            <i class="fa-solid fa-list-check"></i>
            <span>Attendance</span>
        </a>
        <a class="nav-item" onclick="openEmployeeModal()">
            <i class="fa-solid fa-users"></i>
            <span>Employees</span>
        </a>
        <a class="nav-item" onclick="openSalaryModal()">
            <i class="fa-solid fa-indian-rupee-sign"></i>
            <span>Salary</span>
        </a>
        <a class="nav-item" onclick="openModal('More Features', 'અન્ય ઉપયોગી ફીચર્સ ટૂંક સમયમાં ઉમેરાશે.')">
            <i class="fa-solid fa-ellipsis"></i>
            <span>More</span>
        </a>
    </div>
</div>

<!-- Dynamic Modal Popup -->
<div class="modal" id="appModal">
    <div class="modal-content">
        <div class="modal-header">
            <div class="modal-title" id="modalTitle">Title</div>
            <div class="close-btn" onclick="closeModal()">&times;</div>
        </div>
        <div id="modalBody">
            <!-- Dynamic Content -->
        </div>
    </div>
</div>

<script>
    // Set Current Date Automatically
    const today = new Date();
    const options = { day: 'numeric', month: 'short', year: 'numeric' };
    document.getElementById('currentDate').innerText = today.toLocaleDateString('en-GB', options);

    // Dynamic Modal Open/Close Logic
    function openModal(title, contentHtml) {
        document.getElementById('modalTitle').innerText = title;
        document.getElementById('modalBody').innerHTML = typeof contentHtml === 'string' ? `<p style="font-size: 14px; color: #d1d5db;">${contentHtml}</p>` : '';
        document.getElementById('appModal').style.display = 'flex';
    }

    function closeModal() {
        document.getElementById('appModal').style.display = 'none';
    }

    // Attendance Function
    function openAttendanceModal() {
        openModal('Attendance System', '');
        const employees = JSON.parse(localStorage.getItem('employees') || '[]');
        let html = `
            <div class="form-group">
                <label>તારીખ પસંદ કરો:</label>
                <input type="date" class="form-control" id="attDate" value="${new Date().toISOString().split('T')[0]}">
            </div>
            <div class="form-group">
                <label>કર્મચારી પસંદ કરો:</label>
                <select class="form-control" id="attEmp">
                    ${employees.map(e => `<option value="${e.name}">${e.name}</option>`).join('') || '<option>કોઈ કર્મચારી ઉમેરેલ નથી</option>'}
                </select>
            </div>
            <div class="form-group">
                <label>સ્ટેટસ:</label>
                <select class="form-control" id="attStatus">
                    <option value="Present">Present (હાજર)</option>
                    <option value="Absent">Absent (ગેરહાજર)</option>
                    <option value="Half Day">Half Day (અડધો દિવસ)</option>
                </select>
            </div>
            <button class="btn-submit" onclick="saveAttendance()">હાજરી સબમિટ કરો</button>
            <div class="data-list" id="attList"></div>
        `;
        document.getElementById('modalBody').innerHTML = html;
        renderAttendance();
    }

    function saveAttendance() {
        const emp = document.getElementById('attEmp').value;
        const date = document.getElementById('attDate').value;
        const status = document.getElementById('attStatus').value;

        if(!emp) return alert('મહેરબાની કરીને કર્મચારી ઉમેરો!');

        let list = JSON.parse(localStorage.getItem('attendance') || '[]');
        list.push({ emp, date, status });
        localStorage.setItem('attendance', JSON.stringify(list));
        alert('હાજરી નોંધાઈ ગઈ!');
        renderAttendance();
    }

    function renderAttendance() {
        let list = JSON.parse(localStorage.getItem('attendance') || '[]');
        let html = list.map(a => `<div class="data-item"><span>${a.emp} (${a.date})</span><b style="color:${a.status === 'Present' ? '#10b981' : '#ef4444'}">${a.status}</b></div>`).join('');
        document.getElementById('attList').innerHTML = html;
    }

    // Employees Function
    function openEmployeeModal() {
        openModal('Manage Employees', '');
        let html = `
            <div class="form-group">
                <label>કર્મચારીનું નામ:</label>
                <input type="text" class="form-control" id="empName" placeholder="દા.ત. Ramesh Kumar">
            </div>
            <div class="form-group">
                <label>મોબાઈલ નંબર:</label>
                <input type="number" class="form-control" id="empPhone" placeholder="10 અંકનો નંબર">
            </div>
            <div class="form-group">
                <label>દૈનિક પગાર (Daily Salary):</label>
                <input type="number" class="form-control" id="empSalary" placeholder="દા.ત. 500">
            </div>
            <button class="btn-submit" onclick="saveEmployee()">કર્મચારી ઉમેરો</button>
            <div class="data-list" id="empList"></div>
        `;
        document.getElementById('modalBody').innerHTML = html;
        renderEmployees();
    }

    function saveEmployee() {
        const name = document.getElementById('empName').value;
        const phone = document.getElementById('empPhone').value;
        const salary = document.getElementById('empSalary').value;

        if(!name || !salary) return alert('નામ અને પગાર ઉમેરવો ફરજિયાત છે!');

        let list = JSON.parse(localStorage.getItem('employees') || '[]');
        list.push({ name, phone, salary });
        localStorage.setItem('employees', JSON.stringify(list));
        alert('કર્મચારી સફળતાપૂર્વક ઉમેરાઈ ગયો!');
        renderEmployees();
    }

    function renderEmployees() {
        let list = JSON.parse(localStorage.getItem('employees') || '[]');
        let html = list.map(e => `<div class="data-item"><span><b>${e.name}</b> (${e.phone || 'No Phone'})</span><span>₹${e.salary}/day</span></div>`).join('');
        document.getElementById('empList').innerHTML = html;
    }

    // Salary Calculator Function
    function openSalaryModal() {
        openModal('Salary Calculation', '');
        const employees = JSON.parse(localStorage.getItem('employees') || '[]');
        let html = `
            <div class="form-group">
                <label>કર્મચારી પસંદ કરો:</label>
                <select class="form-control" id="salEmp">
                    ${employees.map(e => `<option value="${e.salary}">${e.name} (₹${e.salary}/day)</option>`).join('') || '<option>કોઈ કર્મચારી નથી</option>'}
                </select>
            </div>
            <div class="form-group">
                <label>કુલ કામના દિવસો (Working Days):</label>
                <input type="number" class="form-control" id="salDays" placeholder="દા.ત. 26">
            </div>
            <button class="btn-submit" onclick="calcSalary()">પગારની ગણતરી કરો</button>
            <div id="salResult" style="margin-top:15px; font-weight:bold; color:#10b981; font-size:16px;"></div>
        `;
        document.getElementById('modalBody').innerHTML = html;
    }

    function calcSalary() {
        const dailyRate = parseFloat(document.getElementById('salEmp').value);
        const days = parseFloat(document.getElementById('salDays').value);
        if(!dailyRate || !days) return alert('બધી માહિતી દાખલ કરો!');
        const total = dailyRate * days;
        document.getElementById('salResult').innerText = `કુલ પગાર: ₹ ${total.toLocaleString('en-IN')}`;
    }

    // Expense Tracker Function
    function openExpenseModal() {
        openModal('Expenses Management', '');
        let html = `
            <div class="form-group">
                <label>ખર્ચની વિગત (Expense Title):</label>
                <input type="text" class="form-control" id="expTitle" placeholder="દા.ત. ચા-નાસ્તો, ચા-પાણી, પેટ્રોલ">
            </div>
            <div class="form-group">
                <label>રકમ (Amount ₹):</label>
                <input type="number" class="form-control" id="expAmount" placeholder="દા.ત. 250">
            </div>
            <button class="btn-submit" onclick="saveExpense()">ખર્ચ ઉમેરો</button>
            <div class="data-list" id="expList"></div>
        `;
        document.getElementById('modalBody').innerHTML = html;
        renderExpenses();
    }

    function saveExpense() {
        const title = document.getElementById('expTitle').value;
        const amount = document.getElementById('expAmount').value;

        if(!title || !amount) return alert('વિગત અને રકમ દાખલ કરો!');

        let list = JSON.parse(localStorage.getItem('expenses') || '[]');
        list.push({ title, amount, date: new Date().toLocaleDateString('en-GB') });
        localStorage.setItem('expenses', JSON.stringify(list));
        alert('ખર્ચ ઉમેરાઈ ગયો!');
        renderExpenses();
    }

    function renderExpenses() {
        let list = JSON.parse(localStorage.getItem('expenses') || '[]');
        let html = list.map(x => `<div class="data-item"><span>${x.title} (${x.date})</span><b style="color:#ef4444">₹${x.amount}</b></div>`).join('');
        document.getElementById('expList').innerHTML = html;
    }
</script>

</body>
</html>
