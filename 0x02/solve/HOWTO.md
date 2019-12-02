Bài 2:  http://ksnctf.sweetduet.info/problem/32
  Đọc code thì thấy có thể khai thác được đoạn code "if (strcasecmp($_POST['password'], $password) == 0)", hàm strcasecmp luôn trả về 0 khi truyền vào mảng, dùng postman với cặp giá trị {key,value} ={ password[],123} thì thấy flag = "FLAG_VQcTWEK7zZYzvLhX"
 Bài 4: http://ksnctf.sweetduet.info/problem/35
  Đọc source thì thấy bài này có file database.db, sau khi lấy file database.db về thì ta thấy trong file có một table users gồm 2 trường id,password với trong table có một {id,password}={root,flag}

