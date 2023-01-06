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
  
## kakao map 컴포넌트 생성
```javaScript
  /*global kakao */
  import React, { useEffect } from "react";

  const KakaoMap = () => {
    const { kakao } = window;

    useEffect(() => {
      const container = document.getElementById("map"); //지도를 담을 영역의 DOM 레퍼런스
      const options = {
        //지도를 생성할 때 필요한 기본 옵션
        center: new kakao.maps.LatLng(33.450701, 126.570667), //지도의 중심좌표.
        level: 3, //지도의 레벨(확대, 축소 정도)
      };
      const map = new kakao.maps.Map(container, options); //지도 생성 및 객체 리턴
    }, []);

    return <div id="map" style={{ width: "300px", height: "300px" }}></div>;
  };

  export default KakaoMap;
```
## kakao map 컴포넌트 생성 (패키지 사용)
- kakao maps api를 리액트에 맞게 활용할 수 있는 패키지를 설치하면 코드가 절반으로 줄어든다. 
- ```yarn add react-kakao-maps-sdk```
  
```javaScript
  import React from "react";
  import { Map } from "react-kakao-maps-sdk";

  const KakaoMap = () => {
    return (
      <Map
        center={{ lat: 33.450701, lng: 126.570667 }}
        style={{ width: "375px", height: "812px" }}
        level={3}
      />
    );
  };

  export default KakaoMap;
```
  
## 사용할 페이지에 import 해주기!!
