# This project is all about basics of JsonPowerDB (JPDB) and how to use JPDB for CRUD operations.

# About JsonPowerDB:
JsonPowerDB is a Real-time, High Performance, Lightweight and Simple to Use, Rest API based Multi-mode DBMS. JsonPowerDB has ready to use API for Json document DB, RDBMS, Key-value DB, GeoSpatial DB and Time Series DB functionality. JPDB supports and advocates for true serverless and pluggable API development.

# Benefits of using JsonPowerDB
Simplest way to retrieve data in a JSON format.
Schema-free, Simple to use, Nimble and In-Memory database.
It is built on top of one of the fastest and real-time data indexing engine - PowerIndeX.
It is low level (raw) form of data and is also human readable.
It helps developers in faster coding, in-turn reduces development cost.

# Screenshots:
![Screenshot (72)](https://user-images.githubusercontent.com/59838695/107753809-9c28f400-6d46-11eb-8376-3d697b30d4d4.png)

# JPDB Code Used
$("#submitsignup").click(function(){

        document.getElementById("error").style.display = "none";

        var email = $("#emailsignup").val();
        var password = $("#passwordsignup").val();
        var hidden = $("#hiddensignup").val();

        if(email === "" || password === "")
        {
            document.getElementById("error").style.display = "block";
        }
        else
        {
            var jsonstring = {
                playeremail : email,
                playerpassword : password
            };

            var jsonStr = JSON.stringify(jsonstring);
            
            var putReq = createPUTRequest("90935430|-31948797722490438|90931893", jsonStr, "game", "game-player");

            jQuery.ajaxSetup({async:false});
            var resultObj = executeCommandAtGivenBaseUrl(putReq, "http://api.login2explore.com:5577", "/api/iml");
            jQuery.ajaxSetup({async : true});

            <?php $_SESSION['variable'] = "curr";
                setcookie("variable", "curr", time()+60*60*24*365);
             ?>

            window.location.href = "nextpage.php";
        }
    });

    $("#submitlogin").click(function(){
        
        document.getElementById("error").style.display = "none";
        var email = $("#emaillogin").val();
        var password = $("#passwordlogin").val();
        var hidden = $("#hiddenlogin").val();
        
        if(email === "" || password === "")
        {
            document.getElementById("error").style.display = "block";
        } 
        else
        {
            
            var jsonstring = {
                playeremail : email,
                playerpassword : password
            };

            var jsonStr = JSON.stringify(jsonstring);

            var getReq = createGETRequest("90935430|-31948797722490438|90931893", "game", "game-player", jsonStr);

            jQuery.ajaxSetup({async:false});
            var resultObj = executeCommandAtGivenBaseUrl(getReq, "http://api.login2explore.com:5577", "/api/irl");
            jQuery.ajaxSetup({async : true});

            if(resultObj.message === "DATA NOT FOUND")
            {
                document.getElementById("error").innerHTML = "Incorrect Email / Password";
                document.getElementById("error").style.display = "block";   
            }
            else
            {
                <?php $_SESSION['variable'] = "curr";
                setcookie("variable", "curr", time()+60*60*24*365);
                 ?>
                window.location.href = "nextpage.php";
            }
        }
    });

