
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Attendance System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
        }
        header {
            background-color: #007BFF;
            color: white;
            padding: 1rem 0;
            text-align: center;
        }
        .container {
            max-width: 600px;
            margin: 2rem auto;
            background: #ffffff;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        .form-group {
            margin-bottom: 1rem;
        }
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }
        .form-group input, .form-group select {
            width: 100%;
            padding: 0.5rem;
            font-size: 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        button {
            background-color: #007BFF;
            color: white;
            padding: 0.75rem 1.5rem;
            font-size: 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .footer {
            text-align: center;
            margin-top: 1rem;
            font-size: 0.9rem;
            color: #666;
        }
        table {
            width: 100%;
            margin-top: 2rem;
            border-collapse: collapse;
        }
        table, th, td {
            border: 1px solid #ddd;
        }
        th, td {
            padding: 0.5rem;
            text-align: center;
        }
        th {
            background-color: #007BFF;
            color: white;
        }
    </style>
</head>
<body>
    <header>
        <h1>Electronics Shop Attendance</h1>
    </header>
    <div class="container">
        <form id="attendance-form">
            <div class="form-group">
                <label for="employee-name">Employee Name</label>
                <input type="text" id="employee-name" name="employeeName" required>
            </div>
            <div class="form-group">
                <label for="attendance-status">Attendance Status</label>
                <select id="attendance-status" name="attendanceStatus" required>
                    <option value="Present">Present</option>
                    <option value="Absent">Absent</option>
                    <option value="On Leave">On Leave</option>
                </select>
            </div>
            <button type="submit">Submit Attendance</button>
        </form>

        <!-- Table to Display Saved Attendance -->
        <table id="attendance-table">
            <thead>
                <tr>
                    <th>Date</th>
                    <th>Employee Name</th>
                    <th>Status</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>

    <script>
        document.getElementById('attendance-form').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form from reloading the page

            const name = document.getElementById('employee-name').value;
            const status = document.getElementById('attendance-status').value;

            // Get current date in format YYYY-MM-DD
            const date = new Date().toISOString().split('T')[0];

            // Append data to the table
            const tableBody = document.querySelector('#attendance-table tbody');
            const newRow = document.createElement('tr');
            newRow.innerHTML = `
                <td>${date}</td>
                <td>${name}</td>
                <td>${status}</td>
            `;
            tableBody.appendChild(newRow);

            // Clear the form fields
            document.getElementById('attendance-form').reset();
        });
    </script>
</body>
</html>
