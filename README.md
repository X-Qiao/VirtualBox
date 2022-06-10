# virtualbox
b1042026 b1042092 b1042093
### 更新
```
sudo apt update
sudo apt upgrade
```
```
sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql
```
```
sudo apt install net-tools
ifconfig
```
```
cd /var/www/html
ls
```
```
sudo apt install vim
sudo vim info.php
```
```
<?php 
      phpinfo();  
?>
:wq!(強制存檔離開
```
```
sudo apt install phpmyadmin
```
```
sudo mysql -u root mysql
```
```
UPDATE user SET plugin='mysql_native_password' WHERE User='root';
```
```
FLUSH PRIVILEGES;
```
```
exit
```
```
sudo mysql_secure_installation
```
```
登入phpmyadmin失敗
sudo mysql -p -u root
CREATE USER '(自己想要的帳號)'@'%' IDENTIFIED BY '(密碼)';
GRANT ALL PRIVILEGES ON *.* TO '(帳號)'@'%';
exit
```
```
建立完資料庫之後回去終端機的指令
sudo nano (資料庫名稱).php
<?php
          $host ='localhost';
          $dbuser ='(主機的帳號)';
          $dbpw ='(自己的密碼)';
          $dbname ='(資料庫名稱)';
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
              echo "(資料庫名稱) 資料表有".$num."筆資料<br>";  }
           $result =mysqli_query($link,$sql);
           while($row =mysqli_fetch_array($result,MYSQLI_ASSOC)) {
                printf("第%s筆資料: %s<br>, %s<br>, %s<br>",$row["number"],$row["id"],$row["name"],$row["gender"]);
}
?>
ctrl+o存檔
ctrl+x退出
```

```
<?php
          $host ='localhost';
          $dbuser ='(主機的帳號)';
          $dbpw ='(自己的密碼)';
          $dbname ='(資料庫名稱)';
          $link = mysqli_connect($host,$dbuser,$dbpw,$dbname);
          if($link){
             mysqli_query($link, 'SET NAMES uff8');
             echo("正確連接資料庫");
          }
          else{
             echo "不正確連接資料庫</br>" . mysqli_connect_error();
          }
          
          //sql語法存在變數中
          $sql ="INSERT INTO '(資料庫名稱)' ('number','id','name','gender') VALUE ('1' ,'b1042001','姓名','男')";
          
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
