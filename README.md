# decline-number_-
# c
음이 아닌 정수 X의 자릿수가 가장 큰 자릿수부터 작은 자릿수까지 감소한다면, 그 수를 감소하는 수라고 한다. N번째 감소하는 수를 출력하는 프로그램을 작성해보자! 0은 0번째 감소하는 수이고, 1은 1번째 감소하는 수이다. 만약 N번째 감소하는 수가 없다면 -1을 출력한다.
순서대로 해보자면 0번째부터 9번째 감소하는 수는 0, 1, 2, 3, 4, 5, 6, 7, 8, 9가 되고 여기까지가 한자리다. 두자리에선 10, 20, 21, 30, 31, 32, … 순서로 세자리에선 210, 310, 320, 321, … 순서로 올라가게된다.

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main(){
	int n;
	scanf("%d",&n);
	long long number[100];
	int start,end;
	int current;
	int i,j,k;
	for(i=0;i<10;i++){
		number[i]=i;}
	start=0;
	end=9;
	current=10;//0과9까지 넣고나서 다음은 10 
	for(i=1;i<10;i++){//10의 승수를 알려줌 i=2면, 10의2승으로 100
	    for(j=i;j<10;j++){//j는 맨앞자리수  
	    	for(k=start;k<=end;k++){ //감소하는 수  
	    		if(number[k] / pow(10.0,i-1) <j){//해당수의 맨앞자리수가 j보다 작은경우  
	    			number[current++]=j*pow(10.0,i)+number[k]; //pow(a,b)== a의 b승  
	    			if(current>n){
	    				printf("n번째로 감소하는 수: %d\n",number[n]);
	    				return 0;}}}}
		start=end+1;
		end=current-1;}
	printf("n번째에서 감소하는 수가 없어서 -1\n");
	return 0;
}
