### 파일의 상태와 Git의 명령어

> Git은 다양한 명령어를 통해 Git을 조작하고 파일의 상태를 변경할 수 있음
> 

![파일의 상태 및 라이프사이클](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95564b9f-4c25-4f36-a03b-d4811d32a939/Untitled.png)

파일의 상태 및 라이프사이클

- Untracked - Git의 관리 대상이 아닌 파일. 스냅샷과 Staging Area 어디에도 포함되지 않은 파일
- Tracked - Git의 관리 대상에 포함되는 파일. 처음 Clone된 파일은 이 상태에 포함
    - Unmodified - Clone 혹은 Commit 이후 아직 아무것도 수정하지 않은 상태
    - Modified - 파일을 수정한 상태
    - Staged - 수정한 파일을 Commit할 예정인 상태

---

`$ git clone ‘주소' ‘폴더명’`

> 프로젝트를 내 클라이언트의 로컬로 복제
> 

`$ git status`

> 파일의 현재 상태 표시
> 

```swift
$ git status
On branch main // 현재 사용중인 branch
Your branch is up to date with 'origin/main'.

Changes not staged for commit: // 변경 사항이 staged 상태로 변경되지 않음 (작업 공간에 있음)
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md
```

`$ git add ‘파일명’`

> 파일을 Staged 상태로 변경, ‘파일명' 대신에 . 을 사용하면 폴더 내 모든 파일을 변경
> 

`$ git commit -m ‘커밋 메세지’`

> Staged 상태의 파일들의 변경 사항을 Git directory에 적용
> 

```swift
git commit -m "test"
[main 4f816ce] test // [main 브랜치에 적용] 커밋 메세지
 1 file changed, 12 insertions(+) // 변경된 파일의 수, 변경된 라인(+,-)의 수

# 커밋 메세지에서 줄바꿈하는 방법
" 를 열어놓고 텍스트를 입력하다가 엔터를 입력하면, 입력이 종료되지 않고 줄바꿈이 적용됨
```

`$ git branch ‘브랜치명’`

> 새로운 branch를 생성
> 

`$git checkout ‘브랜치명’`

> 현재 사용하는 branch를 다른 branch로 변경
> 

`$ git pull`

> 리모트 저장소(서버)에서 commit된 내용을 가져와서 로컬의 파일과 병합 (로컬 += 리모트)
> 

$ `git push`

> 로컬의 commit된 내용을 보내서 리모트 저장소의 내용과 병합 (리모트 += 로컬)
>
