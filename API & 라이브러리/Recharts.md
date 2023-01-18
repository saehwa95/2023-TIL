# Recharts 사용하기
- 공식 사이트 : https://recharts.org/en-US
- 설치 : yarn add recharts

## AreaChart 사용법
1. 공식 문서에서 내가 사용할 그래프 디자인 선택
2. 예제 코드 확인
3. 활용 할 데이터 연결해주고 그래프 만들기
4. 각 컴포넌트의 속성인 Cartesian Components를 확인하면 default 속성과 내가 바꿀 수 있는 속성에 대한 내용이 나와있으니 확인

## 내가 작성한 코드
```javascript
  import React from "react";
  import { AreaChart, Area, Tooltip, YAxis } from "recharts";
  import styled from "styled-components";

  const TideGraph = ({ weatherData }) => {
    const tideInfo = weatherData?.tide_info;
    console.log(tideInfo);

    return (
      <ChartWrapper>
        <AreaChart width={1105} height={384} data={tideInfo}>
          <YAxis domain={[0, "dataMax + 700"]} hide="true" />
          <Tooltip />
          <Area
            className="chart"
            type="monotone"
            dataKey="tph_level"
            stroke="#006981"
            fill="#006981"
          />
        </AreaChart>
      </ChartWrapper>
    );
  };

  export default React.memo(TideGraph);
```

## 내가 만든 그래프
![image](https://user-images.githubusercontent.com/100126319/213266077-bc4136d0-dd35-4e14-9851-9e191707ca4c.png)

## 사용 후 느낀 점
간단한 그래프를 만들고 싶다면 추천한다. <br>
나는 처음에 y축을 수정하고 싶어서 구글링만 했는데, 결국 답은 공식문서에 있었다!! <br>
교훈 : 공식문서 먼저 확인하기!!

