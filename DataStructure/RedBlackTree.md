# Red-Black Tree

[알고리즘 ) Red-Black Tree](https://zeddios.tistory.com/237)

1. **Root Property** : 루트노드의 색깔은 **검정(Black)**이다.

2. **External Property** : 모든 **external node들은 검정(Black)**이다.

3. **Internal Property** : 빨강(Red)노드의 자식은 **검정(Black)**이다.

== No Double Red(빨간색 노드가 연속으로 나올 수 없다.)

4. **Depth Property** : 모든 리프노드에서 **Black Depth는 같다.** 

== 리프노드에서 루트노드까지 가는 경로에서 만나는 블랙노드의 개수는 같다.
### Reconstructing

**1. 나(z)와 내 부모(v), 내 부모의 부모(Grand Parent)를 오름차순으로 정렬**

**2. 무조건 가운데 있는 값을 부모로 만들고 나머지 둘을 자식으로 만든다.**

**3. 올라간 가운데 있는 값을 검정(Black)으로 만들고 그 두자식들을 빨강(Red)로 만든다.**

![restructing1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile4.uf.tistory.com%2Fimage%2F99F7BD3359CF679E2A66F5)

![restructing2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile29.uf.tistory.com%2Fimage%2F99C2FF3359CF699A316DCD)

### Recoloring

**1. 현재 insert된 노드(z)의 부모와 그 형제(w)를 검정(Black)으로 하고 Grand Parent(내 부모의 부모)를 빨강(Red)로 한다.**

**2. Grand Parent(내 부모의 부모)가 Root node가 아니었을 시 Double Red가 다시 발생 할 수 있다. Double Red가 발생하면 재귀적으로 실행 (Reconstructing이 발생할 수 있다).**

![recoloring1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile21.uf.tistory.com%2Fimage%2F9978F93359CF6CD72B3E2E)

![recoloring2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile8.uf.tistory.com%2Fimage%2F9970483359CF6D5E33619F)

# 질문

- 이분탐색이 아닌 b-tree사용하는 이유가 뭘까