
# Git & Github

참고
- [인프런 git과 github](https://www.inflearn.com/course/git-and-github)의 강사님과 
- [기초 Git 명령어 정리](https://medium.com/@pks2974/%EC%9E%90%EC%A3%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B8%B0%EC%B4%88-git-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC%ED%95%98%EA%B8%B0-533b3689db81)의 작성자님과
- [누구나 쉽게 이해할 수 있는 git 입문](https://backlog.com/git-tutorial/kr/)
의 작성자님께 감사인사 드립니다.
- 그 외의 관련 글을 작성해주시는 분들 모두 감사드립니다.
- 짱 ㅠ

**git 이란?**
- 소스코드를 효과적으로 관리하기 위해 개발된 **분산형 버전 관리 시스템**  즉, 소프트웨어
- 쉽게 말해, 여러명의 개발자가 프로젝트를 협업하여 개발하면서 버전을 관리할 수 있는 시스템
- 최초로 리눅스 토발즈가 리눅스 커널 개발에 이용하려고 개발
- git을 관리하는데 일반적으로 github를 많이 사용
- 소스 코드가 변경된 이력을 쉽게 확인할 수 있고, 특정 시점에 저장된 버전과 비교하거나 특정 시점으로 되돌아갈 수도 있음

**git repository란?**

- 저장소(git repository)란 말그대로 파일이나 폴더를 저장해두는 곳
- 파일이 변경 이력 별로 구분되어 저장
- 비슷한 파일이라도 실제 내용 일부 문구가 서로 다르면 다른 파일로 인식
- 원격 저장소(Remote Repository): 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소
- 로컬 저장소(Local Repository): 내 PC에 파일이 저장되는 개인 저장소

**git branch란?**

- branch란 나뭇가지라는 뜻
- branch를 만든다는 것은 프로젝트를 함에 있어서 독립적인 공간을 새로이 만드는 것
- 기본적으로 있는 branch를 master  브랜치라고 하며 사용자가 여러개의 branch를 만들 수 있음

## Git 설치하기

- 주소
> [https://git-scm.com/downloads](https://git-scm.com/downloads)

- 버전확인
```
> git --version
```

## Git 설정
```
> git config --global user.name "John Doe"
> git config --global user.email johndoe@example.com
```

## 코드 받아오기

github 또는 bitbucket 그 밖의 git server 서비스를 통해 저장소를 가져온다.
이때 보통 GitHub에 등록된 opensource의 경우 fork를 이용해 자신의 저장소에 복사한 후 clone한다고 한다.

변경 후에 pull request

- clone
```
> git clone 주소
```

## 변경을 공유하기

- add

커밋하기 전에 저장을 원하는 파일들을 스테이지에 올린다. 스테이징한다고 표현하기도 함.

```
> git add 파일
```

- commit

스테이지에 올라온 파일들을 가지고 내 컴퓨터에 저장(게임의 세이브에 해당)

```
> git commit -m "코드 설명"
```

커밋 메세지를 입력하는 것이 좋다.

**메세지는 명료하고 이해하기 쉽게**
```
1번째 줄: 커밋 내의 변경 내용을 요약
2번째 줄: 빈 칸
3번째 줄: 변경한 이유
```
주로 위의 형식으로 작성한다고 한다.

- push

원격 저장소에 업로드하는 명령어 
commit은 현재 작업 내용의 세이브 데이터가 내 컴퓨터에만 저장된 것.

```
> git push 원격 저장소명 원격 브랜치명
```

## 브랜치 관리하기
1. 브랜치(branch): 기능 변경을 하고 싶을 때 생성 및 사용
2. 머지(merge): 한 브랜치의 내용을 다른 브랜치에 반영
3. 체크아웃 (checkout): 저장소에서 특정 커밋이나 브랜치로 돌아가고 싶을 때 사용

- branch

현재 선택된 브랜치를 기준으로 생성
```
> git branch 브랜치 이름
> git branch 브랜치 이름 분기하려는 커밋
```

브렌치 삭제
```
> git branch -d 브랜치 이름
> git branch -D 브랜치 이름 // 강제 삭제
```

- checkout

브랜치 이동 
```
> git checkout 브랜치 이름
```

브랜치 만들고 이동
```
> git checkout -b 브랜치 이름
```

마지막 커밋으로 돌아가기(코드뭉치 버리기)
```
> git checkout 파일이름
```
- merge

먼저 어떻게 바뀌었는지 확인해보기
```
> git diff 원래 브랜치 비교할 브랜치
```

1. 작업한 브랜치 내용을 다른 브랜치와 합쳐야 할 때 사용
2. 충돌 발생 가능

A 브랜치에서 B를 병합할때 (A<-B)

```
> git checkout A 브랜치명
> git merge B 브랜치명
```

**최신 코드를 받을려면?**

- pull
코드를 받아와(fetch) 변경점을 merge한다. (충돌 발생 가능)
```
> git pull
```
- fetch
코드를 받아온다. 
```
> git fetch
```

### 충돌은?
- 자동병합을 실패했을 경우 발생
- 주로 두 커밋이 같은 파일을 편집했을 경우 발생
- merge, pull 사용 시 발생

### 해결방법은?
충돌난 파일을 읽어가며 수동으로 수정한다.
- 에디터를 이용한 해결

내것 또는 저장소 것 선택하기
- sourceTree를 이용한 해결

병합툴도 있음,,, 

## Git 되돌리기 

1. Reset: 이력을 그 당시로 되돌리기 (커밋 날아감)
2. 새로운 브랜치를 만들어서 체크아웃
3. Revert: 이전 이력은 그대로 두고, 되돌릴 커밋의 코드만 선택한 커밋의 내용으로 바꿈

git의 코드의 상태

1. uncommit: 파일의 내용을 바꾼 상태
2. staying: 파일의 변경 내역을 add하여 index에 추가한 상태 (스테이지에 올린 상태)
3. 변경 내용을 commit으로 확정
4. commit이 완료되면 서버에 push

### Reset 
```
> git reset 옵션 돌아가고싶은 커밋
```
옵션에는 자주 쓰이는 것 hard, soft, mixed가 있음

1. hard

돌아가려는 커밋 이후의 모든내용(코드 포함)을 모두 지워버린다. uncommit의 전

```
> git reset --hard 커밋
```

2. soft

돌아가려던 이력으로 돌아는 갔지만 이후의 내용은 지워지지 않고 인덱스(스테이지)도 남아있음
staying상태

```
> git reset --soft 커밋
```

3. mixed 

선택한 커밋으로 돌아가지만 soft처럼 내용은 지워지지않는다. 하지만 staying상태가 아닌 uncommit상태

**푸쉬한 상태라면?**

pull 내역이 남기 때문에 그냥 push가 안된다. 
1. 강제 푸시 git push --force : 커밋 날라감
2. 나눠진 분기(원격저장소)를 merge한 후에 충돌을 해결하고 commit 후 push

단점: 이전 커밋이 날라가기 때문에 비추!

### 브랜치를 만들어서 커밋 되돌리기

원하는 분기에서 브랜치를 만든 후에 merge하기 (충돌이 발생함)

### Revert 

커밋이 사라지지 않음
하지만 충돌이 날 가능성이 높다!
```
> git revert 커밋
> git revert 커밋범위 // 범위로 되돌리고 싶을 경우 
// 최신부터 순서대로 
```

>특정한 커밋만 취소하고 싶으면 revert, 또한 이미 push한 코드라면 force라는 옵션이 있지만 revert가 나을 수도...

## 코드를 잠깐 저장하기 stash

코드를 작성중에 잠깐 다른 브랜치로 이동하고 싶은데 commit해두기에는 애매할 경우 사용

- 저장
```
> git stash 
또는
> git stash save
```

- 목록 확인
```
> git stash list
```

- stash 적용
```
> git stash apply // 가장 최근의 stash 적용
> git stash apply stash이름
```

- 스테이지 상태까지 복원

```
> git stash apply --index
```

- 제거

```
> git stash drop // 가장 최근꺼 삭제
> git stash drop stash 이름
> git stash pop // apply + drop
```

## 그 외

- log

히스토리 조회
```
> git log 
```

- gitk

git의 내장 GUI
```
> gitk
```

working directory에 있는 파일의 상태 확인
```
> git status
```

- HEAD 

HEAD는 현재 체크아웃된 커밋을 가리킨다. 즉, 현재 작업중인 커밋 (가장 최근 커밋)

작업트리에 변화를 주는 git 명령어들은 대부분 HEAD를 변경하는것으로 시작함
