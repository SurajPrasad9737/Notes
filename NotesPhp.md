### dataaddProduct.php
<form action="" method="post">
    doctor_name: <input type="text" name="doc_name" id="doc_name">
    doctor_role : <input type="text" name="role" id="role">

    <button type="submit" >submit</button>

</form>

<?php
    include "database.php";
    $con= databaseConnection();
    if(isset($_POST)) {
        $doc_name = $_POST['doc_name'];
        $role = $_POST['role'];
        $query = "insert into doctos(doc_name, doc_role) values('$doc_name', '$role')";
            
        $result = mysqli_query($con, $query);
            
        if ($result) {
            echo "doctor inserted successfully";
        } else {
            echo "doctor cannot be inserted".mysqli_error($con);
        }

    }
?>

admin.php
<h1> I am admin </h1>

<a href="/addProduct.php">add details</a>


book.php
<?php
session_start();
$userid = intval($_SESSION['userid']);
echo $userid;
include "database.php";
$con = databaseConnection();
if (isset($_REQUEST)) {
    $doc_id = intval($_REQUEST['id']);
    $query = "insert into app values($userid, $doc_id)";
    $result = mysqli_query($con, $query);
    if ($result) {
        echo "Document added to your application";
        header("Location: welcome.php");
    } else {
        echo "Error adding document to your application";
    }
}


createCode.sh
for file in *; do
    if [ -f $file ]; then
        echo $file >> ./NotesPhp.md
        cat $file >> ./NotesPhp.md
        echo "
" >> ./NotesPhp.md
    fi
done


database.php
<?php
function databaseConnection(){
$servername="testhodb2.nj";
$username="trainee";
$password="tky4U63#MZjVqu";
$database="test_doom";
$con = mysqli_connect($servername,$username,$password,$database);
if(!$con){
   return false;
}else{
    return $con;
}
}

// databaseConnection();
?>

delete.php
<?php
    if($_REQUEST) {
        $userid = $_REQUEST['id'];
        include "database.php";
        $con = databaseConnection();
        $result = mysqli_query($con, "delete from app where userid=$userid");
        if ($result) {
            echo "deleted";
            header("Location: welcome.php");
        } else {
            echo "not deleted";
        }
    }




login.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .login-container {
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            margin-bottom: 20px;
        }
        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        input[type="submit"] {
            background-color: #5cb85c;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
        }
        input[type="submit"]:hover {
            background-color: #4cae4c;
        }
    </style>
</head>
<body>

<div class="login-container">
    <h2>Login</h2>
    <form action="/login.php" method="post">
        <label for="username">Username</label>
        <input type="text" id="username" name="username" required>

        <label for="password">Password</label>
        <input type="password" id="password" name="password" required>

        <!-- <input type="submit" value="Login"> -->
         <button type="submit">Login</button>
    </form>
</div>

</body>
</html>


login.php
<?php
session_start();
include "database.php";
$database = databaseConnection();

if(isset($_POST) AND $database){
    $username = $_REQUEST['username'];
    $password = $_REQUEST['password'];

    $query = "select * from users where username='$username' and password='$password'";
    $result = mysqli_query($database,$query);
    if($row = mysqli_fetch_assoc($result)){
        $_SESSION['isAdmin'] = boolval($row['isAdmin']);
        $_SESSION['username'] = $row['username'];
        $_SESSION['userid'] = $row['id'];
        header("Location:  welcome.php");
        echo "It worked";
}else{
    echo "Error occurred : ".mysqli_error($database);
}
}else{      
    echo $database ? "connection build" : "failed";
}
?>

logout.php
<?php
session_start();
/* `session_destroy();` is a PHP function that is used to destroy all data registered to a session. In
this context, it is being used to end the current session and remove all session data, effectively
logging the user out. */
session_destroy();
header("Location: login.html");
?>

mail.php
<?php
$to = "nahakdaktar084@gmail.com";
$subject = "Test Email";
$message = "Hello! This is a test email sent from PHP.";
$headers = "From: Suraj Prasad <surajprasad311004@gmail.com>\r\n";  // Sender's name
$headers .= "Reply-To: surajprasad311004@gmail.com\r\n";  // Reply-to address
$headers .= "Content-Type: text/plain; charset=utf-8\r\n";  // Content type

if (mail($to, $subject, $message, $headers)) {
    echo "Email sent successfully.";
} else {
    echo "Email sending failed.";
}
?>


NotesPhp.md


register.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registration Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .registration-container {
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            margin-bottom: 20px;
        }
        input[type="text"],
        input[type="email"],
        input[type="password"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        input[type="submit"] {
            background-color: #5cb85c;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
        }
        input[type="submit"]:hover {
            background-color: #4cae4c;
        }
    </style>
</head>
<body>

<div class="registration-container">
    <h2>Register</h2>
    <form action="/register.php" method="post">
        <label for="username">Username</label>
        <input type="text" id="username" name="username" required>

        <label for="password">Password</label>
        <input type="password" id="password" name="password" required>

        isAdmin: <input type="checkbox" name="isAdmin" id="isAdmin">
        <input type="submit" value="Register" name="submit">
    </form>
</div>

</body>
</html>


register.php
<?php
include "database.php";
$database = databaseConnection();
if($database){
if(isset($_POST)){
    $username = $_REQUEST['username'];
    $passwords = $_REQUEST['password'];
    $isAdmin = $_REQUEST['isAdmin'];
    if ($isAdmin == "on") {
        $isAdmin = 1;
    } else {
        $isAdmin = 0;
    }

    $sql = "INSERT INTO users(username, password, isAdmin) VALUES ('$username','$passwords', $isAdmin)";
    $result = mysqli_query($database, $sql);
    if($result){
        echo "User created successfully";
        header("Location: login.html");
    }else{
        echo "Invalid Data";
    }
}}
else{
    echo "Database Connection Failed";
}
?>

user.php
<h1> I am user </h1>

<table>
    <thead>
        <tr>
            <th>userid</th>
            <th>doctorid</th>
            <th>doctor name</th>
            <th>dcotor role</th>
        </tr>
    </thead>
    <tbody>
        <?php
        session_start();

        include "database.php";
        $con = databaseConnection();
        $query = "select * from app inner join doctos on app.doc_id = doctos.doc_id where app.userid=".$_SESSION['userid'];

        $result = mysqli_query($con, $query);
        if ($result) {
            while ($row = mysqli_fetch_assoc($result)) {
                echo "<tr>
                            <td>$row[userid]</td>
                            <td>$row[doc_id]</td>
                            <td>$row[doc_name]</td>
                            <td>$row[doc_role]</td>
                            <td><a href='/delete.php?id=$row[userid]'>cancel</a></td>";
                echo "</tr>";
            }
        }

        ?>
    </tbody>
</table>

welcome.php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <?php 
    session_start(); 

    if(!isset($_SESSION)) {
        header("Location: login.php");
    }

     if($_SESSION['isAdmin']) {
         echo "<h1>Welcome".$_SESSION['isAdmin']."</h1>";
         require "admin.php";
         echo "<a href='/logout.php'>logout</a>";
     }
     else{
        include "user.php";
        // header("Location: login.html");
     }
    ?>

    <table>
        <thead>
            <tr>
                <th>doctors name</th>
                <th>doctors role</th>
            </tr>
        </thead>
        <tbody>
            <?php 
                // include "database.php";
                // $con = databaseConnection();
                $query = "select * from doctos";

                $result = mysqli_query($con, $query);
                if ($result) {
                    while ($row = mysqli_fetch_assoc($result)) {
                        echo "<tr>
                            <td>$row[doc_name]</td>
                            <td>$row[doc_role]</td>";
                            if (!$_SESSION['isAdmin']) {
                                echo "<td><a href='book.php?id=$row[doc_id]'>book now</a></td>";
                            }
                        echo "</tr>";
                    }
                }

            ?>
    
          
        </tbody>
    </table>
</body>
</html> 

addProduct.php
<form action="" method="post">
    doctor_name: <input type="text" name="doc_name" id="doc_name">
    doctor_role : <input type="text" name="role" id="role">

    <button type="submit" >submit</button>

</form>

<?php
    include "database.php";
    $con= databaseConnection();
    if(isset($_POST)) {
        $doc_name = $_POST['doc_name'];
        $role = $_POST['role'];
        $query = "insert into doctos(doc_name, doc_role) values('$doc_name', '$role')";
            
        $result = mysqli_query($con, $query);
            
        if ($result) {
            echo "doctor inserted successfully";
        } else {
            echo "doctor cannot be inserted".mysqli_error($con);
        }

    }
?>

admin.php
<h1> I am admin </h1>

<a href="/addProduct.php">add details</a>


book.php
<?php
session_start();
$userid = intval($_SESSION['userid']);
echo $userid;
include "database.php";
$con = databaseConnection();
if (isset($_REQUEST)) {
    $doc_id = intval($_REQUEST['id']);
    $query = "insert into app values($userid, $doc_id)";
    $result = mysqli_query($con, $query);
    if ($result) {
        echo "Document added to your application";
        header("Location: welcome.php");
    } else {
        echo "Error adding document to your application";
    }
}


createCode.sh
for file in *; do
    if [ -f $file ]; then
        echo $file >> ./trash/NotesPhp.md
        cat $file >> ./trash/NotesPhp.md
        echo "
" >> ./trash/NotesPhp.md
    fi
done


database.php
<?php
function databaseConnection(){
$servername="testhodb2.nj";
$username="trainee";
$password="tky4U63#MZjVqu";
$database="test_doom";
$con = mysqli_connect($servername,$username,$password,$database);
if(!$con){
   return false;
}else{
    return $con;
}
}

// databaseConnection();
?>

delete.php
<?php
    if($_REQUEST) {
        $userid = $_REQUEST['id'];
        include "database.php";
        $con = databaseConnection();
        $result = mysqli_query($con, "delete from app where userid=$userid");
        if ($result) {
            echo "deleted";
            header("Location: welcome.php");
        } else {
            echo "not deleted";
        }
    }




login.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .login-container {
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            margin-bottom: 20px;
        }
        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        input[type="submit"] {
            background-color: #5cb85c;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
        }
        input[type="submit"]:hover {
            background-color: #4cae4c;
        }
    </style>
</head>
<body>

<div class="login-container">
    <h2>Login</h2>
    <form action="/login.php" method="post">
        <label for="username">Username</label>
        <input type="text" id="username" name="username" required>

        <label for="password">Password</label>
        <input type="password" id="password" name="password" required>

        <!-- <input type="submit" value="Login"> -->
         <button type="submit">Login</button>
    </form>
</div>

</body>
</html>


login.php
<?php
session_start();
include "database.php";
$database = databaseConnection();

if(isset($_POST) AND $database){
    $username = $_REQUEST['username'];
    $password = $_REQUEST['password'];

    $query = "select * from users where username='$username' and password='$password'";
    $result = mysqli_query($database,$query);
    if($row = mysqli_fetch_assoc($result)){
        $_SESSION['isAdmin'] = boolval($row['isAdmin']);
        $_SESSION['username'] = $row['username'];
        $_SESSION['userid'] = $row['id'];
        header("Location:  welcome.php");
        echo "It worked";
}else{
    echo "Error occurred : ".mysqli_error($database);
}
}else{      
    echo $database ? "connection build" : "failed";
}
?>

logout.php
<?php
session_start();
/* `session_destroy();` is a PHP function that is used to destroy all data registered to a session. In
this context, it is being used to end the current session and remove all session data, effectively
logging the user out. */
session_destroy();
header("Location: login.html");
?>

mail.php
<?php
$to = "nahakdaktar084@gmail.com";
$subject = "Test Email";
$message = "Hello! This is a test email sent from PHP.";
$headers = "From: Suraj Prasad <surajprasad311004@gmail.com>\r\n";  // Sender's name
$headers .= "Reply-To: surajprasad311004@gmail.com\r\n";  // Reply-to address
$headers .= "Content-Type: text/plain; charset=utf-8\r\n";  // Content type

if (mail($to, $subject, $message, $headers)) {
    echo "Email sent successfully.";
} else {
    echo "Email sending failed.";
}
?>


register.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registration Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .registration-container {
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            margin-bottom: 20px;
        }
        input[type="text"],
        input[type="email"],
        input[type="password"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        input[type="submit"] {
            background-color: #5cb85c;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
        }
        input[type="submit"]:hover {
            background-color: #4cae4c;
        }
    </style>
</head>
<body>

<div class="registration-container">
    <h2>Register</h2>
    <form action="/register.php" method="post">
        <label for="username">Username</label>
        <input type="text" id="username" name="username" required>

        <label for="password">Password</label>
        <input type="password" id="password" name="password" required>

        isAdmin: <input type="checkbox" name="isAdmin" id="isAdmin">
        <input type="submit" value="Register" name="submit">
    </form>
</div>

</body>
</html>


register.php
<?php
include "database.php";
$database = databaseConnection();
if($database){
if(isset($_POST)){
    $username = $_REQUEST['username'];
    $passwords = $_REQUEST['password'];
    $isAdmin = $_REQUEST['isAdmin'];
    if ($isAdmin == "on") {
        $isAdmin = 1;
    } else {
        $isAdmin = 0;
    }

    $sql = "INSERT INTO users(username, password, isAdmin) VALUES ('$username','$passwords', $isAdmin)";
    $result = mysqli_query($database, $sql);
    if($result){
        echo "User created successfully";
        header("Location: login.html");
    }else{
        echo "Invalid Data";
    }
}}
else{
    echo "Database Connection Failed";
}
?>

user.php
<h1> I am user </h1>

<table>
    <thead>
        <tr>
            <th>userid</th>
            <th>doctorid</th>
            <th>doctor name</th>
            <th>dcotor role</th>
        </tr>
    </thead>
    <tbody>
        <?php
        session_start();

        include "database.php";
        $con = databaseConnection();
        $query = "select * from app inner join doctos on app.doc_id = doctos.doc_id where app.userid=".$_SESSION['userid'];

        $result = mysqli_query($con, $query);
        if ($result) {
            while ($row = mysqli_fetch_assoc($result)) {
                echo "<tr>
                            <td>$row[userid]</td>
                            <td>$row[doc_id]</td>
                            <td>$row[doc_name]</td>
                            <td>$row[doc_role]</td>
                            <td><a href='/delete.php?id=$row[userid]'>cancel</a></td>";
                echo "</tr>";
            }
        }

        ?>
    </tbody>
</table>

welcome.php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <?php 
    session_start(); 

    if(!isset($_SESSION)) {
        header("Location: login.php");
    }

     if($_SESSION['isAdmin']) {
         echo "<h1>Welcome".$_SESSION['isAdmin']."</h1>";
         require "admin.php";
         echo "<a href='/logout.php'>logout</a>";
     }
     else{
        include "user.php";
        // header("Location: login.html");
     }
    ?>

    <table>
        <thead>
            <tr>
                <th>doctors name</th>
                <th>doctors role</th>
            </tr>
        </thead>
        <tbody>
            <?php 
                // include "database.php";
                // $con = databaseConnection();
                $query = "select * from doctos";

                $result = mysqli_query($con, $query);
                if ($result) {
                    while ($row = mysqli_fetch_assoc($result)) {
                        echo "<tr>
                            <td>$row[doc_name]</td>
                            <td>$row[doc_role]</td>";
                            if (!$_SESSION['isAdmin']) {
                                echo "<td><a href='book.php?id=$row[doc_id]'>book now</a></td>";
                            }
                        echo "</tr>";
                    }
                }

            ?>
    
          
        </tbody>
    </table>
</body>
</html> 

