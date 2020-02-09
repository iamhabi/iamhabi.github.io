---
layout: post
title: "현재의 프로그래밍은 20년 전과 어떻게 다른가요?"
date: 2020-02-09
category: translate
---

얼마 전 Quora에서 이런 질문을 봤고, 이에 대한 답변을 쓰기 시작했습니다. 그러나 답변이 너무 길어져서 여기에 포스트로 쓰기로 했습니다.

> 질문 - <https://www.quora.com/How-is-the-notion-of-computer-programming-different-today-than-it-was-20-years-ago>

> 번역 - <https://medium.com/swlh/how-is-computer-programming-different-today-than-20-years-ago-9d0154d1b6ce>

이 목록에는 제가 지난 20년 동안 느낀 변화들을 적었습니다.

-	20년 전에는 대부분 이론이었던 불변성, 꼬리 재귀, lazily evaluated collections, 느긋한 계산법(Lazily evaluated collections), 패턴 매칭, 일급 함수(First Class Functions) 그리고 그것들을 사용하지 않는 사람을 얕보는 것과 같은 몇몇 프로그래밍 개념들은 현재 주류가 되었습니다.

-	데스크탑 소프트웨어는 이제 브라우저를 포함한 웹 페이지를 의미합니다.

-	OOP는 여전히 가장 유명한 프로그래밍 모델일지라도 많은 신뢰를 잃었습니다. Go, Rust 그리고 Swift와 같이 새로운 trait-based 프로그래밍 모델은 더 널리 알려져 있습니다. 상속보다는 합성이 선호됩니다.

-	2천 달러짜리 회의에 참석하고 그곳에서 찍은 셀카를 공유할 때까지 더 이상 공식적으로 프로그래머로 간주되지 않습니다.

-	멀티 프로세서 CPU의 빠른 확산 덕분에 병렬 프로그래밍은 20년 전의 OS 호출이 아닌 프로그래밍 언어 수준에서 지원됩니다. 

-	픽셀은 더 이상 적절한 측정 단위가 아닙니다.

-	쓰레기 수집은 안전한 프로그래밍의 일반적인 방법이 되었지만 코드 리뷰에서 거친 농담이나 Rust의 lifetime과 같은 최신 안전 모델도 등장하고 있습니다.

-	30억 개의 장치가 Java를 실행합니다. 이 숫자는 지난 10년간 변하지 않았습니다.

-	패키지 관리 ecosystem은 지금의 프로그래밍 언어에 필수적입니다. 사람들은 더 이상 단순히 라이브러리를 찾고, 다운로드해서 설치하는 번거로움을 원하지 않습니다. 20년 전 우리는 웹 사이트를 방문해서, zip 파일을 다운로드하고, 파일을 올바른 위치에 복사하고, 빌드 구성에서 path를 추가한 후 그것들이 제대로 작동하길 빌어야 했습니다.

-	소프트웨어 개발 팀이 되는 것은 모든 팀원들이 아침에 15분 동안 함께 서서 포스트잇으로 신비한 상징을 그리는 신비로운 의식을 해야 합니다.

-	오늘날 언어 도구는 더 풍부해졌습니다. 프로그래밍 언어는 보통 컴파일러와 아마도 디버거였습니다. 오늘날 언어는 보통 linter, Code Formatter, 템플릿 생성기, 자동 업데이트 기능 및 다른 언어와의 토론에 사용할 수 있는 인수 목록이 제공됩니다.

-	여전히 탭이냐, 스페이스바 4번이냐를 두고 토론을 합니다.

-	고맙게도 웹상에서 원활한 상호작용을 제공하기 위한 유일한 방법이었던 Adobe Flash는 더 이상 존재하지 않습니다. Now 똑같은 수준의 상호작용을 제공하기 위해 완전히 다른 프로그래밍 모델들을 사용해서 3가지의 다른 플랫폼에서 개발해야 합니다.

-	IDE와 프로그래밍 언어들은 점점 더 멀어지고 있습니다 each other. 20년 전 IDE는 한 가지 언어를 위해 개발됐습니다 (Java를 위한 Eclipse, visual basic, Pascal을 위한 Delphi 등등). 오늘날 IDE와 같은 기능을 제공하면서 여러 언어들과 호환되는 VS code 같은 에디터가 있습니다.

-	코드는 이제 최소한 3가지의 수준의 가상화를 실행해야 합니다. Bare Metal 서버에서 실행되는 코드는 불필요하게 성능이 우수합니다.

-	모바일 장치, 클라우드 서버, 임베디드 IoT 시스템과 같이 다양한 아키텍처로 인해 Cross-platform 개발은 표준이 됐습니다. 20년 전 이것들은 아무나 이용할 수 없는 고가의 기기들이었습니다.

-	여러분의 코드를 로컬에서 실행하는 것은 거의 하지 않는 짓입니다.

-	문서는 항상 온라인이고 Google이라고 불립니다. 더 이상 오프라인 문서는 없습니다. 있다고 하더라도 아무도 그 존재를 모를 겁니다.

-	튜토리얼은 텍스트보다 이해하는데 시간이 오래 걸리는 비디오 형식이 아니라면 도움이 되지 않습니다.

-	그 당시에는 존재하지 않았던 StackOverflow가 있습니다. 프로그래밍에 관한 질문을 하는 것은 동료들과 대화를 하는 것과 관련이 있습니다.

-	사람들이 Mac에서 개발을 합니다.

-	당시와는 반대로 인터넷 연결은 일반적인 것이고 오프라인 상태가 되는 것은 예외적인 것입니다.

-	보안은 우리가 신경 써야 되는 것입니다.

-	지금의 모바일 장치는 평범한 웹 페이지를 보여줄 수 있습니다. 그래서 더 이상 별도의 하위 도메인에서 별도의 WAP 페이지를 만들 필요가 없습니다. 대신에 우리는 별도의 서브 도메인에서 모바일 페이지를 만듭니다.

-	우리는 우리를 당황하게 하는 코드를 제외하곤 기본적으로 모든 코드를 공개합니다.

-	차별에 맞서 싸운 모두들 덕분에, 현장에는 재능이 있는 여성, 여러 인종들(people of colors), LGBT가 있습니다. 저는 여전히 우리가 평등의 측면에 있다고는 말할 수 없지만 이전보다는 훨씬 낫습니다.

-	해킹을 당하는 것은 흔한 일입니다. 모든 사용자 데이터를 잃는 것은 보통 블로그에 비밀번호를 변경하라고 권장하는 글을 쓰는 것으로 피할 수 있습니다. 사과는 필요 없습니다.

-	원격으로 프로그래머로서 일하는 것은 화상 회의, 유비쿼터스 인터넷 접속과 Keurigs 덕분에 그 어느 때보다 쉽습니다.

-	더 이상 소통을 위해 IRC를 사용하지 않습니다. 우리는 서버 주소를 입력하기 싫어서 Slack이라고 불리는 부풀린(bloated) 버전을 선호합니다.

-	우리는 그래픽 카드에서 프로그램을 실행합니다.

-	중앙 집권 및 규칙 기반인 버전이 훨씬 빠르고 효율적이기는 하지만 블록체인과 AI를 포함하지 않는 한 여러분의 프로젝트는 비즈니스 가치가 없습니다.

-	어떤 이유로, 1 기가바이트는 저장 공간으로써 불충분합니다.

-	부채널 공격(side-channel attacks) 때문에 우리는 더 이상 물리적인 프로세서조차 믿지 못합니다.

-	프로그래밍의 상당 부분은 이제 foosball 테이블에서 이루어집니다.

-	이전보다 훨씬 빠른 CPU를 가지게 된 이후로, 계산을 Fortran보다 훨씬 느린 Python으로 합니다. 그래서 계산은 기본적으로 20년 전과 동일한 시간이 걸립니다.

-	새로운 프로그래밍 언어를 만든 것이나 새로운 하드웨어를 만드는 것조차 흔한 취미입니다.

-	유닛 테스트는 과대광고로 등장했고 모든 유용한 것들과 마찬가지로 그 이점이 과대평가되었으며 그것은 필연적으로 종교로 변했습니다.

-	비밀번호를 일반 텍스트로 저장하는 것은 어리석은 짓이지만, 우리는 그 짓을 어쨌든 합니다.

아직 번역이 부족한 부분이 많다. 모르는 단어도 많아서 사전을 자주 찾아 봤고 모르는 용어도 많아서 구글링도 많이 했다. 오역도 많을 거고 계속 번역 연습을 하면서 틀린 부분이 있으면 바로바로 고치자고 생각하고 있다.