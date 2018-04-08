### 소트인사이드 ###

문제번호 : 1427 번

문제링크 : [https://www.acmicpc.net/problem/1427](https://www.acmicpc.net/problem/1427)

----------

## 문제 ##

배열을 정렬하는 것은 쉽다. 수가 주어지면, 그 수의 각 자리수를 내림차순으로 정렬해보자.


## 입력 ##

첫째 줄에 정렬하고자하는 수 N이 주어진다. N은 1,000,000,000보다 작거나 같은 자연수이다.


## 출력 ##

첫째 줄에 자리수를 내림차순으로 정렬한 수를 출력한다.


## 예제 ##
### 입력 ###

	2143


### 출력 ###

	4321


## 풀이 ##
1. N으로 받을 수 있는 최대값  1,000,000,000을 담을 수 있는 char형 크기가 10인 배열을 만든다. 
2. 내림차수 정렬할 수를 입력받고 각각의 값을 data[0]부터 data[length-1]까지 담는다.
3. algorithm 해더파일의 sort함수를 이용하여 정렬한다.   
		--> sort(정렬할 첫번째 주소, 마지막 주소 -1 )
4. 반복문을 length-1부터 0까지 돌려서 내림차순 정렬된 data출력 !




## 코드 ##

		
	#include<iostream>
	#include<cstring>
	#include<algorithm>

	using namespace std;
	
	int main(){
		char data[10];
		int i, len;
		cin >> data;
		len = strlen(data);
		sort(data, data + len);
		for (i = len-1; i >=0; i--){
			cout << data[i];
		}
		return 0;
	}
	
	
	
	
