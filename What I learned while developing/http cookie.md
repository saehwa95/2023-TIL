# http cookie
- 서버에서 클라이언트 브라우저로 쿠키를 넣어줄 수 있다. => 이 방법을 "http cookie"라고 한다. 
- HTTP 쿠키는 서버가 사용자의 웹 브라우저에 전송하는 작은 데이터 조각이다. 
- 브라우저는 그 데이터 조각들을 저장해 놓았다가, 동일한 서버에 재 요청 시 저장된 데이터를 함께 전송한다. 
- 쿠키는 두 요청이 동일한 브라우저에서 들어왔는지 아닌지 판단할 때 주로 사용한다. 
- 이를 이용하면 사용자의 로그인 상태를 유지할 수 있다. 
- 모든 요청마다 쿠키가 함께 전송되기 때문에 성능이 떨어지는 원인이 될 수 있다. 


## 쿠키 설정
- Cookie는 ```Set-Cookie``` HTTP 헤더를 사용하여 설정되며 이는 웹 서버의 HTTP 응답을 통해 송신된다. 
- 이 헤더는 웹 브라우저가 쿠키를 저장하고 이를 차기 서버 요청 시 송신할지 지시한다. 
- 서버는 요청된 페이지를 송신함으로써 응답하며 여기에는 새 쿠키 추가, 기존 쿠키 수정, 쿠키 삭제를 위해 응답에 더 많은 ```Set-Cookie``` 헤더를 포함할 수 있다. 
- 쿠키 값은 페이지 요청에 응답하여 ```Set-Cookie``` 헤더를 포함시킴으로써 서버에 의해 수정이 가능하다. 

## Cross-site, Same-site
- http cookie는 서버와 클라이언트의 도메인이 동일해야한다. 
- 도메인이 동일한지 확인하는 방법
  - 네트워크 탭 : fetch-site를 확인해본다. 
    - cross-site : 도메인 동일하지 않음 
    - same-site : 도메인 동일함
- ```cross-site```라면 도메인이 다르기 때문에 애플리케이션탭에 토큰이 보이지 않는게 정상이다. 
- 개발 환경이라서 도메인이 다를 경우 proxy 설정을 우선 적용하여 same-site로 인식할 수 있게 처리할 수 있다. 

```javaScript
    const ENV = process.env.NODE_ENV === "development";
    //얘 죽이지 말고 나중에 배포한담에 콘솔 확인해보자. 보면 product로 나올거임 (∵분기처리해서)
    console.log(process.env.NODE_ENV);

    export const instance = axios.create({
      baseURL: process.env.REACT_APP_SERVER,
      baseURL: ENV ? "/" : process.env.REACT_APP_SERVER,
      withCredentials: true,
    });
```
