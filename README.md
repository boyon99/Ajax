# Ajax

정통적으로 XMLHttpRequest() 객체를 생성하여 요청하는 방법이 있지만 문법이 난해하고 가독성도 좋지 않다. 따라서 자바스크립트 AJAX 통신 기술인 fetch() 메서드를 사용하여 실습을 진행해보도록 한다.

- XML Http Request 방식

```js
var httpRequest = new XMLHttpRequest();

httpRequest.onreadystatechange = function () {
  if (
    httpRequest.readyState == XMLHttpRequest.DONE &&
    httpRequest.status == 200
  ) {
    document.getElementById("text").innerHTML = httpRequest.responseText;
  }
};

httpRequest.open("GET", "css", true);
httpRequest.send();
```

- Fetch API 방식

```js
fetch("css").then(function (res) {
  // res에 응답 객체가 저장된다.
  console.log(res);
  if (res.status == "404") {
    alert("not found");
  } else {
    res.text().then(function (text) {
      document.querySelector("article").innerHTML = text;
    });
  }
});
// 비동기방식으로 작동한다.
function logs() {
  console.log("1-response end");
}
console.log("2-after");
// then은 완료 이후 실행되는 함수이다.
fetch("html").then((res) => {
  logs();
});
```
