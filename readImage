<!Doctype html>
<html>
<head>
	<title>Photo Details</title>
	
<style>
table, th, td {
    border: 1px solid black;
}
</style>
	
</head>
<body>

<table>
	<tr>
		<th>Property</td>
		<th>Value</td>
	</tr>

	<?php
	error_reporting(0);
	try
	{
		if ((($_FILES["file"]["type"] == "image/gif")
		|| ($_FILES["file"]["type"] == "image/jpeg")
		|| ($_FILES["file"]["type"] == "image/png")
		|| ($_FILES["file"]["type"] == "image/pjpeg"))
		&& ($_FILES["file"]["size"] < 2000000))
		  {
		  if ($_FILES["file"]["error"] > 0)
			{
			  echo "Return Code: " . $_FILES["file"]["error"] . "<br />";
			}
		  else
			{
			echo "Upload: " . $_FILES["file"]["name"] . "<br />";
			echo "Type: " . $_FILES["file"]["type"] . "<br />";
			echo "Size: " . ($_FILES["file"]["size"] / 1024) . " Kb<br />";
			echo "Temp file: " . $_FILES["file"]["tmp_name"] . "<br />";
			
			//Generate Image name
			$_rand_name=rand(0,1000000000);
			$name=$_FILES["file"]["name"];
			$exploded=explode('.',$name);
			$ext=$exploded[1];
			echo "extension is ".$ext."<br/>".$_rand_name."<br/>";
			$image_name=$_rand_name.".".$ext;
			
			if (file_exists("uploads/" . $_FILES["file"]["name"]))
			  {
			  echo $image_name. " already exists. ";
			  }
			else
			  {
					//Move image to uploads folder
				  move_uploaded_file($_FILES["file"]["tmp_name"],
				  "uploads/".$image_name);
				  echo "Stored in: " . "uploads/" .$image_name;
				  echo "<br />";
				  
				  //Extract Photo image Details using exif
					$image = "uploads/" .$image_name;
					$exif = exif_read_data($image, 0, true);
					foreach ($exif as $key => $section) {
					foreach ($section as $name => $val) {

							if($name != "MakerNote")
							{
							 echo "<tr><td>$name:</td><td> $val</td></tr>"; 
							}
						}
					}
				}
			  }
			}
		  
		else
		  {
			echo "Invalid file";
			header('refresh:2;url=index.php');
		  }
	}
	catch(Exception $e)
	{}
	
	?>
</table>

</body>
</html>
