# 미로 탐색 #

문제번호 : 2178 번

문제링크 : [https://www.acmicpc.net/problem/2178](https://www.acmicpc.net/problem/2178)

----------

## 문제 ##

N×M크기의 배열로 표현되는 미로가 있다.

| 1    | 0    | 1    | 1    | 1    | 1    |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1    | 0    | 1    | 0    | 1    | 0    |
| 1    | 0    | 1    | 0    | 1    | 1    |
| 1    | 1    | 1    | 0    | 1    | 1    |

미로에서 1은 이동할 수 있는 칸을 나타내고, 0은 이동할 수 없는 칸을 나타낸다. 이러한 미로가 주어졌을 때, (1, 1)에서 출발하여 (N, M)의 위치로 이동할 때 지나야 하는 최소의 칸 수를 구하는 프로그램을 작성하시오.

위의 예에서는 15칸을 지나야 (N, M)의 위치로 이동할 수 있다. 칸을 셀 때에는 시작 위치와 도착 위치도 포함한다.




## 입력 ##

첫째 줄에 두 정수 N, M(2≤N, M≤100)이 주어진다. 다음 N개의 줄에는 M개의 정수로 미로가 주어진다. 각각의 수들은 붙어서 입력으로 주어진다.




## 출력 ##

첫째 줄에 지나야 하는 최소의 칸 수를 출력한다. 항상 도착위치로 이동할 수 있는 경우만 입력으로 주어진다.




## 예제 ##
### 입력1

```
4 6
101111
101010
101011
111011
```

### 출력1

```
15
```

### 입력2

```
4 6
110110
110110
111111
111101
```

### 출력2

```
9
```



## 풀이





## 코드 ##




	#include<iostream>
	#include<cstring>
	#include<string>
	#include<queue>
	#include<utility>
	#define IOFAST() ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL);
	using namespace std;
	
	int v[110][110];
	int direct[4] = { -1, -1, 1, 1 };//위왼아오
	
	void bfs(int n, int m){
		queue <pair<int, int>> q;
		int  r, c, nr, nc;
		q.push(make_pair(1,1));
	
		while (!q.empty()){
			r = q.front().first;
			c = q.front().second;
			q.pop();
			if ((r < 1 || c < 1) || (r>n || c> m))	continue;
			for (int i = 0; i < 4; i++){
				nr = r; nc = c;
				if (i % 2 == 1){ //왼 오
					nc = c + direct[i];
				}
				else{			//위아
					nr = r + direct[i];
				};
	
	
				if (v[nr][nc] == 1){
					q.push(make_pair(nr, nc));
					v[nr][nc] = v[r][c] + 1;
	
					if (nr == n && nc == m){
						printf("%d", v[nr][nc]);
						return;
					}
				}
	
			}//for
			v[r][c] = 0;
	
		}
	}
	int main(){
	//	IOFAST();
		int  n, m;
		scanf("%d %d",&n,&m);
		for (int i = 1; i <= n; i++){
			for (int j = 1; j <= m; j++){
				scanf("%1d", &v[i][j]);
			}
		}
		bfs(n, m);
		return 0;
	}

​	
	
