Bài 2:  http://ksnctf.sweetduet.info/problem/32
  Đọc code thì thấy có thể khai thác được đoạn code "if (strcasecmp($_POST['password'], $password) == 0)", hàm strcasecmp luôn trả về 0 khi truyền vào mảng, dùng postman với cặp giá trị {key,value} ={ password[],123} thì thấy flag = "FLAG_VQcTWEK7zZYzvLhX"
 
Bài 3: http://ksnctf.sweetduet.info/problem/31
  if (isset($_POST['submit']))
{
    //  Gacha
    if ($_POST['submit'] === 'Gacha')
    {
        //  Yamato is ultra rare
        $ship[] = mt_rand(0, count($shipname)-2);

        $s = implode(',', $ship);
        $sign = hash('sha512', $salt.$s);

        setcookie('ship', $s);
        setcookie('signature', $sign);
    }

    //  Clear
    if ($_POST['submit'] === 'Clear')
    {
        setcookie('ship', '', 0);
        setcookie('signature', '', 0);
    }

    header("Location: {$_SERVER['REQUEST_URI']}");
    exit();
}
Đoạn code trên cho thấy:
- $ship[] được gán 1 giá trị ngẫu nhiên 0-9
- cookie signature = sha512($salt.&s)
- cookie ship = $s
Các khai thác:
- gán cookie ship =10
- cookie signature = sha512(salt+cookieship+cookie)
- sử dụng hashpump -s a7aff87d838a07da5005733c836fdf385509be83c82032c5a8f3962753ebc85ed6cfae2565eb2c98bc6d70648c7e7078a6265cfdbd89341fe05e1305d7840983 -d 0 -k 21 -a ,10
- 9c366c913e32d362a2c3261bc56aaa1741471a37de6a49b4e59946a3396a6d79f261f84f13f935070fec6dd47f2b526ed551bdf9f789b58ffce97ac3bcc24bd1
0\x80\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\xb0,10
- Thay "\x" = "%"
- gán giá trị cookie cho ship và signature reload trang sẽ nhận được flag
- FLAG_uc8qVFa8Sr6DwYVP
Bài 4: http://ksnctf.sweetduet.info/problem/35
  Đọc source thì thấy bài này có file database.db, sau khi lấy file database.db về thì ta thấy trong file có một table users gồm 2 trường id,password với trong table có một {id,password}={root,flag}

