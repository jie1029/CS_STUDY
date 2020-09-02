# Git & Github

### git 기초 용어 요약

- clone : 원격 저장소 복사
- add : 스테이지 영역에 작업 파일 추가
- commit : 세이브, 스테이지 영역의 파일들을 가지고 커밋(==세이브) 생성.
- push : 원격 저장소에 커밋을 업로드한다.

    ### Master & Origin/Master & head

    - Master : branch중 root
    - origin/Master : 원격 저장소
    - head : 현재 작업중인 branch

# 조작하기

### 파일의 내용 되돌리기

- 특정 파일의 내용을 마지막 커밋으로 되돌릴 수 있음. ('코드 뭉치 버리기')

### 브랜치 변경하기

- 브랜치? : 기존 내용을 유지한 체 새로운 내용을 추가하고 싶을 때 사용
- 체크아웃 : 특정 브랜치(혹은 커밋) 으로 돌아가고 싶을 때 사용.
- 소스트리의 체크아웃 : 브랜치 이름을 더블 클릭하는 것만으로 체크아웃 가능.

### 병합하기 1

- 헤드 브랜치에 변경사항이 없고
- 병합 대상 브랜치가 헤드로부터 시작된 경우
- 아주 쉽게 병합 가능 ⇒ Fast-Forward

**충돌 시 충돌 내용 중에서 선택 할 수 있음**

⇒ 충돌이 안나려면? 다른 파일을 이용한다.

### 병합하기 2

- 헤드 브랜치에 추가적인 커밋이 생기는 경우
- 진짜 병합이 필요해짐.
- 충돌이 안나면 좋지만, 충돌이 나도 겁내지 말자.
- 충돌만 피하면 Fast-Forward가 가능.

### 충돌 해결하는 곳

일어날 수 있는 곳 : 

- pull ( : fetch + merge )
- merge

해결 방법 : 

- editor 에서 선택
- sourcetree등에서 내것or저장소것 선택

### 이전 커밋으로 되돌리기

- git reset —hard :  
origin/master, origin/HEAD는 원격에 push되어있는 곳이 있으면 그대로 남아있고,
master만 reset됨.
없다면???
    - 문제점 :  origin/master, origin/head 가 뒤로 갈 수 있음  
    ⇒ git push —force
    ⇒ merge 후( 충돌 : 내것 선택)  push (정상푸쉬)

    ⇒ 쉽다.

    ⇒ 강제푸쉬를 해야한다.  +  커밋이 날아간다.

- **branch를 만들어서 되돌리기**

    되돌아가려는 commit의 branch를 만든다.
    checkout후 merge

    ⇒ commit이 남아있다. + 쉽다

    ⇒ 트리가 지저분해진다.

- revert 되돌리기용
    - 여러 commit 되돌릴 때 : 최신 부터 순차적으로 revert를 반복.

    선택한 커밋을 취소해버린다.
    branch 생성 없이  commit 취소한 commit을 만들어 버린다.

    ⇒ commit이 남아있다.

    ⇒ 충돌이 날 수 있다.

![Git%20&%20Github%2072a9cd3f0f874dd3be107dd294f4c2f7/Untitled.png](Git%20&%20Github%2072a9cd3f0f874dd3be107dd294f4c2f7/Untitled.png)

reset은 commit이 사라진다.

![Git%20&%20Github%2072a9cd3f0f874dd3be107dd294f4c2f7/Untitled%201.png](Git%20&%20Github%2072a9cd3f0f874dd3be107dd294f4c2f7/Untitled%201.png)

revert는 commit이 남아있다.

## Commit 덮어쓰기

- checkout을 할 때는 변경된 사항이 없어야함.
- 임시로 commit을 해서 쓸데없는 commit이 있을 때 덮어쓸 수 있음.

push가 된 commit이라면 —push force로 건너 뛸 수 있음.

## STASH 생성

- checkout을 위해 commit되지않은 변경사항을 임시로 저장.
- untracked 파일은 stash에 올릴 수 없음.
⇒ stage에 올려줘야함.

## Rebase

- 장점 : 트리가 깔끔해진다.
- 단점 :  이미 원격저장소에 올라간 경우 + 협업 중인 경우 위험할 수 있다.

 -  merge 처럼 두 branch를 합칠 때 사용.

# **기타 주의 사항**

### **주석을 남기지 말자**

- 책상도 아니고, 장식장도 아니고 왜 안 쓰는 코드를 남겨놓을까요?

### **좋은 커밋의 단위**

- 커밋은 자주 합시다!
- 원자적으로 쪼갤 수 없는 단위 (주로 함수 등)의 의미있는 개발을 했다면 커밋을 합시다.

### **커밋 메시지를 잘 쓰자!**

- 정말정말 중요한 내용입니다.
- Github을 프로파일로 제출했다면? 커밋 메시지를 봅니다.
- 첫줄에 요약
- 한 줄 띄우고 자세하게 내용을 적자.
- 미래의 나를 위해서라도 커밋 메시지는 잘 적자!