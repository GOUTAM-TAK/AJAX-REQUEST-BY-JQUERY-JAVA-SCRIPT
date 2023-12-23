AJAX REUEST SEND AND HANDLE - DISPLAY IN TABLE FORMAT USING APPEND PREPPEND FUNCTION 

<!DOCTYPE html>
<head>
    <title>AJAX REQUEST</title>
    <script src="C:\\Users\\acts\\Desktop\\AAYUSH-GOUTAM\\WPT\\Class WorkSpace\\scripts\\jquery.js"></script>
<script>
    function display(data){
        str="<table border='2'><tr><th>userId</th><th>id</th><th>title</th><th>body</th></tr>"
        for(var ob of data){
            str+=`<tr><td>${ob.partyName}</td><td>${ob.partyId}</td><td>${ob.leaderName}</td><td>${ob.email}</td></tr>`
        }
        str+="</table>"
        $('#mydiv').html(str);
    }
    function displayappend(data){
        str="<table class='app' border='2'><tr><th>userId</th><th>id</th><th>title</th><th>body</th></tr>"
        for(var ob of data){
            str+=`<tr><td>${ob.firstName}</td><td>${ob.partyId}</td><td>${ob.lastName}</td><td>${ob.email}</td></tr>`
        }
        str+="</table>"
        $(`body`).append(str);
    }

 function   displayPreppend(data){
           str = "<table class='pre' border=2><th>VoterId</th><th>firstName</th><th>ConstituencyId</th><th>email</th><th>VotingStatus</th>"
            for(var ob of data){
               str+=`<tr><td>${ob.id}</td><td>${ob.firstName}</td><td>${ob.constituencyId}</td><td>${ob.email}</td><td>${ob.isVoted}</td></tr>`
            }
            str+="</table>"
            $(`#mydiv`).prepend(str);
    }

        $(document).ready(function(){
            $(`#btn`).click(function(){ //tag selector
                $.ajax({
                    async : true,
                   url : "http://localhost:5106/api/Parties",
                   type : "GET",
                   success : function(result){display(result)},
                   error : function(error){
                    console.log("error is this",error)
                   }
                }) })
            
                   $(`#btn1`).click(function(){ //tag selector
                $.ajax({
                    async : true,
                   url : "http://localhost:5106/api/Candidates",
                   type : "GET",
                   success : function(result){displayappend(result)},
                   error : function(error){
                    console.log("error is this",error)
                   }
            })
                   })
            $(`#btn2`).click(function(){
                $.ajax({
                    async : true,
                    url : "http://localhost:5106/api/Voters",
                    type : "GET",
                    success : function(result){displayPreppend(result)},
                    error : function(error){
                        console.log("this is error",error)
                    }
                })
            })

          
                $(`#btn3`).click(function(){
                    $(`table`).remove(".app")
                })
                $(`#btn4`).click(function(){
                    $(`table`).remove(".pre")
                })

                })
</script>
</head>
<body>
    <input type="button" id="btn" value="display" />
    <input type="button" id ="btn1" value="append"/>
    <input type="button" id="btn2" value="preppend"/>
    <input type="button" id="btn3" value="removeAppend"/>
    <input type="button" id="btn4" value="removePreppend"/>
    <div id="mydiv">

    </div>
</body>
</html>
