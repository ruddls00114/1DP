### 조세퍼스 문제 ###

문제번호 : 1158 번

문제링크 : [https://www.acmicpc.net/problem/1158](https://www.acmicpc.net/problem/1158)

----------

## 문제 ##

조세퍼스 문제는 다음과 같다.

1번부터 N번까지 N명의 사람이 원을 이루면서 앉아있고, 양의 정수 M(≤ N)이 주어진다. 이제 순서대로 M번째 사람을 제거한다. 한 사람이 제거되면 남은 사람들로 이루어진 원을 따라 이 과정을 계속해 나간다. 이 과정은 N명의 사람이 모두 제거될 때까지 계속된다. 원에서 사람들이 제거되는 순서를 (N, M)-조세퍼스 순열이라고 한다. 예를 들어 (7, 3)-조세퍼스 순열은 <3, 6, 2, 7, 5, 1, 4>이다.

N과 M이 주어지면 (N,M)-조세퍼스 순열을 구하는 프로그램을 작성하시오.




## 입력 ##

첫째 줄에 N과 M이 빈 칸을 사이에 두고 순서대로 주어진다. (1 ≤ M ≤ N ≤ 5,000)




## 출력 ##

예제와 같이 조세퍼스 순열을 출력한다.




## 예제 ##
### 입력 ###

	7 3

### 출력 ###

	<3, 6, 2, 7, 5, 1, 4>

## 풀이 ##
입력받은 n만큼 자연수를 큐에 넣는다.(1~n까지)

v벡터에는 출력할 수를 넣을 것인데 이것의 크기가 n일때까지 반복문을 돌린다.

입력받은 m을 3이라고 생각했을때, 3이전의 수 1,2는 제거되지않고 다시 큐에서 반복되어야한다.그래서 큐에 다시 삽입해준다.

q.front가 3이면 큐에서 꺼내 벡터에 넣어준다. 

반복하다가 만약 큐의 사이즈가 m보다 작아지면 ? (큐의 사이즈는 2인데 3번째의 수를 뽑아야할때)

해결하기위해서 m을 다시 정의해준다. 처음에 입력받은 m(mm이라 선언)에서 큐의 사이즈를 빼준 새로운 m을 정의.





## 코드 ##


	#include<iostream>
	#include<vector>
	#include<queue>
	#include<utility> //pair
	#include<algorithm>
	#define IOFAST() ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL);
	using namespace std;
	
	int main(){
		IOFAST();
		int n, m, i,mm;
		cin >> n >> m;
		mm = m;
		queue<int> q;
		vector<int> v;
		for (i = 1; i <= n; i++){
			q.push(i);
		}
		while (v.size()!=n){
			int num;
			if (m == 1){
				num = q.front();
				q.pop();
				v.push_back(num);
			}
			else{
				for (i = 0; i < m - 1; i++){ //
					int temp = q.front();
					q.pop();
					q.push(temp);
				}
				num = q.front();
				q.pop();
				v.push_back(num);
			}
			if (q.size() < m){
				m = mm - q.size();
			}
			else{
				m = mm;
			}
		}
		cout << '<';
		for (i = 0; i < n-1; i++)
			cout << v[i] << ", ";
		cout << v[n-1] << '>';
		return 0;
	
	}


​	
​	
