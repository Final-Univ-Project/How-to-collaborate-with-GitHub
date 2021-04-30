# Git&Github 입문 도서

상태: GitHub

# 참고 도서

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled.png)

Do it!

(지옥에서 온 문서 관리자)

### 깃&깃허브 입문

-이지스 퍼블리싱

# Git 핵심 기능

1. 버전 관리 Version Control
2. 백업 Backup
3. 협업 Collaboration

# Git 관리 도구

## 1. Git Program (GUI)

자동차는 제품일까, 제품군일까? 정답은 제품군이다. 자동차라는 제품군 안에 A라는 자동차, B라는 자동차 등의 다양한 자동차들이 존재한다.

이와 마찬가지로, Git Program (Git Client Program)은 Git을 보다 편리하게 사용할 수 있도록 해준다. 

- Github Desktop
- 토터스 깃 TortoiseGit
- 소스트리 SourceTree

## 2. Git (CLI)

Git에서는 Linux 명령어를 사용한다.

- Git Bash ( [https://git-scm.com/](https://git-scm.com/) )

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/__2021-03-17_124634.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/__2021-03-17_124634.png)

# <1> 버전 관리

Git에서는 문서를 수정할 때마다 간단한 메모와 수정 내용을 Snapshot으로 찍어서 저장한다.

처음 Git으로 만들어졌을 때는 git 0.0.1이라는 일련번호가 붙은 채 배포된다. 프로그램 개발을 하면서 수정할 때마다 새로 번호를 붙여 이전 상태와 구별을 하는데, 이렇게 번호 등을 통해 구별된 것을 버전이라 한다.

## Git 저장소 만들기

Git repository를 만들고 싶은 Directory로 이동해서, Git을 초기화하면, 그 때부터 해당 Directory에 있는 파일들을 버전 관리할 수 있다.

```bash
// Git Repository를 만들 Directory로 이동하기
mkdir git-dir-name
cd git-dir-name

// Git 초기화하기
git init

// Git Repository 생성 확인하기
// (해당 Directory가 Git을 사용하면서 버전이 저장될 곳임)
ls -la
```

---

Git에서 Version을 관리하면 원래 파일이름은 유지하면서 파일에서 무엇을 변경하였는지를 변경 시점마다 저장할 수 있다. 또 각 Version마다 작업했던 내용을 확인할 수 있고, 그 Version으로 되돌아갈 수도 있다.

그렇다면 어떻게 파일이름은 그대로 유지하면서 수정내역을 기록하는 걸까?

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/creating_version_flow.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/creating_version_flow.png)

### 작업 디렉터리 Working Directory

= 작업 트리 Working tree

= 파일 수정, 저장 등의 작업을 하는 디렉터리

   (우리 눈에 보이는 디렉터리)

ex. 앞에서 생성했던 git-dir-name 디렉터리.

### 스테이지 Stage

= 스테이징 영역 Staging area

= Version으로 만들 파일이 대기하는 곳

ex. 작업 디렉터리에서 10개의 파일을 수정했는데, 4개의 파일만 버전으로 만들려면 4개의 파일만 Stage로 넘겨준다.

### 저장소 Repository

= Stage에서 대기하고 있던 파일들을 Version으로 만들어 저장하는 곳

파일 수정을 마치고, Stage에 다 넣었다면, 버전을 만들기 위해 Git에게 '커밋 commit' 명령을 내린다. 그렇게 되면 Stage에서 대기하던 파일이 모두 저장소에 저장된다.

(Stage와 Rspository는 눈에 보이지 않는 가상의 개념들이다. 이들은 깃을 초기화했을 때 만들어지는 .git 디렉터리 안에 숨은 파일 형태로 존재하는 영역이다.)

---

## 파일을 스테이징하기

작업 디렉터리에서 파일을 만들거나 수정을 마쳤다면 Stage에 파일을 추가한다. 이 때 Git에게 Version을 만들 준비를 하라고 알려주는 것을 '스테이징 Staging' 또는 'Stage에 올린다'라고 표현한다.

```bash
// 파일(.txt 등)을 Stage에 올리기
git add edited_file.txt

// Git 상태 확인하기
// (changes to be committed : 파일을 commit할 것이다.)
git status
```

## 파일 커밋하기

파일이 Stage에 있다면 이제 Version을 만들 수 있다. Git에서 Version을 만드는 것을 '커밋한다 commit'고 한다.

여기서 commit을 할 때는 그 Version에 어떤 변경사항이 있었는지 확인하기 위한 메시지를 기록해야 한다.

```bash
// 파일을 commit하기
// -m 옵션으로 commit과 함께 저장할 메시지를 적을 수 있다
git commit -m "message1"

// commit한 Version 정보 확인하기
// (commit한 사람, 만든 시간, commit 메시지 확인가능)
git log
```

## Staging과 Commit 한꺼번에 처리하기

commit 명령에 -am 옵션을 사용하면, Stage에 올리고 commit하는 과정을 한꺼번에 처리할 수 있다. 하지만 이 방법은 한 번이라도 commit한 적이 있는 파일을 다시 commit할 때만 사용할 수 있다.

```bash
// commit한 적이 있는 파일을 Staging하고 commit하기
git commit -am "message2"

// commit한 Version 기록 확인하기
git log
```

### [git status] Git 상태 확인하기

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%201.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%201.png)

- On branch master : 현재 master branch에 있다.
- No commits yet : 아직 commit한 파일이 없다.
- nothing to commit : commit할 파일이 없다.
- untracked files : 아직 한번도 Version관리하지 않은 파일.

### [git log] Commit 기록 확인하기

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%202.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%202.png)

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%203.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%203.png)

지금까지 만든 Version과 각 Version마다의 정보를 확인할 수 있다.

- 커밋 해시 commit hash (= 깃 해시 git hash) : commit을 구별하는 아이디.
- (HEAD→ master) : 해당 Version이 가장 최신이라는 표시.
- Author : 해당 Version을 누가 만들었는지.
- Date : 해당 Version이 언제 만들어졌는지.
- 커밋 로그 commit log : git log 출력 결과 정보들.
- — stat 옵션 : commit에 관련된 파일까지 출력.

### [git diff] 변경 사항 확인하기

대규모의 소스 코드를 수정하는 경우 최근 버전과 비교해서 어떤 부분이 다른지 확인하고 싶다. 

git diff 명령을 사용하면, 작업 디렉터리에 있는 파일과 Stage에 있는 파일을 비교하거나, Stage에 있는 파일과 Repository에 있는 최신 commit을 비교해서 수정한 파일을 commit하기 전에 최종적으로 검토할 수 있다.

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%204.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%204.png)

- line 맨 앞의 - : 파일에서 뒤의 내용이 삭제되었다는 표시.
- line 맨 앞의 + : 파일에서 뒤의 내용이 추가되었다는 표시.

이렇게 수정한 내용으로 다시 Version을 만들려면, Stage에 올리고 commit한다.

수정한 내용을 버리려면 git checkout 명령을 사용하여 수정한 내용을 취소한다.

## 버전 관리 단계(상태)

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%205.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%205.png)

- tracked 상태 : Git은 한 번이라도 commit한 파일의 수정여부를 계속 추적한다. 따라서 commit한 적이 있다는 표시.
- untracked 상태 : 한 번도 Git에서 버전관리를 하지 않았다.
- modified : 파일이 수정되었고, 아직 Stage에 올라가지 않은 상태.
- staged : Stage에 올라가있고, 아직 commit하기 직전인 상태.
- unmodified : commit을 끝내고, 수정사항이 반영되어 수정이 없다고 표시.

![Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%206.png](Git&Github%20%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%86%E1%85%AE%E1%86%AB%20%E1%84%83%E1%85%A9%E1%84%89%E1%85%A5%205d858d9e614a4c4e8e2576f5c67c06eb/Untitled%206.png)

## 되돌리기

### 작업 디렉터리에서의 되돌리기

```bash
// 작업 디렉터리에서 수정한 내용을 이전의 작업한 내용으로 되돌리기
git checkout — edited_file.txt
```

### Stage에서의 되돌리기

```bash
// 수정된 파일을 Stage에 올린 경우에 Staging 취소하기
// (잘 수행된 경우, unstaged 메시지를 출력한다)
git reset HEAD edited_file.txt
```

### commit에서의 되돌리기

```bash
// 가장 마지막에 한 commit 취소하기
git reset HEAD^

git reset --soft HEAD^  // commit하기 전 상태로
git reset --mixed HEAD^ // commit, staging하기 전 상태로
git reset --hard HEAD^  // commit, staging, 파일수정하기 전 상태로

// 특정 commit으로 되돌리기
git reset committed_hash

// commit을 되돌릴 때, 취소한 commit을 삭제하지 않고 되돌리기
git revert committed_hash
```