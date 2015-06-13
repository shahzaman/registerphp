
  <?PHP
	$con=mysql_connect("localhost","root","");
	if(!$con){
	die('Not connect'.mysql_error());	
	}
	mysql_select_db("trading",$con);

	$company= $_POST['Company'];
	$firstname= $_POST['FirstName'];
	$lastname=$_POST['LastName'];
	$address=$_POST ['Address'];
	$country=$_POST['Country'];
	$city=$_POST['City'];
	$email=$_POST['Email'];
	$mobile=$_POST['Mobile'];
	$username=$_POST['UserName'];
	$password=$_POST ['Pass_word'];
	
 

$query = "SELECT * FROM user WHERE username='$username'";

$result1 = mysql_query($query) or die (mysql_error().$query);    
$count = mysql_num_rows($result1);

if ($count>0) {
echo ("<SCRIPT LANGUAGE='JavaScript'>
        window.alert('username already exist')
        window.location.href='register.html'
        </SCRIPT>");
} else {
	  
	$sql="insert into user(Company,FirstName,LastName,Address,Country,City,Email,Mobile,UserName,Password)values('$company','$firstname','$lastname','$address','$country','$city','$email','$mobile','$username','$password')";
    if(!mysql_query($sql,$con)){
	  die('ERROR'.mysql_error());
	}

	echo("<SCRIPT LANGUAGE='JavaScript'>
        window.alert('Data Succesfully Enter!')
		window.location.href='profile.php';
        </SCRIPT>"); 
}
	
        

 ?>
