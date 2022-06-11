# VirtualBox
b1042026 羅翊宸

b1042092 李心喬

b1042093 藍宇晨


* [在VirtualBox使用MySQL建立資料庫](#在virtualbox使用mysql建立資料庫)
  - [更新](#更新)
  - [安裝apache2](#安裝apache2)
  - [確認ip位置](#確認ip位置)
  - [建檔+寫入php格式](#建檔寫入php格式)
  - [安裝phpmyadmin+建立帳號](#安裝phpmyadmin建立帳號)
    - [如果登入phpmyadmin失敗](#如果登入phpmyadmin失敗) 
     
  - [建立資料庫](#建立資料庫)
  - [建立完資料庫之後回去終端機的指令](#建立完資料庫之後回去終端機的指令)
  - [建立新增要輸入資料庫的資料](#建立新增要輸入資料庫的資料)
    - [如果出現sql語法錯誤畫面](#如果出現sql語法錯誤畫面)
* [建立網頁輸入要搜尋的資料庫](#建立網頁輸入要搜尋的資料庫)
  - [瀏覽器檢視是否有成功](#瀏覽器檢視是否有成功)
    - [新增資料至資料庫](#新增資料至資料庫)
    - [搜尋資料庫](#搜尋資料庫)
* [參考資料](#參考資料)

## 在VirtualBox使用MySQL建立資料庫

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
皆可查看自己電腦的ip位置

![專題1](https://user-images.githubusercontent.com/106758228/173145464-8cb1162d-bb15-404c-a630-a0d710eef5c5.png)

### 建檔+寫入php格式
建立一個檔案
```
cd /var/www/html
ls
```
安裝vim
```
sudo apt install vim
```
將php格式寫入
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

### 安裝phpmyadmin+建立帳號
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

#### 如果登入phpmyadmin失敗

![專題13](https://user-images.githubusercontent.com/106758228/173149198-2cadcd7a-ab86-4b72-81b6-12af6a1b48b2.png)

```
sudo mysql -p -u root
```
```
CREATE USER '自己想要的帳號'@'%' IDENTIFIED BY '密碼';

GRANT ALL PRIVILEGES ON *.* TO '帳號'@'%';

exit
```
![專題14](https://user-images.githubusercontent.com/106758228/173151771-f18d307e-4091-4e8a-b282-2b79e126ad4a.png)
![專題15](https://user-images.githubusercontent.com/106758228/173152273-d4ee01ea-6c68-4825-a66e-e665e78614ac.png)

### 建立資料庫
登入後出現以下畫面

![專題16](https://user-images.githubusercontent.com/106761671/173173496-e6fb013d-e615-4e17-bb45-18e381796ded.png)

建立一個新的資料夾層

![專題17](https://user-images.githubusercontent.com/106761671/173173737-57f16250-6c99-4c0b-8de3-5bcd25a8e112.png)


建立資料表

![專題18](https://user-images.githubusercontent.com/106761671/173173755-2f50fb39-9a4b-4113-ae41-f659b2160098.png)


建立資料表裡面的內容

![專題19](https://user-images.githubusercontent.com/106761671/173173771-43cb5bbe-de2f-4fc8-accf-2b4048556ef5.png)


瀏覽後要有剛剛輸入的欄位

![專題20](https://user-images.githubusercontent.com/106761671/173173797-c25b179f-6ce6-4a2f-bcba-6c5a49d1888f.png)


輸入資料表的內容

![專題21](https://user-images.githubusercontent.com/106761671/173173838-9cf49b9e-df50-4972-9d1f-48380a6622f4.png)


按確定執行後會出現

![專題22](https://user-images.githubusercontent.com/106761671/173173903-8c12ca37-02c9-4b17-aab1-8cd4847e6810.jpg)


### 建立完資料庫之後回去終端機的指令
```
sudo vim 資料庫名稱.php
```
```
<?php
          $host ='localhost';
          $dbuser ='主機的帳號';
          $dbpw ='自己的密碼';
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
           $sql  ="SELECT* FROM 資料庫名稱";
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
![專題22](https://user-images.githubusercontent.com/106761671/173174276-50ffce0e-280b-494b-a9d1-04a2bb510c3f.png)

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
          $sql ="INSERT INTO '資料表名稱' ('number','id','name','gender') VALUE ('1' ,'b1042001','姓名','男')";
          
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
![專題error1](https://user-images.githubusercontent.com/106761671/173175820-8782b2aa-79cc-4dfc-bfc3-8e84e421280d.png)

#### 如果出現sql語法錯誤畫面

![專題error2](https://user-images.githubusercontent.com/106761671/173174999-aec03401-a660-49dc-a780-f240eb96d9db.png)

將sounyu.php中的

$sql ="INSERT INTO '資料表名稱' ('number','id','name','gender') VALUE ('1' ,'b1042001','姓名','男')";改成
```
$sql ="INSERT INTO 資料表名稱(number,id,name,gender) VALUES ('1' ,'b1042001','姓名','男')";
```
![專題23](https://user-images.githubusercontent.com/106761671/173175871-cee38f87-83ab-4920-98d1-86e6515248f0.png)

## 建立網頁輸入要搜尋的資料庫
```
sudo vim action.php
```
```
<html>
<head><title>php連接資料庫MysQl</title></head>
<body>
輸入要搜尋的資料庫
<form action='資料庫名稱.php'>
<input type='text' name='a' />
<button type='submit'>送出</button>
</form>
</body>
</html>
```
![專題23-1](https://user-images.githubusercontent.com/106761671/173175937-6a04c560-2999-413c-b966-4b26f12f4e27.png)

### 瀏覽器檢視是否有成功
#### 新增資料至資料庫
到瀏覽器搜尋
```
ip位置/sounyu.php
```
會出現以下畫面為成功

![專題25](https://user-images.githubusercontent.com/106761671/173175026-8e8aa508-a43f-4298-b3e2-a16a0e6c433d.png)


在phpmyadmin資料庫中可看見新增的

![專題28](https://user-images.githubusercontent.com/106761671/173175094-7b348c43-672b-4c17-8332-5a7918ef9f63.png)


#### 搜尋資料庫
到瀏覽器搜尋
```
ip位置/action.php
```
會出現以下畫面

![專題24](https://user-images.githubusercontent.com/106761671/173175178-806062f0-2b91-481a-8d5f-e79d4f635214.png)


在搜尋欄輸入資料庫名稱  送出之後會顯示該資料庫的資料內容

![專題27](https://user-images.githubusercontent.com/106761671/173175244-2f029368-5722-443a-a347-d29cd76d487b.png)

## 參考資料
