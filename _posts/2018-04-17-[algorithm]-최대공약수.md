### 최대공약수 ###

문제번호 : 1850 번

문제링크 : [https://www.acmicpc.net/problem/1850](https://www.acmicpc.net/problem/1850)

----------

## 문제 ##

모든 자리가 1로만 이루어져있는 두 자연수 A와 B가 주어진다. 이 때, A와 B의 최대 공약수를 구하는 프로그램을 작성하시오.

예를 들어, A가 111이고, B가 1111인 경우에 A와 B의 최대공약수는 1이고, A가 111이고, B가 111111인 경우에는 최대공약수가 111이다.



## 입력 ##

첫째 줄에 두 자연수 A와 B를 이루는 1의 개수가 주어진다. 입력되는 수는 19자리를 넘지 않는 자연수이다.



## 출력 ##

첫째 줄에 A와 B의 최대공약수를 출력한다. 정답은 천만 자리를 넘지 않는다.



## 예제 ##

### 입력1 ###

	3 4 


### 출력1 ###

	1

### 입력2 ###

	3 6 


### 출력2 ###

	111


## 풀이 ##
>최대공약수 구하는 방법 : 유클리드 호제법  
>b =aq+r 일때 최대공약수 g(b,a) = g(a,r)  
>즉, a, b (b>a) 일 때 b%a = r이 되는데 이 때 a, b의 최대공약수랑 a,r의 최대공약수랑 같다.


 처음에는 이 문제를 두 개의 숫자를 입력받고, 그 숫자의 개수만큼 1을 만들어서 만들어진 두 수의 최대공약수를 구했다. 그 결과는 시간초과가 나왔다.  
그래서 다시 고민한 결과 만약 입력이 3 6 라면 111과 111111의 최대공약수를 바로 구하지 않고, 3과 6의 최대공약수(3)를 구해서 그 값만큼 1을 입력(111)하면 된다. 이렇게 했더니 결과는 런타임 에러..가 났다. 
이유의 정답은 문제에 있었다. 입력되는 수는 19**자리**를 넘지않는다. 19가 아닌 19자리이므로 int형으로는 담을수없다 long long int를 써서 해결하였다. 

## 코드 ##

			
	#include<iostream>
	#include<cstring>
	#include<algorithm>
	#include<math.h>
	using namespace std;
	long long int gcd(long long int h, long long int l);

	int main(){
		long long int arr[2], gcdNum;
		int i;
		for (i = 0; i < 2; i++){
			cin >> arr[i];
		}
		gcdNum = gcd(arr[0], arr[1]);
		for (i = 1; i <= gcdNum; i++){
			cout << "1";
		}
	}
	long long int gcd(long long int h, long long int l){
		long long int r, tmp;
		if (h < l){
			tmp = h;
			h = l;
			l = tmp;
		}
		do{
			r = h%l;
			h = l;
			l = r;
		} while (r != 0);
		return h;
	}
	
	
	
