---
layout: post
title: "MaybeBoard"
date: 2020-09-07
category: project
---

개인적으로 DailyBoard나 DashBoard 같은 것이 필요해서 제작했다.  

"MaybeBoard"인 이유는 이것도 '아마' 일종의 DashBoard겠지라고 생각해 MaybeBoard라고 이름을 붙였다.

**<https://github.com/iamhabi/MaybeBoard>**

![](/media/MaybeBoard/MaybeBoard.png)


## Clock

<https://www.w3schools.com/graphics/canvas_clock_start.asp>

w3schoools의 소스를 내 입맛대로 고쳤다.

setInterval() 함수를 사용하면 새로 고침 할 때 시계가 늦게 로딩되어서 requestAnimationFrame() 함수를 사용하였다.

## Weather

<https://openweathermap.org/>  
<https://github.com/CodeExplainedRepo/Weather-App-JavaScript>

날씨 API는 openweathermap이라는 곳을 사용했다.  

날씨 아이콘과 소스는 위에 링크를 걸어둔 github에 있는 것을 사용하였다.  
위 github의 소스를 내 입맛대로 고쳐 사용하였다.

json과 api를 사용하는 것이 처음이라 헤맸는데 위의 github 덕분에 공부가 됐다.

## Calendar

<https://developers.google.com/calendar>

시계와 날씨만 만들고 끝내려 했지만 달력도 만들면 좋을 거 같아서 만들었다.

![](/media/MaybeBoard/calendar.png)

사진에서 볼 수 있듯이 오늘 날짜는 skyblue 색상으로 background를 칠했다.  

이벤트는 길이 별로 색을 다르게 하여 구분하기 쉽게 했다. 사용한 색은 lightpink, greenyellow, lightgreen, lightsteelblue, lightsalmon , paleturquoise이다. 6일이 넘어가는 이벤트는 모두 paleturquoise를 사용한다.  

이벤트 길이가 긴 것이 더 위로 올라가도록 하기 위해 sortEventbyLength()라는 함수를 만들어 버블 정렬을 사용해 내림차순으로 정렬하였다.