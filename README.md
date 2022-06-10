# virtualbox
b1042026 b1042092 b1042093
### 更新
```
sudo apt update
sudo apt upgrade
```
### 安裝apache2
```
sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql
```

### 確認ip位置
```
sudo apt install net-tools
ifconfig
```
或
```
hostname -I
```
皆可查看自己點腦的ip位置

![專題1](https://user-images.githubusercontent.com/106758228/173145464-8cb1162d-bb15-404c-a630-a0d710eef5c5.png)


建立一個檔案
```
cd /var/www/html
ls
```
```
sudo apt install vim
```
```
sudo vim info.php
```
```
<?php 
      phpinfo();  
?>

:wq!(強制存檔離開
```
![專題2](https://user-images.githubusercontent.com/106758228/173145625-1e55da61-ba70-46ae-bbff-e49a6d13a084.png)

### 安裝phpmyadmin
```
sudo apt install phpmyadmin
```
![專題3](https://user-images.githubusercontent.com/106758228/173145934-a34b1aa9-4613-4a3a-80a2-c82035c30642.png)

![專題4](https://user-images.githubusercontent.com/106758228/173146037-d365842d-7772-4a0b-8a19-61ee3b367a2c.png)

建立帳號
```
sudo mysql -u root mysql
```
![專題5](https://user-images.githubusercontent.com/106758228/173146445-42e06141-86dd-48f1-9195-0e38105ac38f.png)

```
UPDATE user SET plugin='mysql_native_password' WHERE User='root';
```
```
FLUSH PRIVILEGES;
```
```
exit
```
![專題6](https://user-images.githubusercontent.com/106758228/173147123-12207724-7fc4-40c5-afb8-6bd0956b7580.jpg)

```
sudo mysql_secure_installation
```
![專題7](https://user-images.githubusercontent.com/106758228/173147309-3ff0fa6f-395b-41f2-a4c2-7dffbf324ffe.png)

依序輸入
```
y 
2
y
y
y
```
![專題8](https://user-images.githubusercontent.com/106758228/173147807-9831c412-2c5e-476b-aff5-202bb7cd207b.png)
![專題9](https://user-images.githubusercontent.com/106758228/173148171-7ff93fec-0afe-4606-bdee-4d62471ce63c.png)
![專題10](https://user-images.githubusercontent.com/106758228/173148371-7492448d-2597-4680-8d89-6c3d15706ea9.png)

設定完成後到瀏覽器網址的地方輸入以下
```
自己的ip位置/phpmyadmin
```
![專題11](https://user-images.githubusercontent.com/106758228/173148925-b35bafda-de4d-415c-abf6-7e43f9f2cf8e.png)

如果有順利連接會顯示這個畫面然後登入帳密
![專題12](https://user-images.githubusercontent.com/106758228/173149099-d51a90c4-a00a-4f1b-914e-97531ef894ed.png)

預設帳號:root，密碼是在ubuntu設定的密碼

### 如果登入phpmyadmin失敗

![專題13](https://user-images.githubusercontent.com/106758228/173149198-2cadcd7a-ab86-4b72-81b6-12af6a1b48b2.png)

```
sudo mysql -p -u root
CREATE USER '自己想要的帳號'@'%' IDENTIFIED BY '密碼';
GRANT ALL PRIVILEGES ON *.* TO '帳號'@'%';
exit
```
### 建立完資料庫之後回去終端機的指令
```
sudo vim 資料庫名稱.php
```
```
<?php
          $host ='localhost';
          $dbuser ='(主機的帳號)';
          $dbpw ='(自己的密碼)';
          $dbname =$_GET['a'];
          $link = mysqli_connect($host,$dbuser,$dbpw,$dbname);
          if(empty($link)){
             print mysqli_error($link);
             die("資料庫連接失敗");
             exit;  }
          if(!mysqli_select_db($link,$dbname)){
              die("資料選取失敗");  }
          else {
               echo "連接".$dbname."資料庫成功<br>";  }
          mysqli_query($link,"SET NAMES'UFT-8'");
           $sql  ="SELECT* FROM (下一層資料庫名稱)";
           $result = mysqli_query($link,$sql);
           if($result) {
              $num =mysqli_num_rows($result);
              echo $_GET['a'];
              echo "資料表有".$num."筆資料<br>";  }
           $result =mysqli_query($link,$sql);
           while($row =mysqli_fetch_array($result,MYSQLI_ASSOC)) {
                printf("第%s筆資料: %s<br>, %s<br>, %s<br>",$row["number"],$row["id"],$row["name"],$row["gender"]);
}
?>
```
### 建立新增要輸入資料庫的資料
```
sudo vim sounyu.php
```
```
<?php
          $host ='localhost';
          $dbuser ='主機的帳號';
          $dbpw ='自己的密碼';
          $dbname ='資料庫名稱';
          $link = mysqli_connect($host,$dbuser,$dbpw,$dbname);
          if($link){
             mysqli_query($link, 'SET NAMES uff8');
             echo("正確連接資料庫");
          }
          else{
             echo "不正確連接資料庫</br>" . mysqli_connect_error();
          }
          
          //sql語法存在變數中
          $sql ="INSERT INTO '資料庫名稱' ('number','id','name','gender') VALUE ('1' ,'b1042001','姓名','男')";
          
          //用mysqli_query方法執行(sql語法)將變數存在變數中
          $result =mysqli_query($link,$sql);
          
          //如果有異動到資料庫數量(更新資料庫)
          if(mysqli_affected_rows($link)>0){
          //如果有一筆以上代表有更新
          //mysqli_insert_id可以抓到第一筆的id
          $new_id =mysqli_insert_id($link);
            echo "新增後的id為{$new_id}";
          }
          elseif(mysqli_affected_rows($link)==0){
            echo"無資料新增";
          }
          else{
            echo "{$sql}語法執行失敗，錯誤訊息:" . mysqli_error($link);
          }
          mysqli_close($link);
?>
```

### 如果出現sql語法錯誤畫面
將sounyu.php中的$sql ="INSERT INTO '資料庫名稱' ('number','id','name','gender') VALUE ('1' ,'b1042001','姓名','男')";改成
```
$sql ="INSERT INTO 資料庫名稱(number,id,name,gender) VALUES ('1' ,'b1042001','姓名','男')";
```

### 建立網頁輸入要搜尋的資料庫
```
sudo vim action.php
```
```
<html>
<head><title>php連接資料庫MysQl</title></head>
<body>
輸入要搜尋的資料庫
<form action='(資料庫名稱).php'>
<input type='text' name='a' />
<button type='submit'>送出</button>
</form>
</body>
</html>
```
