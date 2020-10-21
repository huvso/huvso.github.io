---
comments: true
title: KoNLPy org.jpype.classloader.DynamicClassLoader Error 해결
key: 202010216
picture_frame: shadow
tags:
  - AI
---

# KoNLPy org.jpype.classloader.DynamicClassLoader Error 해결
  - 오늘(2020.10.21) 기준으로 Jpype가 1.1.0으로 업데이트 되었다.
  - 참조: [https://pypi.org/project/JPype1/](https://pypi.org/project/JPype1/)
  - 오늘 기준 이후로 KoNLPy를 기본으로 설치하게 되면 다음과 같은 에러가 나타날 것이다

  
  ```
  /usr/local/lib/python3.6/dist-packages/jpype/_core.py in startJVM(*args, **kwargs)
    214 
    215     try:
--> 216         _jpype.startup(jvmpath, tuple(args),
    217                        ignoreUnrecognized, convertStrings, interrupt)
    218         initializeResources()

  SystemError: java.lang.ClassNotFoundException: org.jpype.classloader.DynamicClassLoader
  ```
  - KoNLPy의 Dependancy 정보를 보면 다음과 같다.
  ```
  JPype1>=0.7.0
  beautifulsoup4==4.6.0
  colorama
  lxml>=4.1.0
  numpy>=1.6
  tweepy>=3.7.0
  ```

  - pip 명령어로 KoNLPy를 설치하게 되면 Dependancy에 따라, 오늘 업데이트된 JPype1 1.1.0으로 설치되게 된다.
  - 때문에, 버전 종속성을 제거하기 위해 가장 간단하게 KoNLPy 설치 전에 JPype1 0.7.0을 설치해주면 된다.
  - 설치 스크립트는 다음과 같다.
  ```
  pip install JPype1===0.7.0
  pip install konlpy
  ```