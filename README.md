
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>to do list</title>
    <style>
        body{
            background-color: yellow;
        }
        input{
            height: 30px;
            width: 200px;
            border: 2px solid;
            font-size: 20px;
        }
        button{
            height: 37px;
            width: 100px;
            border-radius: 20px;
            
        }
        .a{
            background-color: pink
            
        }
        
        
    </style>
</head>

<body>
    <input type="text" placeholder="enter name" id="name">
    <input type="number" placeholder="enter age" id="age">
    <button class="a" onclick="myevent()">Add</button>
    <ul id="list"></ul>
    <script>
        let item = [];
        let editIndex = -1;
        function myevent() {
            let name = document.getElementById("name").value;
            let age = document.getElementById("age").value;
            if (editIndex === -1) {
            item.push({ name: name, age: age });
            } else {
                item[editIndex] = { name: name, age: age };
            editIndex = -1;
            }
            document.getElementById("name").value = "";
            document.getElementById("age").value = "";
            renderList();
        }
        function renderList() {
            const list = document.getElementById('list');
            list.innerHTML = "";
            item.forEach((item, index) => {
                list.innerHTML += `
        <li>${item.name} ${item.age}
        <button onclick="deletItem(${index})">delete</button>
        <button onclick="editItem(${index})">edit</button>
        </li>
        `
            })
        }
        function deletItem(index) {
            item.splice(index, 1);
            renderList();
        }
        function editItem(index){
            document.getElementById("name").value = item[index].name;
            document.getElementById("age").value = item[index].age;
            editIndex = index;
        }
        
    </script>
    
</body>

</html>
