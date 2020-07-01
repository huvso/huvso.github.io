---
comments: true
title: PostgreSQL Index Type
key: 2020-07-02
picture_frame: shadow
tags:
  - PostgreSQL
---


# postgreSQL Index Type
- Version Info : PostgreSQL(Ver 9.6)


1. B-tree
	- Default Tree 방식
&nbsp;

2. hash
	- 동등 비교 최적화
&nbsp;

3. GiST(Generalized Search Tree)
	- 지역 분석 최적화
	- 참조: https://www.postgresql.org/docs/9.2/static/gist.html
&nbsp;

4. GIN(Generalized Inverted Index)
	- 여러값을 하나의 Row에 맵핑(Arrays and full-text searchs 이용)
	- 참조: https://www.postgresql.org/docs/9.2/static/gin.html
&nbsp;

5. SP-GiST(Space-Partitioning Generalized Search Tree)
	- 인-메모리 최적화, 파티셔닝 구조가
	- 참조: PostgreSQL: https://www.postgresql.org/docs/9.2/static/spgist.html
	- 참조: http://www.sai.msu.su/~megera/wiki/spgist_dev
&nbsp;

6. BRIN(Block Range INdex)
	- 사이즈가 제한된 큰 데이터 사용 시 최적
	- 참조: https://www.postgresql.org/docs/9.6/static/brin.html