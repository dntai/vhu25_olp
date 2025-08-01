** Ý tưởng **


**Minh Họa**
```cpp
#include <iostream>
#include <cstring>
#include <fstream>

using namespace std;

#define FI "WLOOP.INP"
#define FO "WLOOP.OUT"

ifstream finp(FI);
ofstream fout(FO);

/* Kiem tra xau s co lap theo chu ky nao do khong? */
int LaXauLap(const char *s);

/* Kiem tra xau s co lap theo chu ky k */
int LaXauLapTheoChuKy(const char *s, int n, int k);

int nTests, nDem;
char s[256];

int main()
{
    nDem = 0;
    
    finp >> nTests;
    finp.ignore(1000,'\n');
    
    while(nTests>0)
    {
        finp.get(s,256,'\n');
        finp.ignore(1000,'\n');
        
        nDem = nDem + LaXauLap(s);
    
        nTests = nTests - 1;
    }// while
    
    fout << nDem;
    
    finp.close();
    fout.close();
    
    return 0;
}// main

int LaXauLapTheoChuKy(const char *s, int n, int k)
{
    int i, j;
    
    /* Do dai n phai la boi so cua chu ky k */
    if(n%k!=0) return 0;
    
    /* Duyet va kiem tra tung ky tu trong doan lap dau giong voi cac doan lap khac */
    for(i=0; i<=k-1; i++)// duyet tung vi tri trong doan lap dau
    {
        /* 
        So sanh ky tu tai vi tri i trong doan dau co giong voi cac doan khac? 
        Chi dung khi hoac khong tim thay (j>n-1) hoac co 1 ky tu khac (s[i]!=s[j])
        */
        j= i + k;
        while(j<=n-1 && s[i]==s[j]) j = j + k;
        /* Neu tim thay 1 ky tu khac voi ky tu o doan lap dau */
        if(j<=n-1) return 0;
    }// for
    
    /* Khong co ky tu o vi tri trong doan lap dau khac voi cac doan lap khac! */
    return 1;
}// LaDoiXung

int LaXauLap(const char *s)
{
    int i, len;
    /* Kiem tra xau co chu ky 1, 2, ..., len(s)/2 */
    len = strlen(s);
    for(i=1;i<=len/2;i++)
    {
        /* Kiem tra xau s co lap theo chu ky i */
        if(LaXauLapTheoChuKy(s,len,i)) 
            return 1; // thoa man
    }// for
    
    return 0; // khong co chu ky nao thoa man
}// LaXauLap
```