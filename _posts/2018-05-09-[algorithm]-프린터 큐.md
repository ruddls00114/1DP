# 프린터 큐 #

문제번호 : 1966 번

문제링크 : [https://www.acmicpc.net/problem/1966](https://www.acmicpc.net/problem/1966)

----------

## 문제 ##

여러분도 알다시피 여러분의 프린터 기기는 여러분이 인쇄하고자 하는 문서를 인쇄 명령을 받은 ‘순서대로’, 즉 먼저 요청된 것을 먼저 인쇄한다. 여러 개의 문서가 쌓인다면 Queue 자료구조에 쌓여서 FIFO - First In First Out - 에 따라 인쇄가 되게 된다. 하지만 상근이는 새로운 프린터기 내부 소프트웨어를 개발하였는데, 이 프린터기는 다음과 같은 조건에 따라 인쇄를 하게 된다.

1. 현재 Queue의 가장 앞에 있는 문서의 ‘중요도’를 확인한다.
2. 나머지 문서들 중 현재 문서보다 중요도가 높은 문서가 하나라도 있다면, 이 문서를 인쇄하지 않고 Queue의 가장 뒤에 재배치 한다. 그렇지 않다면 바로 인쇄를 한다.

예를 들어 Queue에 4개의 문서(A B C D)가 있고, 중요도가 2 1 4 3 라면 C를 인쇄하고, 다음으로 D를 인쇄하고 A, B를 인쇄하게 된다.

여러분이 할 일은, 현재 Queue에 있는 문서의 수와 중요도가 주어졌을 때, 어떤 한 문서가 몇 번째로 인쇄되는지 알아내는 것이다. 예를 들어 위의 예에서 C문서는 1번째로, A문서는 3번째로 인쇄되게 된다.




## 입력 ##

첫 줄에 test case의 수가 주어진다. 각 test case에 대해서 문서의 수 N(100이하)와 몇 번째로 인쇄되었는지 궁금한 문서가 현재 Queue의 어떤 위치에 있는지를 알려주는 M(0이상 N미만)이 주어진다. 다음줄에 N개 문서의 중요도가 주어지는데, 중요도는 적절한 범위의 int형으로 주어진다. 중요도가 같은 문서가 여러 개 있을 수도 있다. 위의 예는 N=4, M=0(A문서가 궁금하다면), 중요도는 2 1 4 3이 된다.




## 출력 ##

각 test case에 대해 문서가 몇 번째로 인쇄되는지 출력한다.




## 예제 ##
### 입력 ###

	3
	1 0
	5
	4 2
	1 2 3 4
	6 0
	1 1 9 1 1 1

### 출력 ###

	1
	2
	5

## 풀이 ##


테스트케이스 개수를 입력받고, 그 수만큼 반복.

중요도와 찾고싶은 문서의 인덱스(0부터 시작)를 입력받는다(변수 n과 m )

중요도(imp)를 내림차순으로 넣기위해서 vector 를 만들고 (배열로 해도됨)

queue의 형을 pair형을 넣는다 그래서 pair의 first는 문서의 인덱스, second는 중요도 를 넣는다.
ex) 4 3 / 2 1 4 3

| vector | 4    | 3    | 2    | 1    |
| ------ | ---- | ---- | ---- | ---- |
| queue  | 0 2  | 1 1  | 2 4  | 3 3  |

그런다음,이중 반복문을 통해서 vector의 원소 순서대로, 즉 중요도가 큰 순서로 queue에서 그 값을 찾아 pop한다.pop할때는 pop된 문서의 수를 파악하기 위해서 cnt의 값을 +1 해주고,만약 pop하는 문서가 처음에 주어진 m문서라면 cnt값을 출력하고 모든반복문을 중단한다 (flag변수를 통해서)



## 코드 ##


	#include<iostream>
	#include<vector>
	#include<queue>
	#include<utility> //pair
	#include<algorithm> //sort
	#define IOFAST() ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL);
	using namespace std;
	
	int main(){
		IOFAST();
	
		int i, testcase;
		cin >> testcase;
		
		for (i = 0; i < testcase; i++){
			int  j, k, n, m, imp, cnt = 0,flag=0;
			queue <pair<int, int>> q;
			vector<int> v;
			cin >> n >> m; 		//문서의 수와 출력순서를 알고싶은 문서의 위치
			for (j = 0; j < n; j++){
				cin >> imp;
				v.push_back(imp);
				q.push(make_pair(j, imp));
			}
			sort(v.rbegin(), v.rend());	// 벡터를 거꾸로 정렬 (내림차순)
			
			for (k = 0; k < v.size(); k++){
	             if(flag==1) break;
				for (j = 0; j < q.size(); j++){
					if (v[k] == q.front().second){	//
						cnt++;
						if (m == q.front().first){
							cout << cnt << '\n';
							flag=1; 	//답을 찾았으니 첫번째 반복문을 끝내기 위해서 
						}
						q.pop();
						break;
					}
					else{	// 최대의 중요도가 아닐때 다시 큐에 삽입
						int a, b;
						a = q.front().first;
						b = q.front().second;
						q.pop();
						q.push(make_pair(a, b));
					}
				}
			}
	
		}//testcase
	
		return 0;
	
	}


​	
​	
