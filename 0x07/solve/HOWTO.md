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
## Bài 3

Thấy đoạn javascript đọc k hiểu gì, sau một lúc thì sử dụng [tool](http://sanya.sweetduet.info/unyaencode/) để console.log đoạn mã đó ra

Sau khi decode ta thu được đoạn mã

``` javascript
$(function() {
    $("form").submit(function() {
        var t = $('input[type="text"]').val();
        var p = Array(70, 152, 195, 284, 475, 612, 791, 896, 810, 850, 737, 1332, 1469, 1120, 1470, 832, 1785, 2196, 1520, 1480, 1449);
        var f = false;
        if (p.length == t.length) {
            f = true;
            for (var i = 0; i < p.length; i++)
                if (t.charCodeAt(i) * (i + 1) != p[i]) f = false;
            if (f) alert("(」・ω・)」うー!(/・ω・)/にゃー!");
        }
        if (!f) alert("No");
        return false;
    });
});
```

Hàm decode bằng c++

```c++
#include<iostream>

using namespace std;

int main(){
    int arr[]={70, 152, 195, 284, 475, 612, 791, 896, 810, 850, 737, 1332, 1469, 1120, 1470, 832, 1785, 2196, 1520, 1480, 1449};
    for (int i = 0; i < 21; i++){
        cout<< char(arr[i]/(i+1));
    }
    return 0;
}
```
Decode ta được flag như sau:`FLAG_fqpZUCoqPb4izPJE`
