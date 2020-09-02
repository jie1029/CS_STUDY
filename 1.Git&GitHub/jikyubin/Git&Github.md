
# Git & Github

먼저 
- [인프런 git과 github](https://www.inflearn.com/course/git-and-github)의 강사님과 
- [누구나 쉽게 이해할 수 있는 git 입문](https://backlog.com/git-tutorial/kr/)
의 작성자님께 감사인사 드립니다.
- 그 외의 관련 글을 작성해주시는 분들 모두 감사드립니다.
- git 공부 시작!

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

- 브랜치 삭제
```
> git push --delete 원격 브랜치명
```

## 브랜치 관리하기
- 브랜치(bran
- 체크아웃 (checkout): 저장소에서 특정 커밋이나 브랜치로 돌아가고 싶을 때 사용

----
- branch

현재 선택된 브랜치를 기준으로 생성
```
> git branch 브랜치 이름
```
- checkout

브랜치 이동 시
```
> git checkout 브랜치 이름
```




충돌을 내보자
```
왜 충돌이 안날까?
```
이상하네

- merge

1. 작업한 브랜치 내용을 다른 브랜치와 합쳐야 할 때 사용
2. 충돌 발생 가능

A 브랜치에서 B를 병합할때 (A<-B)
현재 브랜치: HEAD 브랜치라고 함
```
> git checkout A 브랜치명
> git merge B 브랜치명
```

- 충돌


**최신 코드를 받을려면?**

- pull

코드를 받아와 변경점을 merge한다. (충돌 발생 가능)
```
> git pull
```
- fetch

코드를 받아온다. 
```
> git fetch
```


## 그 외

- log

히스토리 조회
```
> git log 
```