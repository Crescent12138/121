# 121
#include <stdio.h>
#include <math.h>
#include<iostream>
#include<cstdlib>
#include<ctime>
using namespace std;
#define  ll long long 
#define N 1e9
typedef struct node{
	int x;
	long long  y;
}T;
T x[1005];

void quickSort(T s[], int l, int r)
{
	T tmp;
	if (l < r)
	{
		int i = l, j = r, x = s[l].x;
		while (i < j)
		{
			while (i < j && s[j].x >= x) // 从右向左找第一个小于x的数
				j--;
			if (i < j) {
				tmp = s[i];
				s[i++] = s[j];
				s[j] = tmp;
			}
			while (i < j && s[i].x < x) // 从左向右找第一个大于等于x的数
				i++;
			if (i < j) {
				tmp = s[j];
				s[j--] = s[i];
				s[i] = tmp;
			}
		}
		s[i].x = x;
		quickSort(s, l, i - 1); // 递归调用
		quickSort(s, i + 1, r);
	}
}

void rander(int i) {
		x[i].x = (rand()*31)%40+160;
}
int main() {
	srand((unsigned int)time(NULL));
	int tim = 6;
	while (tim--) {
		int k = 1;
		memset(x, 0, sizeof(x));
		for (long long i = 2007310201;i <= 2007310260;i++) x[k++].y = i;
		for (int i = 1;i <= 60;i++) rander(i);
		quickSort(x, 1, 60);
		for (int i = 1;i <= 60;i++) {
			printf("%d\t%lld\t%d\t|", i,x[i].y, x[i].x);
			if (i % 5 == 0)cout << endl;
		}
		cout << endl;
	}
}
