---
comments: true
title: PIP Install Option
key: 202007025
picture_frame: shadow
tags:
  - Python
---
# pip Install Option

-   pip install --help로 Option 리스트를 볼 수 있음
-   help 명령어는 Keyword를 한눈에 보기 어려워 Option List를 정리하고자 함
-   현재문서는 단순 설명을 번역하는 수준밖에 되지 않지만 직접 사용해보면서 설명이나 know-how를 추가하겠음

## 설치 옵션

**\-r, --requirement**

-   requirements file을 명시하여 설치하고자 여러개의 package를 한번에 설치
    
-   requirements file의 형식은 다음과 같음
    
    ```
    # Python Excel
    pyexcel==0.5.8
    pyexcel-xls==0.5.7
    pyexcel-xlsx=0.5.6
    
    # DB Connector
    pyhive==0.6.0
    ```
    

**\-c --constraint**

-   설치 package의 version에 대한 제약 조건 파일을 명시
-   constraint file은 requirements.txt 파일에 -c 형태로도 명시 할 수 있음
-   constraint file은 requirements.txt 파일과 구분하여 package 관리를 좀 더 깔끔하게 할 수 있음
-   pip 8.0 이후에는 hash key를 이용한 버전 제약 조건을 관리하는것이 더 좋을 수 있음
-   참조: [https://stackoverflow.com/questions/34645821/pip-constraints-files/34653182](https://stackoverflow.com/questions/34645821/pip-constraints-files/34653182)

**\-no-deps**

-   의존성 package들을 설치 하지 않음

**\--pre**

-   시험판이나 개발 버전을 설치 할 수 있도록 함
-   기본적으로 pip는 stable version만을 설치함
-   module 개발을 한다거나 필요한 기능의 module을 테스트 할 때 활용 할 수 있음

**\--e, --editable <path/url>**

-   setuptools의 develop mode 처럼 패키지를 수정 가능한 모드로 설치 할 수 있음
-   project path를 명시하거나 형상관리(Git, SVN 등)툴의 url을 명시 할 수 있음

**\-t, --target**

-   패키지를 설치하고자 하는 경로를 명시하여 설치 할 때 사용
-   기본적으로 이 옵션은 기존 파일/폴더를 대체하지 않고 해당 명령이 수행 될 때만 경로를 변경해서 설치
-   의 기존 패키지를 새 버전으로 바꾸려면 --upgrade 옵션을 사용할 것
    

**\--user**

-   사용자 경로에 설치함

**--root**

-   root directory에 설치를 한다고 하는데 잘 모르겠음

**--prefix**

-   lib,bin 및 기타 최상위 폴가 있는 설치 접두사
-   \-t, --user, --root, --prefix 이 것들은 정확히 무엇을 위한 옵션인지는 모르겠음.
-   python package directory 관리를 위한 옵션이라는 것을 알겠으나,
-   어떤 디렉토리들을 설정하고 그 디렉토리들이 python에서 어떻게 참조되는지 명확한 이해가 필요할 듯
-   또한 직접 사용해보면서 삽질을 많이 해봐야겠음
-   참조: [링크](https://stackoverflow.com/questions/25333640/pip-python-differences-between-install-option-prefix-and-root-and)

**\-b, --build**

-   패키지 압축해제 및 빌드할 디렉토리 명시
-   초기 빌드는 임시 디렉토리
-   임시 디렉토리의 위치는 Linux에서는 TMPDIR 환경 변수를 설정하고 Windows에서는 TEMP 환경 변수를 설정하여 제어 할 수 있음
-   빌드가 될 때 실패되면 빌드 디렉토리는 clean 되지 않음

**\-src**

-   편집 가능한 프로젝트를 check out할 디렉토리
-   virtualenv의 기본값은 " / src"
-   전역 설치의 기본값은 " / src"

**\-U, --upgrade**

-   패키지를 최신 버전으로 업그레이드
-   종속성 처리는 upgrade-strategy에 따름

**\--upgrade-strategy <upgrade\_strategy>**

-   종속성 업그레이드를 처리하는 방법 결정\[default: only-if-needed\]
-   종속성 업그레이드 처리 방법은 두 종류가 있고 자세한 설명은 다음과 같음  
    · "eager": 현재 설치된 버전이 업그레이드 된 패키지의 요구 사항을 충족 하는지 상관 없이 종속성이 업그레이드 됨  
    · "only-if-needed": 업그레이드 된 패키지의 요구 사항을 충족하지 않는 경우에만 업그레이드 됨

**\--force-reinstall**

-   무조건 모든 패키지를 재설치함
-   최신 버전의 패키지라도 무조건 재설치함

**\--l, --ignore-installed**

-   설치가 되어있는 패키지들은 무시함

**\--ignore-requires-python**

-   Requires-Python 정보를 무시함

**\--no-build-isolation**

-   최신 소스 배포를 빌드 할 때 isolation을 비활성화함
-   이 옵션을 사용하는 경우 PEP 518에서 지정한 빌드 종속성이 이미 설치되어 있어야함

**\--install-option**

-   setup.py install 명령에 arguments들을 명시
-   ex) --install-option="--install-scripts = /usr/local/bin"
-   여러개의 arguments를 명시할 수 있음
-   디렉토리 경로 옵션을 추가하는 경우에는 절대 경로를 사용해야함

**\--global-option**

-   setup.py global options을 명시

**\--compile**

-   Python 소스 파일을 바이트 코드로 컴파일

**\--no-compile**

-   Python 소스 파일을 바이트 코드로 컴파일 하지 않음

**\--no-warn-script-location**

-   PATH 외부에서 설치 할 때 warn 표시하지 않음

**\--no-warn-conflicts**

-   깨진 의존성에 대해 warn 표시하지 않음

**\--only-binary**

-   소스 패키지를 사용하지 않음
-   여러번 명시 할 수 있으며 명시 할 때 마다 기존 값에 추가되는 형태
-   format\_control의 종류는 2가지고 있고 자세한 설명은 다음과 같음  
    · all: 모든 소스 패키지 비활성화  
    · none: 세트를 비우기 위해 사용됨. 하나이상의 패키지를 비우려면 패키지 이름 사이에 comma 사용
-   바이너리 배포판이 없는 패키지의 경우 이 옵션을 사용하면 설치 되지 않음\\

**\--prefer-binary**

-   최신 소스 패키지보다 오래된 바이너리 패키지 우선 설치

**\--no-clean**

-   build directory들을 clean up 하지 않음

**\--progress-bar <progress\_bar>**

-   progress의 종류를 설정함\[pretty|off|on|ascii|emoji\]

**\-i, --index-url**

-   Python Package Index의 기본 url 명시(default: [http://pypi.org/simple](http://pypi.org/simple))
-   PEP 503 (단순 저장소 API)를 준수하거나 또는 동일한 형식으로 배치된 로컬 디렉토리 url을 사용해야함

**\--extra-index-url**

-   python package index를 추가 url들을 명시
-   \--index-url과 동일한 정책을 따름

**\--no-index**

-   package index 무시

**\-f, --find-links**

-   html 파일의 URL 또는 경로인 경우 아카이브에 대한 링크를 구문 분석함
-   로컬 경로 또는 file:// url이 디렉토리인 경우 디렉토리 목록에서 아카이브를 찾음.

**\--process-dependency-links**

-   의존성 링크의 프로세싱을 가능하게 함