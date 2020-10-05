## b-tree

[B-Tree Visualization](https://www.cs.usfca.edu/~galles/visualization/BTree.html)

### index

[](https://yurimkoo.github.io/db/2020/03/14/db-index.html)

- 컬럼을 인덱스 설정하면 해당 컬럼 조회(or 조인)가 빨라진다 O(N) → O(logN)
- 빠른 경우 : 조회시 인덱스가 걸린 컬럼을 WHERE와 함께 사용할 경우
- 삽입, 삭제시 성능 저하
- PK, FK 는 자동 index 생성
- 조회시 자주 사용하고 고유한 값 위주로 인덱스를 설정하는것이 좋다.

### 인덱스를 설정하기 좋은 컬럼

| 기준                     | 정도                        |
| ------------------------ | --------------------------- |
| 카디널리티 (Cardinality) | 높을 수록 적합              |
| 선택도 (Selectivity)     | 낮을 수록 적합 (5~10% 적정) |
| 활용도                   | 높을 수록 적합              |
| 중복도                   | 없을 수록 적합              |

- Cardinality: 가능한 값의 다양성?

  ```
  cardinality 가 낮은 경우의 대표적인 속성들로는 성별, 부서, 지역 등이 있을 수 있습니다.
  대표적으로는 성별로 들 수 있는데, 성별의 속성에는 남자, 여자 의 두개의 데이터 값만 들어 갈 수 있기 때문에
  cardinality 가 낮다고 이야기 할 수 있고,
  cardinality 가 높은 경우의 대표적인 속성들로는 주민번호, 사원번호 등이 있을 수 있고,
  대표적으로는 주민번호 를 들 수 있는데, 대한민국 전체 인구가 서로 다른 주민번호를 갖고 있기 때문에
  cardinality 가 높다고 이야기 할 수 있습니다.
  ```

- Selectivity: 특정 필드값을 지정했을 때 선택되는 레코드 수를 테이블 전체 레코드 수로 나눈 것

- 활용도: 쿼리를 날릴 때 WHERE 절에 자주 활용되는지

- 중복도

### Clustered index

[](https://docs.microsoft.com/ko-kr/sql/relational-databases/indexes/clustered-and-nonclustered-indexes-described?view=sql-server-ver15)

[클러스터드 인덱스와 넌 클러스터드 인덱스](https://lng1982.tistory.com/144)

[[SQL] 인덱스 (클러스터, 비클러스터) 개념](https://mongyang.tistory.com/75)

### Clustered vs Non-clustered

- Clustered
  - 테이블 당 하나
  - 물리적으로 재배열
  - 생성하면 데이터 전체를 다시 정렬하므로 데이터가 많다면 오래걸림
  - 검색 속도가 빠르지만 데이터 입력/수정/삭제는 느리다
  - 인덱스 리프 페이지 자체가 데이터 페이지
  - 같은 페이지의 메모리를 건드릴 확률이 높음
- Non-clustered
  - 여러개 생성 가능
  - 인덱스에 키와 포인터 저장 (로케이터)
  - 실제 데이터를 정렬하지 않고 인덱스만 바뀜
  - 검색 속도는 클러스터형 보다 느리지만, 입력/수정/삭제는 더 빠르다
  - 인덱스 자체의 리프 페이지는 데이터가 위치하는 포인터
  - 다른 페이지의 메모리를 건드릴 확률이 높음

