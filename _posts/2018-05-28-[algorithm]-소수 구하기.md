# 소수 구하기

문제번호 :  1929번

문제링크 : [https://www.acmicpc.net/problem/1929](https://www.acmicpc.net/problem/1929)

----------

## 문제 ##

M이상 N이하의 소수를 모두 출력하는 프로그램을 작성하시오.




## 입력 ##

첫째 줄에 자연수 M과 N이 빈 칸을 사이에 두고 주어진다. (1≤M≤N≤1,000,000)




## 출력 ##

한 줄에 하나씩, 증가하는 순서대로 소수를 출력한다.




## 예제 ##
### 입력 ###

	3 16

### 출력 ###

	3
	5
	7
	11
	13

## 풀이 ##

소수는  자신보다 작은 ( 1을 제외한 )수로 나누어 떨어지지 않는 수를 소수라고 한다.



n= a*b이라고 할때, a >= √n 이면, a * b = n = √n * √n 이므로, b<=√n 된다.

이를 통해서 자신보다 작은 모든 수가 아니라 자신의 제곱근값보다 작은 수들을 소수 판별하는 것이 더 효율적이다.

<에라토스테네스의 체 >

모든 자연수는 하나 이상의 소수의 곱으로 표현할 수 있다.

이것을 이용해서 소수를 구하는 방법이다.

2가 아닌 2의 배수들은 소수가 아니다.

3이 아닌 3의 배수들은 소수가 아니다.

5가 아닌 5의 배수들을 소수가 아니다.

....

이를 이용해서 소수를 구해보자.



## 코드


	#include<iostream>
	#include<cstring>
	#define IOFAST() ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL);
	using namespace std;
	int main(){
		IOFAST();
		
		int m, n;
		bool arr[1000001];
		cin >> m >> n; 
		memset(arr, true, sizeof(arr));
		arr[0] = arr[1] = false; // 0과 1은 소수가 아님.
		
		for (int i = 2; i<=sqrt(1000000); i++){ //2~ 1000까지 소수 판별(중복방지를 위해서)
	
			if (arr[i]== false)	continue;	//소수가 아니면 PASS
	
			for (int j = 2; j <= n/i; j++){	//소수(자신)를 제거한 소수의 배수들을 모두 제거(i*j<=n)
				arr[i*j] = false;
			}
		}
		for (int i = m; i <= n; i++){
			if (arr[i]==true) cout << i << '\n';
		}
		return 0;
	}

​	
	
