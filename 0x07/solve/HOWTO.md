## Bài 1
Nhận thấy flag khi truyền vào bị mã hóa rot13
``` javascript
var flag = document.getElementById("flag").value;
var rotFlag = flag.replace(/[a-zA-Z]/g, function(c) {
  return String.fromCharCode(
    (c <= "Z" ? 90 : 122) >= (c = c.charCodeAt(0) + 13) ? c : c - 26
  );
});
```
sau đó so với chuỗi `PyvragFvqrYbtvafNerRnfl@syner-ba.pbz`
```javascript
if ("PyvragFvqrYbtvafNerRnfl@syner-ba.pbz" == rotFlag) {
  alert("Correct flag!");
} else {
  alert("Incorrect flag, rot again");
}
```
 Vậy ta decode đoạn mã `PyvragFvqrYbtvafNerRnfl@syner-ba.pbz` sẽ được `ClientSideLoginsAreEasy@flare-on.com`
