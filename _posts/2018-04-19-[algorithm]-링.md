### 링 ###

문제번호 : 3036 번

문제링크 : [https://www.acmicpc.net/problem/3036](https://www.acmicpc.net/problem/3036)

----------

## 문제 ##

상근이는 창고에서 링 N개를 발견했다. 상근이는 각각의 링이 앞에 있는 링과 뒤에 있는 링과 접하도록 바닥에 내려놓았다.   

![](https://www.acmicpc.net/upload/images/ring.png)

상근이는 첫 번째 링을 돌리기 시작했고, 나머지 링도 같이 돌아간다는 사실을 발견했다. 나머지 링은 첫 번째 링 보다 빠르게 돌아가기도 했고, 느리게 돌아가기도 했다. 이렇게 링을 돌리다 보니 첫 번째 링을 한 바퀴 돌리면, 나머지 링은 몇 바퀴 도는지 궁금해졌다.

링의 반지름이 주어진다. 이 때, 첫 번째 링을 한 바퀴 돌리면, 나머지 링은 몇 바퀴 돌아가는지 구하는 프로그램을 작성하시오.

## 입력 ##

첫째 줄에 링의 개수 N이 주어진다. (3 ≤ N ≤ 100)

다음 줄에는 링의 반지름이 상근이가 바닥에 놓은 순서대로 주어진다. 반지름은 1과 1000를 포함하는 사이의 자연수이다.


## 출력 ##

출력은 총 N-1줄을 해야 한다. 첫 번째 링을 제외한 각각의 링에 대해서, 첫 번째 링을 한 바퀴 돌리면 그 링은 몇 바퀴 도는지 기약 분수 형태 A/B로 출력한다.





## 예제 ##

### 입력 ###

	4
	12 3 8 4

### 출력 ###

	4/1
	3/2
	3/1

## 풀이 ##

가장앞의 링과 나머지 각각의 최대공약수를 구해 그것으로 나눈 몫.  
즉 
12 과 3 의 최대공약수 3으로 각각 12와 3을 나누면 4 / 1 를 구할 수 있다.


## 코드 ##


		
	#include<iostream>
	#include<cstring>
	#include<algorithm>

	using namespace std;
	int gcd(int h, int l);
	int main(){
		int t, h, l, q1, q2;
		int gcdNum,tmp;
		int* arr;
		cin >> t;
		arr = new int[t];
		for (int i = 0; i < t; i++)
			cin >> arr[i];
		
		for (int i = 1; i < t; i++){
			gcdNum = gcd(arr[0],arr[i]);
			cout << (arr[0] / gcdNum) << "/" <<(arr[i] / gcdNum)<< endl;
		}
	    
	}
	int gcd( int h, int l){
		int r;
		do{
			r = h%l;
			h = l;
			l = r;
		} while (r != 0);
		return h;
	}