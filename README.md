# week03

## My 3th week works.

* ## 0318_JoinPage.html

 다음의 우편번호 서비스와 부트스트랩을 이용해 간단한 회원가입 창을 만들었다.

 form tag의 submit 기능 및 여러가지 정보의 정규표현식을 학습했다.
 정리한 정규표현식의 종류는 아래와 같다.

 - 2~4글자 한글 이름 정규식

    `var regex = /^[가-힣]{2,4}$/;`


 - 숫자와 문자 포함 형태의 6~12자리 이내의 비밀번호 정규식

    `var regex = /^[A-Za-z0-9]{6,12}$/;`


 - 특수문자 / 문자 / 숫자 포함 형태의 8~15자리 이내의 비밀번호 정규식

    `var regex = /^.*(?=^.{8,15}$)(?=.*\d)(?=.*[a-zA-Z])(?=.*[!@#$%^&+=]).*$/;`

 - email 정규식

    `var regex = /^[0-9a-zA-Z]([-_.]?[0-9a-zA-Z])*@[0-9a-zA-Z]([-_.]?[0-9a-zA-Z])*.[a-zA-Z]{2,3}$/i;`

 - 5글자 우편번호 정규식

    `var regex = /^\d{5}/;`

* ## 0319_To_do_list.html

 이전에 만들었던 To do List에 localStorage를 이용하여 추가, 수정, 삭제한 page의 status를 저장/로드했다.

 <li> tag 안의 속성들을 하나하나 가져오기가 번거로워 특정 <ul> tag의 html값을 저장하고 불러와 페이지를 세팅했다.

 ```
 function saveTodo(){
    var todos = {};
    todos['todo'] = $('#todo').html();
    todos['ing'] = $('#ing').html();
    todos['completed'] = $('#completed').html();

    var todos_string = JSON.stringify(todos);
    localStorage.setItem(storage_key, todos_string);
}

function loadTodo(){
    var todos_string = localStorage.getItem(storage_key);
    if(todos_string != null){
        var todos = JSON.parse(todos_string);
        for(var key in todos){
            $('#'+key).html(todos[key]);
        }
    }
}
 ```
 
 
 * ## 0319_Signup.html & 0319_Signup_ok.html

 위의 JoinPage.html을 조금 수정하여 Signup.html에서 form submit시 Signup_ok.html로 넘어가도록 했다.
 
 Signup_ok.html에서는 넘어온 query문을 다시 decoding 하고 localStorage에 저장해, 페이지가 새로고침되거나 브라우저를 껐다 켜더라도 회원정보가 유지되도록 했다.
 
 또한 id의 중복 검사 기능을 추가했다.

