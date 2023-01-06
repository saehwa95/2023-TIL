# 카카오 맵 API 활용하기 

## APP KEY 받기 
- 카카오 개발자 사이트에 접속한 후 내 애플리케이션 페이지에서 애플리케이션을 추가한다. 
- 플랫폼 설정을 WEB으로 등록하고, 이때 도메인 주소를 ```http://localhost:3000/```로 등록했다. 

## APP KEY 적용 
- index.html 파일 <body>태그 최하단에 <script>태그를 작성하여 JavaScript 키를 넣어준다.
- 이때 작성하는 JavaScript 키는 노출하지 않도록 설정이 필요하다. 
- 우선 .env 파일을 생성해 ```REACT_APP_KAKAO_MAP_KEY=[내가 발급 받은 키]```를 적어준다. 
- .gitignore 파일에 .env를 추가한다. 
- index.html 파일에 작성한 ```JavaScript 키```를 ```REACT_APP_KAKAO_MAP_KEY```로 덮어서 작성한다. 
- 설정한 내용을 적용하기 위해 dotenv 패키지를 설치한다. 
- ```(yarn 명령어 : yarn add dotenv)```
  
  
