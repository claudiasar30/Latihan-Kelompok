Latihan Pengjarkom Lanjut
<h2>Nama = 	1. Claudia Sartika Alison (22101152630276)
	2. Lara Dilla Wahyuni (22101152630288)
 	3. Najwa Salsabilla Rahayu (22101152630297)</h2>
  <form id="form1" name="form1" method="post" action="" enctype="multipart/form-data">
    <table width="100%" border="2">
	  <td>Foto</td>
        <td><input name="foto" type="file" id="foto" /></td>
      </tr>
      <tr>
        <td>&nbsp;</td>
        <td><input name="simpan" type="submit" id="simpan" value="Simpan Data User" /></td>
      </tr>
    </table>
  </form>
  <?php
if($_POST["simpan"]){
	include "koneksi.php";
	$nmfoto  = $_FILES["foto"]["name"];
	$lokfoto = $_FILES["foto"]["tmp_name"];
	if(!empty($lokfoto)){
		move_uploaded_file($lokfoto, "foto/$nmfoto");
	}
 $sqlm = mysqli_query($kon, "insert into user (iduser, username, password, email, nama, tmplahir, tgllahir, jk, foto, tgldaftar) values ('$_POST[iduser]', '$_POST[username]', '$_POST[password]', '$_POST[email]', '$_POST[nama]', '$_POST[tmplahir]', '$_POST[tgllahir]', '$_POST[jk]', '$nmfoto', NOW())");
	
	if($sqlm){
		echo "Data User berhasil disimpan";
	}else{
		echo "Gagal menyimpan";
	}
	echo "<META HTTP-EQUIV='Refresh' Content='2; URL=?p=user'>";
}
?>
