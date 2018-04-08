###   ###

문제번호 : 2750 번

문제링크 : [https://www.acmicpc.net/problem/2750](https://www.acmicpc.net/problem/2750)

----------

## 문제 ##

N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.



## 입력 ##

첫째 줄에 수의 개수 N(1<=N<=1,000)이 주어진다. 둘째 줄부터 N개의 줄에는 숫자가 주어진다. 이 수는 절대값이 1,000보다 작거나 같은 정수이다. 수는 중복되지 않는다.



## 출력 ##

첫째 줄부터 N개의 줄에 오름차순으로 정렬한 결과를 한 줄에 하나씩 출력한다.



## 예제 ##
### 입력 ###

	5
	5
	2
	3
	4
	1

### 출력 ###

	1
	2
	3
	4
	5


## 풀이 ##
정렬의 기초를
버블정렬과 삽입정렬을 통해 구해보았다.  
> 버블정렬은 두 인접한 원소의 대소를 비교해 가장 큰 값을 n-1,n-2..에 차례대로 정렬되는 방법이다.flag를 넣은 이유는 비교가 끝난 경우 반복문을 빠져나오기 위해서 사용했다.
> 삽입정렬은 모든 요소를 앞에서부터 차례대로 비교하여 자신의 위치를 찾아서 삽입하는 방법이다.



## 코드 ##
	
	
		#include<iostream>
		#include<cstring>
		#include<algorithm>
	
		int main(){
	
			int n,flag, i,j,tm;
			scanf("%d", &n);
			int* arr = new int[n];
			for (i = 0; i < n; i++)	
				scanf("%d", arr+i);
			//버블정렬
			for (j = 0; j < n; j++){
				flag = 0;
				for (i =1; i < n - j; i++){
					if (arr[i - 1] >= arr[i]){
						tm = arr[i - 1];
						arr[i - 1] = arr[i];
						arr[i] = tm;
						flag = 1;
					}
				}
				if (flag == 0) break;
			}
			/* //삽입정렬
			for (i = 1; i < n; i++){		
				key = arr[i];
				for (j = i - 1; j >= 0; j--){ 
					if (arr[j] <= key)	break;
					arr[j + 1] = arr[j];
				}
				arr[j + 1] = key;
			} */
			for (i = 0; i < n; i++)	
				printf("%d \n", *(arr + i));
	
		}
