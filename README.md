# NUGU developers 문서

본 페이지는 NUGU developers 문서를 보관하고 있는 저장소입니다.

NUGU developers 문서는 누구나 아래의 절차를 통해 문서의 개정을 요청하실 수 있습니다.

## 문서 사이트 구조

NUGU developers 문서는 markdown 문서로서 [Jekyll](https://jekyllrb.com/) `4.2.2` 버전으로 제작되었으며, 추가적인 plugin 은 [jekyll-spaceship](https://github.com/jeffreytse/jekyll-spaceship), [jekyll-potion](https://github.com/nugudevelopers/jekyll-potion) 을 사용합니다.

또한 GitHub Actions 를 통해 빌드하고 빌드된 결과물을 `gh-pages` 라는 브랜치로 archiving 하여 서비스 하도록 구성되어 있습니다. 

### 디렉토리 구조

NUGU developers 는 다음과 같이 예약된 디렉토리 구조를 가지며, 문서 작성시 해당 디렉토리를 이용해 문서를 작성합니다.

만일 정해진 경로 규칙에 맞지 않게 작업된 문서 개정 요청의 경우 문서 관리자는 개정 요청을 거부할 수 있습니다.

| 경로명                       | 설명                                                                                                                                          | 작업 가능 여부  | 
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|:---------:|
| _jekyll-potion            | NUGU developers 문서 구동을 위한 필수 라이브러리입니다.<br/>[jekyll-potion](https://github.com/nugudevelopers/jekyll-potion) 의 변경 요청은 링크를 통해 해당 프로젝트에 공헌하세요. |     N     |
| _plugins                  | NUGU developers 문서의 layout을 구성하는 디렉토리이며 수정할 수 없습니다.                                                                                         |     N     |
| assets/favicon            | NUGU developers 사이트의 favicon 을 보관하는 디렉토리이며 수정할 수 없습니다.                                                                                      |     N     |
| assets/files              | NUGU developers 사이트의 이미지를 제외한 정적 요소를 보관하는 디렉토리입니다.                                                                                          |     Y     |
| assets/images             | NUGU developers 사이트의 이미지를 보관하는 디렉토리입니다.                                                                                                     |     Y     |
| assets/img                | NUGU developers 사이트 구성을 위한 이미지를 보관하는 디렉토리이며 수정할 수 없습니다.                                                                                     |     N     |
| developers                | [jekyll-potion](https://github.com/nugudevelopers/jekyll-potion) 의 NUGU developers 용 theme 디렉토리이며 수정할 수 없습니다.                               |     N     | 
| _config.jekyll_potion.yml | [Jekyll](https://jekyllrb.com/) 을 구성하는 파일로서 수정할 수 없습니다.                                                                                     |     N     |
| Gemfile                   | [Jekyll](https://jekyllrb.com/) 을 구성하는 파일로서 수정할 수 없습니다.                                                                                     |     N     |
| Gemfile.lock              | [Jekyll](https://jekyllrb.com/) 을 구성하는 파일로서 수정할 수 없습니다.                                                                                     |     N     |
| _config.yml               | [Jekyll](https://jekyllrb.com/) 을 구성하는 파일로서 수정할 수 없습니다.                                                                                     |     N     |
| _config.*.yml             | [Jekyll](https://jekyllrb.com/) 을 구성하는 파일로서 수정할 수 없습니다.                                                                                     |     N     |
| 404.html                  | [Jekyll](https://jekyllrb.com/) 을 구성하는 파일로서 수정할 수 없습니다.                                                                                     |     N     |
| README.md                 | NUGU developers 문서 제작 가이드로서 수정할 수 없습니다.                                                                                                     |     N     |

이외의 디렉토리, 파일은 정적 요소일 경우 `assets`에, markdown 문서일 경우 최상단 디렉토리를 기준으로 작성할 수 있습니다.

하위 페이지의 경우, 확장자를 제외한 페이지명과 동일한 이름의 디렉토리를 작성할 경우 하위 페이지로서 표현됩니다.

## 환경 구축하기

NUGU developers 문서는 [GitHub 저장소](https://github.com/nugudevelopers/document-staging) 를 fork 하여 작업한 후 [pull requests](https://docs.github.com/en/pull-requests) 를 통해 문서 개정 요청을 할 수 있습니다.

### 프로젝트 fork 하기

[Fork a repo](https://docs.github.com/en/get-started/quickstart/fork-a-repo) 를 통해 https://github.com/nugudevelopers/document-staging 를 `document-staging` 라는 저장소로 fork 합니다.

프로젝트명은 반드시 `document-staging` 로 지정되어야 합니다.

만일 이를 변경하고자 한다면, `_config.staging.yml` 파일 내 `baseurl` 값도 변경한 프로젝트명으로 변경해야 하며, pull requests 를 보낼 때 제외하여야 합니다.

기본적으로 `main`, `gh-pages` 브랜치는 반드시 copy 되어야 올바른 문서로 표현되기 때문에 `Copy the main branch only` 는 반드시 해제한 후 fork 합니다.

### GitHub Pages 활성화하기

1. [Creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) 을 참조하여 access token 을 생성하고 생성된 값을 복사합니다.
2. [Creating encrypted secrets for a repository](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) 을 참조하여 1번에서 생성한 access token 을 `GITHUB_TOKEN` 라는 이름으로 `Actions scrests` 으로서 생성합니다. 
3. [Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) 를 참조하여, `Settings` > `Pages` 로 이동합니다.
4. `Builde and deployment` 섹션 내 `Source` 를 `Deploy from a branch`, `Branch` 는 `gh-pages`, `/ (root)` 를 선택한 후 `Save` 버튼을 클릭합니다.
5. `Actions` 로 이동하여 1번째 workflow 가 녹색으로 완료되면 웹브라우저를 통해 `https://{계정명}.github.io/developers-staging/` 를 접속하여 NUGU developers 문서 사이트가 정상적으로 구동됨을 확인합니다. 

## 문서 작성하기

문서를 작성할 때는 반드시 브랜치를 생성하여 작업해야 합니다.

자세한 내용은 [Creating a branch](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository#creating-a-branch) 를 참고하세요.

프로젝트 환경이 구성되었으면, 문서 작업자는 각자의 환경에 맞게 주로 사용하는 text 에디터를 통해 markdown 문서를 작성하거나, 변경하고 필요한 정적 요소(이미지, 파일...)등을 업로드할 수 있습니다.

기본적으로는 markdown 문법이 준수된 문서라면 어떤 형태여도 상관없으며, [jekyll-spaceship](https://github.com/jeffreytse/jekyll-spaceship) 에서 제공하는 문법, [jekyll-potion](https://github.com/nugudevelopers/jekyll-potion)의 [태그](https://nugudevelopers.github.io/jekyll-potion/components/tag) 를 지원합니다.

[jekyll-potion](https://github.com/nugudevelopers/jekyll-potion)의 [태그](https://nugudevelopers.github.io/jekyll-potion/components/tag) 는 각 태그별 선언, 그리고 선언에 대한 설명만 이해하고 있다면 작성이 가능합니다.

만일 [jekyll-spaceship](https://github.com/jeffreytse/jekyll-spaceship) 에서 제공하는 문법, [jekyll-potion](https://github.com/nugudevelopers/jekyll-potion) 에서 제공하는 문법 간의 충돌이 발생한다면, [jekyll-spaceship](https://github.com/jeffreytse/jekyll-spaceship), [jekyll-potion](https://github.com/nugudevelopers/jekyll-potion) 순으로 적용됩니다. 

또한 수정되는 부분이 여러 페이지일 경우, 하나의 수정건으로 작업되어야 합니다.

반드시 모든 수정이 끝난 경우에만 pull requests 를 요청하세요.

### GitHub 를 통해 문서 작성하기

개인 PC 에 Ruby, [Jekyll](https://jekyllrb.com/) 을 설치하지 않은 경우, 작성할 수 있는 방법입니다.

GitHub 는 [Working with files](https://docs.github.com/en/repositories/working-with-files) 를 통해 웹페이지를 통해 파일을 생성하거나 편집할 수 있습니다.

편집을 마친 후 저장을 하면 GitHub 는 자동으로 변경을 감지하여, workflow 를 통해 변경된 내용을 GitHub pages 에 반영합니다.

### 로컬에서 문서 작성하기

개인 PC 를 통해 NUGU developers 사이트를 구동시켜 수정되는 내용을 직접 확인하며 작성할 수 있는 방법입니다.

먼저 [Jekyll](https://jekyllrb.com/) 의 설치가 필요합니다. [설치 가이드](https://jekyllrb.com/docs/installation/) 를 참조하여 설치합니다.

만일 Git 에 익숙하지 않은 경우, [GitHub Desktop](https://desktop.github.com/) 설치를 권장합니다.

설치를 마친 후 fork 한 저장소를 [Cloning a repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) 를 통해 clone 받습니다.

clone 한 디렉토리로 이동한 후 아래의 명령어를 수행합니다.

```bash
bundle exec jekyll serve --config _config.yml,_config.jekyll_potion.yml,_config.staging.yml --trace
```

서버 구동이 끝나면, 웹브라우저를 통해 `http://localhost:4000/document-staging/` 를 접근하여 NUGU developers 문서가 제대로 구동됨을 확인합니다.

구동을 마친 후, 문서를 변경합니다. 변경한 문서는 일정한 시간을 두고 반영되니, 웹브라우저를 통해 확인합니다.

변경을 마친 후 [Creating and editing commits](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits) 을 참조하여, commit 을 생성합니다.

생성된 commit 을 [Pushing changes to GitHub](https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop/making-changes-in-a-branch/pushing-changes-to-github) 를 참조하여 push 합니다.

## pull requests 생성하기

작성한 문서를 수정한 후 fork 된 프로젝트의 Github Page 가 정확하게 수정됨을 확인했다면, [pull requests](https://docs.github.com/en/pull-requests) 를 통해 반영을 요청할 수 있습니다.

별도의 요청 양식은 존재하지 않으나, 희망하는 배포일정을 알려주시면 되도록 맞춰서 배포를 진행합니다. 

pull requests 는 문서 사이트 빌드 오류, 컨텐츠 들의 디렉토리 경로, 작성한 내용, merge 시 충돌 등을 검토하여 merge 되며 특이사항이 있는 경우 pull requests 의 댓글을 통해 커뮤니케이션합니다.

## 튜토리얼 따라하기

NUGU developers 문서의 형상은 Github 를 통해 관리되고 있습니다.

따라서 문서 작성을 위해서는 반드시 Github, Git 사용에 대한 이해가 필요합니다.

하지만 Github, Git 에 대한 경험이 부족한 경우 다음의 튜토리얼을 진행하시기 바랍니다.
