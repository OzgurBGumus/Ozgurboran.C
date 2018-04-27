#include <stdio.h>
#include <string.h>
#include <conio.h>
//    0=BOŞ 1=Player1 2=Player2

int fharf();
int fsayi();
int kare_olustur(int matris[][8]);
int main(){
	int degisken, hamle1=2, hamle2=1, m, n, hamle, satir, sutun, x;
	int matris[8][8];
	for (m=0;m<8;m++)
	for (n=0;n<8;n++)
	matris[m][n]=0;
	matris[3][3]=2;
	matris[3][4]=1;
	matris[4][3]=1;
	matris[4][4]=2;
	kare_olustur(matris);
	
	for(hamle=0;hamle<60;hamle++){		
		degisken=hamle1; /* HAMLE1 HER TUR O KISIYE AIT RAKAMI ALACAK. */
		hamle1=hamle2;
		hamle2=degisken;
		printf("%d. OYUNCU______\n", hamle1);
		baslik:
		satir=fharf();
		sutun=fsayi();
		if(satir>=8 || satir<0 || sutun>=8 || sutun<0 || matris[satir][sutun]!=0){
			printf("GECERSİZ HAMLE"); goto baslik;
		}
		if(matris[satir-1][sutun]==hamle2 || matris[satir+1][sutun]==hamle2 || matris[satir][sutun-1]==hamle2 || matris[satir][sutun+1]==hamle2 || matris[satir-1][sutun-1]==hamle2 || matris[satir+1][sutun+1]==hamle2 || matris[satir+1][sutun-1]==hamle2 || matris[satir-1][sutun+1]==hamle2){
			
			
			//İHTİMALLER
			
			for(n=satir+1;n<8;n++){
				if(matris[n][sutun]==0){
					break; //OLMADI
				}
				else if(matris[n][sutun]==hamle2){
					continue;
				}
				else if(matris[n][sutun]==hamle1){
					n=n-satir-1;
					for(;n>=0;n--){
						matris[satir+n][sutun]=hamle1;
					}
					x++; //GECERLİ BİR HAMLE OLDUGUNUN KANITI;
					break;
				}
				else
				break; //OLMADI
			}
			for(n=satir-1;n>0;n--){
				if(matris[n][sutun]==0){
					break; //OLMADI
				}
				else if(matris[n][sutun]==hamle2){
					continue;
				}
				else if(matris[n][sutun]==hamle1){
					n=satir-n-1;
					for(;n>=0;n--){
						matris[satir-n][sutun]=hamle1;
					}
					x++; //GECERLİ BİR HAMLE OLDUGUNUN KANITI;
					break;
				}
				else
				break; //OLMADI
			}
			for(n=sutun+1;n<8;n++){
				if(matris[satir][n]==0){
					break;
				}
				else if(matris[satir][n]==hamle2){
					continue;
				}
				else if(matris[satir][n]==hamle1){
					n=n-sutun-1;
					for(;n>=0;n--){
						matris[satir][sutun+n]=hamle1;
					}
					x++;
					break;
				}
				else
				break;
			}
			for(n=sutun-1;n>0;n--){
				if(matris[satir][n]==0){
					break;
				}
				else if(matris[satir][n]==hamle2){
					continue;
				}
				else if(matris[satir][n]==hamle1){
					n=sutun-n-1;
					for(;n>=0;n--){
						matris[satir][sutun-n]=hamle1;
					}
					x++;
					break;
				}
				else
				break; //OLMADI
			}
			m=sutun;
			for(n=satir+1;n<8;n++){
				m=m++;
				if(matris[n][m]==0){
					break;
				}
				else if(matris[n][m]==hamle2){
					m++;
					continue;
				}
				else if(matris[n][m]==hamle1){
					n=n-satir-1;
					m=m-sutun-1;
					for(;n>=0;n--){
						if(m>=0){
							matris[satir+n][sutun+m]=hamle1;
						}
						else break;
					}
					x++;
					break;
				}
				else
				break; //OLMADI
			}
			m=sutun;
			for(n=satir-1;n>0;n--){
				m=m--;
				if(matris[n][m]==0){
					break;
				}
				else if(matris[n][m]==hamle2){
					m--;
					continue;
				}
				else if(matris[n][m]==hamle1){
					n=satir-n-1;
					m=sutun-m-1;
					for(;n>=0;n--){
						if(m>=0){
							matris[satir-n][sutun-m]=hamle1;
						}
						else break;
					}
					x++;
					break;
				}
				else
				break;
				
			}
			m=sutun;
			for(n=satir-1;n>0;n--){
				m=m++;
				if(matris[n][m]==0){
					break;
				}
				else if(matris[n][m]==hamle2){
					m++;
					continue;
				}
				else if(matris[n][m]==hamle1){
					n=satir-n-1;
					m=m-sutun-1;
					for(;n>=0;n--){
						if(m>=0){
							matris[satir-n][sutun+m]=hamle1;
						}
						else break;
					}
					x++;
					break;
				}
				else
				break;
			}
			m=sutun;
			for(n=satir+1;n>8;n++){
				m--;
				if(matris[n][m]==0){
					break;
				}
				else if(matris[n][m]==hamle2){
					m--;
					continue;
				}
				else if(matris[n][m]==hamle1){
					n=n-satir-1;
					m=sutun-m-1;
					for(;n>=0;n--){
						if(m>=0){
							matris[satir+n][sutun-m]=hamle1;
						}
						else break;
					}
					x++;
					break;
				}
				else
				break;
			}
			if(x==0){
				printf("GECERSİZ HAMLE"); goto baslik;	
			}
			else{
				kare_olustur(matris);	
			}
			
			
			}
			else{
			printf("GECERSİZ HAMLE"); goto baslik;
			
			
			
			
		}
		x=0;
		}
	return 0;
	}
	//////////////////////////////////////////////////////////////////////////////
int kare_olustur(int matris[][8]){
	int n, m=0;
	for(n=0;n<8;n++){
	
	switch(n){
		case 0:
			printf("A");
			break;
		case 1:
			printf("B");
			break;
		case 2:
			printf("C");
			break;
		case 3:
			printf("D");
			break;
		case 4:
			printf("E");
			break;
		case 5:
			printf("F");
			break;
		case 6:
			printf("G");
			break;
		case 7:
			printf("H");
			break;
	}	
	for(m=0;m<8;m++){
		if(matris[n][m]==0)
		printf(" :");
		else if(matris[n][m]==1)
		printf("X:");
		else if(matris[n][m]==2)
		printf("O:");
		if(m==7)
		printf("\n");
	}
	if(n==7)
	printf(" 1 2 3 4 5 6 7 8\n");
	}
return 0;
}
/////////////////////////////////////////////////////////////////////////
int fharf(){
	char harf;
	int harf1;
	printf("Harf Giriniz.\t\t:::");
	hata:
	scanf("%c", &harf);
	if(harf=='A' || harf=='a')
	harf1=0;
	else if(harf=='B' || harf=='b')
	harf1=1;
	else if(harf=='C' || harf=='c')
	harf1=2;
	else if(harf=='D' || harf=='d')
	harf1=3;
	else if(harf=='E' || harf=='e')
	harf1=4;
	else if(harf=='F' || harf=='f')
	harf1=5;
	else if(harf=='G' || harf=='g')
	harf1=6;
	else if(harf=='H' || harf=='h')
	harf1=7;
	else
	goto hata;
	
	return harf1;
}
//////////////////////////////////////////////////////////////////////////////
int fsayi(){
	int sayi;
	printf("Sayi giriniz.\t\t==");
	scanf("%d", &sayi);
	return sayi-1;
}
///////////////////////////////////////////////////////////////////////////////

	
	
