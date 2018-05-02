### 괄호 ###

문제번호 : 9012 번

문제링크 : [https://www.acmicpc.net/problem/9012](https://www.acmicpc.net/problem/9012)



## 문제 ##



괄호 문자열(Parenthesis String, PS)은 두 개의 괄호 기호인 ‘(’ 와 ‘)’ 만으로 구성되어 있는 문자열이다. 그 중에서 괄호의 모양이 바르게 구성된 문자열을 올바른 괄호 문자열(Valid PS, VPS)이라고 부른다. 한 쌍의 괄호 기호로 된 “( )” 문자열은 기본 VPS 이라고 부른다. 만일 x 가 VPS 라면 이것을 하나의 괄호에 넣은 새로운 문자열 “(x)”도 VPS 가 된다. 그리고 두 VPS x 와 y를 접합(concatenation)시킨 새로운 문자열 xy도 VPS 가 된다. 예를 들어 “(())()”와 “((()))” 는 VPS 이지만 “(()(”, “(())()))” , 그리고 “(()” 는 모두 VPS 가 아닌 문자열이다. 

여러분은 입력으로 주어진 괄호 문자열이 VPS 인지 아닌지를 판단해서 그 결과를 YES 와 NO 로 나타내어야 한다. 




## 입력 ##



입력 데이터는 표준 입력을 사용한다. 입력은 T개의 테스트 데이터로 주어진다. 입력의 첫 번째 줄에는 입력 데이터의 수를 나타내는 정수 T가 주어진다. 각 테스트 데이터의 첫째 줄에는 괄호 문자열이 한 줄에 주어진다. 하나의 괄호 문자열의 길이는 2 이상 50 이하이다. 




## 출력 ##



출력은 표준 출력을 사용한다. 만일 입력 괄호 문자열이 올바른 괄호 문자열(VPS)이면 “YES”, 아니면 “NO”를 한 줄에 하나씩 차례대로 출력해야 한다. 




## 예제 ##
### 입력 ###

	6
	(())())
	(((()())()
	(()())((()))
	((()()(()))(((())))()
	()()()()(()()())()
	(()((())()(

### 출력 ###

	NO
	NO
	YES
	NO
	YES
	NO

## 풀이 ##

)괄호가 (괄호를 만나면 스택에서 pop되는 방식으로, 마지막괄호까지 검사하여 스택에 남은 괄호가 있으면 NO 없으면 YES를 출력하도록 하였다.

1. 괄호를 입력받아서 str변수에 저장시킴
2. str의 길이만큼 for문을 돌려서 괄호 하나씩 검사
   1. ')' 일 경우 스택에 있는 '('를 pop함 만약 첫번째, 스택이 비었을때 ')'입력이 되면 반복문을 빠져나와 바로 NO를 출력하도록 하였다.
   2. '('  일 경우 스택에 push
3. 반복문을 빠져나와서 스택에 남은 괄호가 없으면 YES, 있으면 NO를 출력하고 스택을 비워준다.


## 코드 ##


	#include<iostream>
	#include<string>
	#include<stack>
	#define IOFAST() ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL);
	using namespace std;
	
	int main(){
		IOFAST();
	
		int t, j;
		string str;
		stack<char> st;
		cin >> t;
	
		for (int i = 0; i < t; i++){
			str = "";
			cin >> str;
			for (j = 0; j<str.length(); j++){
				if (str[j] == ')'){
					if (st.empty()) {// ) 가 맨처음 들어온경우(예외처리)
						st.push(str[j]); 
						break;
					} 
					st.pop(); //(를 빼냄
				}
				else{
					st.push(str[j]);
				}
			} //for
			if (st.empty() ){
				cout << "YES\n";
			}
			else{
				cout << "NO\n";
				while (!st.empty()) st.pop();
			}
			
		}
	
		return 0;
	}
	


​	
​	
