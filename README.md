<!DOCTYPE html>
<html>
<head>
<title>Contribution Sorter</title>

<style>
body{
font-family: Arial;
background:#f4f4f4;
text-align:center;
}

.container{
background:white;
padding:20px;
width:400px;
margin:auto;
margin-top:50px;
border-radius:10px;
box-shadow:0 0 10px rgba(0,0,0,0.2);
}

input{
padding:8px;
margin:5px;
}

button{
padding:8px 15px;
background:#007bff;
color:white;
border:none;
cursor:pointer;
}

table{
width:100%;
margin-top:20px;
border-collapse:collapse;
}

th,td{
padding:8px;
border-bottom:1px solid #ddd;
}

</style>
</head>

<body>

<div class="container">

<h2>Amount Leaderboard</h2>

<input type="text" id="name" placeholder="Enter Name">
<input type="number" id="amount" placeholder="Enter Amount">

<br><br>

<button onclick="addData()">Add</button>

<table id="table">
<tr>
<th>Name</th>
<th>Amount</th>
</tr>
</table>

</div>

<script>

let data=[];

function addData(){

let name=document.getElementById("name").value;
let amount=parseInt(document.getElementById("amount").value);

if(name=="" || amount==""){
alert("Enter name and amount");
return;
}

data.push({name:name,amount:amount});

data.sort(function(a,b){

if(b.amount===a.amount){
return a.name.localeCompare(b.name);
}

return b.amount-a.amount;

});

display();

}

function display(){

let table=document.getElementById("table");

table.innerHTML="<tr><th>Name</th><th>Amount</th></tr>";

for(let i=0;i<data.length;i++){

table.innerHTML+=
"<tr><td>"+data[i].name+"</td><td>"+data[i].amount+"</td></tr>";

}

}

</script>

</body>
</html>
