# Quest 00. 형상관리 시스템

## Introduction
* git은 2021년 현재 개발 생태계에서 가장 각광받고 있는 버전 관리 시스템입니다. 이번 퀘스트를 통해 git의 기초적인 사용법을 알아볼 예정입니다.

## Topics
* git
  * `git clone`, `git add`, `git commit`, `git push`, `git pull`, `git branch`, `git stash` 명령
  * `.git` 폴더
* GitHub

## Resources
* [Resources to learn Git](https://try.github.io)
* [Learn Git Branching](https://learngitbranching.js.org/?locale=ko)
* [Inside Git: .Git directory](https://githowto.com/git_internals_git_directory)

## Checklist
* 형상관리 시스템은 왜 나오게 되었을까요?
  * 프로젝트에서 발생하는 변경사항을 체계적으로 추적하고 통제하여 관련된 사람에게 보고 함으로써 여러사람들과 협업 시 프로젝트의 완성도를 높이고 실수를 줄이기 위해서 사용한다.
* git은 어떤 형상관리 시스템이고 어떤 특징을 가지고 있을까요? 분산형 형상관리 시스템이란 무엇일까요?
  * git 은 분산형 버전관리 시스템으로 Repository 의 완전한 복사본을 로컬에 저장 가능하다. 로컬에서 모든 히스토리를 기록하여 처리속도가 빠르지만 대용량 코드 관리에 부적절하다.
  * 분산형 형상관리 시스템 : 각 개발자가 중앙 서버에 접근하지 않고 코드작업을 할수있다. 각 개발자의 독립적으로 작업한 후 변경사항을 병합/거절한다.
* git은 어떻게 개발되게 되었을까요? git이 분산형 시스템을 채택한 이유는 무엇일까요?
  * 대다수 리눅스 커널 개발자들이 비트키퍼에 대한 접근을 포기한 후 리누스 토르발스가 비트키퍼와 같은 시스템을 사용하고자 했지만 자신에게 맞는 접근이 자유로운 시스템을 찾지 못해 만들게 된 분산형 개발 관리 체계이다. 이 때 아래의 목표를 세웠다.
    * 빠른 속도
    * 단순한 구조
    * 비선형적인 개발(수천 개의 동시 다발적인 브랜치)
    * 완벽한 분산
    * Linux와 같은 대형 프로젝트에도 유용할 것
* git과 GitHub은 어떻게 다를까요?
  * git은 버전관리 툴, github은 git을 이용한 서비스다. Github에서 제공하는 서비스를 활용하여 여러사람들이 하나의 저장소를 가지고 보다 쉽게 협업할 수 있다.
* git의 clone/add/commit/push/pull/branch/stash 명령은 무엇이며 어떨 때 이용하나요? 그리고 어떻게 사용하나요?
  * clone: 원격 저장소의 데이터를 카피
  * add: commit을 하기전에 변경된 사항들을 추가
  * commit: 로컬 저장소에 staged된 변경사항들에 대하여 변경을 확정짓고 기록
  * push: 로컬 저장소에 남긴 기록들의 히스토리를 원격 저장소에 적용
  * pull: 원격저장소의 변경사항들을 로컬 저장소로 가져와 merge
  * branch: 작업트리를 다룰 수 있는 명령어
  * stash: 현재 작업중인 변경사항을 임시 공간에 저장해두기 위한 명령어
* git의 Object, Commit, Head, Branch, Tag는 어떤 개념일까요? git 시스템은 프로젝트의 히스토리를 어떻게 저장할까요?
  * Object: git이 파일을 관리하기 위해 파일을 만드는데 이를 Object라고 하며, tree, blob, commit, tag 4가지로 이루어져있다.
  * Commit: '작업 트리'에 있는 변경내용을 바로 저장소에 기록하는 것이 아니라 그사이 '인덱스'에 파일 상태를 기록
  * Head: 마지막 커밋 스냅샷 다음 커밋의 부모 커밋
  * Branch: 코드 수정시 원래 코드와 상관없이 독립적으로 개발을 진행할때 원래 코드에서 새로운 버전을 생성한것
  * Tag: 커밋을 참조하기 쉽도록 알기 쉬운 이름을 붙이는 것
* 리모트 git 저장소에 원하지 않는 파일이 올라갔을 때 이를 되돌리려면 어떻게 해야 할까요?
  1. git reset 사용
  2. git revert 사용

## Quest
* GitHub에 가입한 뒤, [이 커리큘럼의 GitHub 저장소](https://github.com/KnowRe-Dev/WebDevCurriculum)의 우상단의 Fork 버튼을 눌러 자신의 저장소에 복사해 둡니다.
* Windows의 경우 같이 설치된 git shell을, MacOSX의 경우 터미널을 실행시켜 커맨드라인에 들어간 뒤, 명령어를 이용하여 복사한 저장소를 clone합니다.
  * 앞으로의 git 작업은 되도록 커맨드라인을 통해 하는 것을 권장합니다.
* 이 문서가 있는 폴더 바로 밑에 있는 sandbox 폴더에 파일을 추가한 후 커밋해 보기도 하고, 파일을 삭제해 보기도 하고, 수정해 보기도 하면서 각각의 단계에서 커밋했을 때 어떤 것들이 저장되는지를 확인합니다.
* `clone`/`add`/`commit`/`push`/`pull`/`branch`/`stash` 명령을 충분히 익혔다고 생각되면, 자신의 저장소에 이력을 push합니다.

## Advanced
* Mercurial은 어떤 형상관리 시스템일까요? 어떤 장점이 있을까요?
* 실리콘밸리의 테크 대기업들은 어떤 형상관리 시스템을 쓰고 있을까요?
