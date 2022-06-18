# Git and Github

Git과 Github는 다르다.
Git은 실시간 정보 추적. Github는 저장소이다.

## 1. Git

1.1 Repositories
리포지토리란 저장장치 내의 주요 장소이다. 쉽게, '폴더'라고 생각할 수 있다.

1.2 Commits
자신이 지금까지 작업한 결과물을 업로드 하는 것.

1.3 Areas
총 3개의 area가 있다.
(이후에 복습하여 upload 필요)

1.4 Branches
하나의 root에서 파생된 분기점. 이 분기점에서 각각의 작업을 할 수 있다. 여기서 말하는 '각각'이 바로 branch이다.
branch는 같은 시간에서 서로 다른 결과를 갖고 있다. 일반적으로 안정적인 branch를 root에 합친다. 그런데 문제가 생기는 경우가 있다.
이를 conflict라 한다.
만약 다른 branch에서 같은 부분을 수정했을 경우, merge가 되지 않는다.
문제가 되는 부분을 수정하면 다시 정상적으로 merge할 수 있다.

## 2. Github

2.1 Forking and cloning
Fork란 어떤 repository에 있는 모든것을 복사하는 행위이다.
복사된 데이터는 자신의 repository에서 확인할 수 있다.
Clone이란 Github상에 존재하는 repository를 자신의 컴퓨터에 복제하는 것을 말한다.

2.2 Pull requests
협업시 자신이 작업한 결과물을 다시 원래의 master branch로 합치는것을 pull requset라 한다.

2.3 Origin and upstream
Origin이란 자신이 clone한 master branch를 말한다. 즉, 나의 repository이다.
upstream이란 자신이 clone한 원본. 예를 들어 회사의 repository이다.

2.4 Issues
협업시 bug 등 의사소통이 필요한 부분에 대한 comment. 일반적으로 pulling 할 때 issue에 있는 bug가 해결됐다고 말한다.
