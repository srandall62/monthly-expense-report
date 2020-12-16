# monthly expense report
 <!DOCTYPE html>
<html>

<head>
    <title>Expense Report</title>
    <style>
        body {
            background: rgb(136, 136, 206);
        }
        
        h1 {
            text-align: center;
            color: navy;
            border-bottom: 5px double navy;
        }
        
        #divider {
            border: 10px double navy;
            margin-bottom: 30px;
        }
        
        table {
            border: 2px double navy;
            text-align: center;
            margin-left: auto;
            margin-right: auto;
        }
        
        th {
            display: relative;
            min-width: 150px;
            margin-top: 20px;
            padding-right: 100px;
            border: 2px double navy;
        }
        
        td {
            border-bottom: 2px double navy;
        }
        
        #expname {
            display: absolute;
            margin-left: 100px;
        }
        
        #incoming {
            display: absolute;
            margin-left: 130px;
        }
        
        p {
            display: absolute;
            margin-left: 100px;
            font-size: 20px;
        }
    </style>
</head>

<body id="main">
    <h1>Monthly Expense Report</h1>
    <div>
        <form id="incoming">
            <input type="integer" id="income" placeholder="Amount of Income">
            <select name="freq" id="freq">
                <option value="weekly" id="weekly">Weekly</option>
                <option value="bi-weekly" id="biWeekly">Bi-Weekly</option>
                <option value="monthly" id="monthly">Monthly</option>
            </select>
            <input type="button" id="pay" onClick="addIncome()" value="Add">
            <input type="button" id="additional" onClick="additional()" value="Add an Income">
        </form>
    </div>
    <div id="divider"></div>
    <input type="text" id="expname" placeholder="Name of Expense">
    <input type="number" id="expamt" placeholder="Amount Due">
    <input type="date" id="due">
    <input type="button" value="Add Expense" onClick="addRow()" id="add">
    <div id="divider"></div>

    <table id="tbody">
        <thead>
            <th id="noe">Name of Expense</th>
            <th id="ad">Amount Due</th>
            <th id="dd">Date Due</th>
        </thead>
        <tbody id="table-body">
            <td></td>
            <td></td>
            <td></td>
        </tbody>
    </table>
    <p id="totalIncome"></p>


    <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.4/jquery.min.js"></script>
    <script>
        function addRow() {
            "use strict";
            var tableBody = document.getElementById("table-body");
            var td1 = document.createElement("td");
            var td2 = document.createElement("td");
            var td3 = document.createElement("td");
            var row = document.createElement("tr");
            td1.innerHTML = document.getElementById("expname").value;
            td2.innerHTML = document.getElementById("expamt").value;
            td3.innerHTML = document.getElementById("due").value;
            row.appendChild(td1);
            row.appendChild(td2);
            row.appendChild(td3);
            tableBody.appendChild(row);
        }

        var total;

        function addIncome() {
            "use strict";
            var income = document.getElementById("income").value;
            var frq = document.getElementById("freq").value;

            if (frq == "weekly") {
                total = income * 4;
            } else if (frq == "bi-weekly") {
                total = income * 2;
            } else if (frq == "monthly") {
                total = income;
            }
            document.getElementById("totalIncome").innerHTML = "Your total monthly income is; " + total;
        }
        var sumTotal;
        var subTotal;

        function additional() {
            var income = document.getElementById("income").value;
            var frq = document.getElementById("freq").value;
            if (frq == "weekly") {
                subTotal = income * 4;
            } else if (frq == "bi-weekly") {
                subTotal = income * 2;
            } else if (frq == "monthly") {
                subTotal = income;
            }
            sumTotal = total + subTotal;
            document.getElementById("totalIncome").innerHTML = "Your adjusted monthly total income is; " + sumTotal;
        }
    </script>
</body>

</html>
