<!DOCTYPE html>
<html lang="gu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>અટેન્ડન્સ મેનેજર</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }
        body { background-color: #f2f2f7; padding: 20px; color: #1c1c1e; }
        
        .card {
            background: white;
            border-radius: 12px;
            padding: 16px;
            margin-bottom: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
        }
        
        h2 { text-align: center; margin-bottom: 15px; color: #007aff; }
        
        .input-group { display: flex; gap: 10px; margin-bottom: 15px; }
        input[type="text"] {
            flex: 1; padding: 12px; border: 1px solid #c7c7cc; border-radius: 8px; font-size: 16px;
        }
        
        button {
            background-color: #007aff; color: white; border: none; padding: 12px;
            border-radius: 8px; font-weight: bold; font-size: 16px; cursor: pointer;
        }
        
        .student-item {
            display: flex; justify-content: space-between; align-items: center;
            padding: 12px 0; border-bottom: 1px solid #e5e5ea;
        }
        .student-item:last-child { border-bottom: none; }
        
        .btn-group { display: flex; gap: 8px; }
        .btn-p { background-color: #34c759; padding: 8px 12px; font-size: 14px; }
        .btn-a { background-color: #ff3b30; padding: 8px 12px; font-size: 14px; }
        .status { font-weight: bold; font-size: 14px; }
        .present { color: #34c759; }
        .absent { color: #ff3b30; }
    </style>
</head>
<body>

    <h2>📋 હાજરી પત્રક</h2>

    <!-- નામ ઉમેરવા માટે -->
    <div class="card">
        <div class="input-group">
            <input type="text" id="nameInput" placeholder="નામ લખો...">
            <button onclick="addPerson()">ઉમેરો</button>
        </div>
    </div>

    <!-- લિસ્ટ -->
    <div class="card">
        <div id="list"></div>
    </div>

    <script>
        let data = JSON.parse(localStorage.getItem('attendance')) || [];

        function render() {
            const list = document.getElementById('list');
            if (data.length === 0) {
                list.innerHTML = "<p style='text-align:center; color:#8e8e93;'>કોઈ નામ ઉમેરેલું નથી.</p>";
                return;
            }
            list.innerHTML = '';
            data.forEach((item, index) => {
                list.innerHTML += `
                    <div class="student-item">
                        <div>
                            <strong>${item.name}</strong><br>
                            <span class="status ${item.status === 'હાજર' ? 'present' : item.status === 'ગેરહાજર' ? 'absent' : ''}">
                                ${item.status || 'બાકી'}
                            </span>
                        </div>
                        <div class="btn-group">
                            <button class="btn-p" onclick="setStatus(${index}, 'હાજર')">P</button>
                            <button class="btn-a" onclick="setStatus(${index}, 'ગેરહાજર')">A</button>
                        </div>
                    </div>
                `;
            });
        }

        function addPerson() {
            const input = document.getElementById('nameInput');
            if (input.value.trim() === '') return;
            data.push({ name: input.value, status: '' });
            input.value = '';
            saveAndRender();
        }

        function setStatus(index, status) {
            data[index].status = status;
            saveAndRender();
        }

        function saveAndRender() {
            localStorage.setItem('attendance', JSON.stringify(data));
            render();
        }

        render();
    </script>
</body>
</html>
