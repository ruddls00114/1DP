#  DFS와 BFS#

문제번호 : 1260 번

문제링크 : [https://www.acmicpc.net/problem/1260](https://www.acmicpc.net/problem/1260)

----------

## 문제 ##

그래프를 DFS로 탐색한 결과와 BFS로 탐색한 결과를 출력하는 프로그램을 작성하시오. 단, 방문할 수 있는 정점이 여러 개인 경우에는 정점 번호가 작은 것을 먼저 방문하고, 더 이상 방문할 수 있는 점이 없는 경우 종료한다. 정점 번호는 1번부터 N번까지이다.



## 입력 ##

첫째 줄에 정점의 개수 N(1 ≤ N ≤ 1,000), 간선의 개수 M(1 ≤ M ≤ 10,000), 탐색을 시작할 정점의 번호 V가 주어진다. 다음 M개의 줄에는 간선이 연결하는 두 정점의 번호가 주어진다. 한 간선이 여러 번 주어질 수도 있는데, 간선이 하나만 있는 것으로 생각하면 된다. 입력으로 주어지는 간선은 양방향이다.




## 출력 ##

첫째 줄에 DFS를 수행한 결과를, 그 다음 줄에는 BFS를 수행한 결과를 출력한다. V부터 방문된 점을 순서대로 출력하면 된다.




## 예제 ##
### 입력 ###

	4 5 1
	1 2
	1 3
	1 4
	2 4
	3 4

### 출력 ###

	1 2 4 3
	1 2 3 4

## 풀이 ##
## 코드 ##


	#include<iostream>
	#include<vector>
	#include<queue>
	#include<cstring>
	#include<algorithm>
	#define IOFAST() ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL);
	using namespace std;
	
	vector <int> check;
	//vector <int> check_b;
	vector <vector<int>> a;
	void dfs(int n){
		check[n] = 1;
		cout << n << " ";
		for (int i = 0; i < (signed int)a[n].size(); i++){
			int m = a[n][i];
			if (check[m] == 0)
				dfs(m);
		}
	}
	void bfs(int n){
		queue <int> q;
		check[n] = 1;
		q.push(n);
		while (!q.empty()){
			int m = q.front();
			q.pop();
			cout << m << " ";
			for (int i = 0; i<(signed int)a[m].size(); i++){
				int w = a[m][i];
				if (check[w] == 0){
					check[w] = 1;
					q.push(w);
				}
			}
	
		}
	
	}


	int main(){
		IOFAST();
		//bfs dfs
		int i, v, e, n;
		cin >> v >> e >> n;
		check.resize(v + 1,0);
		a.resize(v + 1);
		for (i = 1; i <= e; i++){
			int u, v;
			cin >> u >> v;
			a[u].push_back(v);
			a[v].push_back(u);
	
		}
		for (i = 1; i <=v; i++){
			sort(a[i].begin(), a[i].end());
		}
		dfs(n);
		check.clear(); check.resize(v + 1);
		cout << '\n';
		bfs(n);
	
		return 0;
	}

​	
​	
