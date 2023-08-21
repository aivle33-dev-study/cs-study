# 코드 소유자 등록하는 방법

### 코드 소유자(Code Owners)란?

Github에는 Code Owner라는 기능이 있는데, Repository 내에 특정 파일이나 특정 디렉토리, 원하면 특정 확장자 별로도 Owner를 지정하여 파일 및 코드를 관리할 수 있는 방식이다.

이를 활용하면 코드리뷰를 위해 PR 생성 시, 작업한 파일에 관련된 Owner들을 자동으로 PR(Pull Request) Reviewer로 지정할 수 있다.

### 사용 방법

팀 프로젝트에서 main 브랜치에 대한 merge 권한을 특정한 한 명만 갖도록 설정하려면 GitHub의 보호 기능을 활용하여 다음과 같이 진행할 수 있습니다.

1. Repository Settings 설정
    - 해당 리포지토리로 이동하고 상단 탭에서 "Settings"을 클릭합니다.
    - 왼쪽 메뉴에서 "Branches"를 선택합니다.
    - "Branch protection rules" 섹션에서 "Add rule" 버튼을 클릭합니다.

2. Branch Protection Rule 생성
    - "Branch name pattern"에 main 또는 master를 입력하여 해당 브랜치를 선택합니다.
    - "Require pull request reviews before merging" 옵션을 활성화합니다.
    - "Include administrators" 옵션은 선택 해제합니다.
    - "Require review from Code Owners" 옵션을 활성화합니다.
    - "Dismiss stale pull request approvals when new commits are pushed" 옵션은 선택 여부를 결정합니다. 이 옵션을 선택하면 새로운 커밋이 푸시될 때 이전의 승인이 자동으로 해제됩니다.
    - "Require signed commits" 옵션은 선택 여부를 결정합니다. 필요하다면 활성화할 수 있습니다.

3. Code Owners 파일 설정
    - .github/CODEOWNERS 파일을 생성하고 열어줍니다.
    - main 브랜치에 대한 승인 권한을 가진 사용자를 지정합니다. 아래 예시와 같이 작성합니다:


### 기본 문법
```
# 프로젝트 내 모든 디렉토리 및 파일 대상으로 오너를 user-a로 지정할 경우.
* @user-a

# JS 파일에 관련된 오너로 user-a와 user-b 두 명으로 지정 할 경우.
*.js @user-a @user-b

# 어느 경로 상관 없이 src/atoms/button.tsx 경로의 패턴을 가진 파일의 오너를 user-a로 지정할 경우.
src/atoms/button.tsx @user-a

# 레포 내 root의 '/docks/'의 하위 디렉토리 전체를 user-a로 지정할 경우.
/docs/ @user-a

# 어느 경로 상관 없이 docs/ 바로 하위의 파일들에만 user-a로 할 경우.(ex: docs/readme.md)
# 단, docs/build-app/readme.md 처럼 중첩 경로는 안됨.
docs/* @user-a

# 어느 경로 상관 없이 docs/build-app/ 패턴을 가진 경로 하위로 모두 user-a와 user-b로 지정할 경우.
docs/build-app/ @user-a @user-b

# 레포 내 root의 '/apps/' 하위 전체를 nunu로 지정하되, '/apps/github' 제외할 경우.
/apps/ @user-a
/apps/github
```

### References

- [Github Docs - About code owners](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)
- [Tistory Blog - [Github](Code Owner로 Auto Assign 하기](https://helloinyong.tistory.com/329)

<br>

# PR Template 생성하는 방법

1. Repository 루트 경로 내에 `.github` 폴더를 만든다
2. 위 폴더 내부에 `pull_request_template.md` 파일을 만든다
3. 위 마크다운 파일을 작성하면 다음 PR 요청 시 자동으로 comment 내용이 설정된다

### References
- [Github Docs - Create a PR Template](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)
- [Tistory Blog - [Git] GitHub pull request template 만들기](https://wecandev.tistory.com/150)
