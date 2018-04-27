#include <stdio.h>
#include <string.h>

int main(){
	
	int temp, temp1, backpack, temp2, i, i1, cesit, adet=0, total=0;
	float backpack1, agirlik;
	
	printf("item cesit sayisini giriniz::::\t");
	scanf("%d", &cesit);
	int matris[cesit][4];
	for(i=0;i<cesit;i++){
		for(i1=0;i1<4;i1++)
		matris[i][i1]=0;
	}
	for(i=0;i<cesit;i++){
		matris[i][2]=i+1;
	}

	
	
	for(i=0;i<cesit;i++){
		printf("%d. esyanin agirligi::::\t", i+1); scanf("%f", &agirlik);
		matris[i][0]=agirlik*10;
		printf("%d. esyanin degeri::::::\t", i+1); scanf("%d", &matris[i][1]);
		for(i1=0;i1<i;i1++){
			if(matris[i][0]<10){
			if(matris[i][1]/(matris[i][0])>matris[i1][1]/(matris[i1][0])){
				temp=matris[i][0];
				temp1=matris[i][1];
				temp2=matris[i][2];
				matris[i][0]=matris[i1][0];
				matris[i][1]=matris[i1][1];
				matris[i][2]=matris[i1][2];
				matris[i1][0]=temp;
				matris[i1][1]=temp1;
				matris[i1][2]=temp2;
			}
		}
			else
			if(matris[i][1]/(matris[i][0]/10)>matris[i1][1]/(matris[i1][0]/10)){
				temp=matris[i][0];
				temp1=matris[i][1];
				temp2=matris[i][2];
				matris[i][0]=matris[i1][0];
				matris[i][1]=matris[i1][1];
				matris[i][2]=matris[i1][2];
				matris[i1][0]=temp;
				matris[i1][1]=temp1;
				matris[i1][2]=temp2;
			}
		}
	}
		for(i=0;i<cesit;i++){
	for(i1=0;i1<3;i1++)
	printf("%d   ", matris[i][i1]);
	printf("\n");}
	printf("Backpack Size::::\t"); scanf("%f", &backpack1);
	backpack=backpack1*10;
	printf("=========================================================\n");
	printf("=========================================================\n");
	printf("En iyi Urun Listesi:::::::::::::::::::::\n");
	for(i=0;i<cesit;i++){
		if(backpack>=matris[i][0]){
			backpack=backpack-matris[i][0];
			adet=1;
			("%d. Esya Adeti ::::\t\t\t%d\n", matris[i][2], adet);
			matris[i][3]=1;
			total=total+matris[i][1];
			adet=0;
			}
		else{
			("%d. Esya Adeti ::::\t\t\t%d\n", matris[i][2], adet);
		}
		
	}
	for(i=0;i<cesit;i++)
	printf("%d. Esya adeti :::\t\t%d\n", matris[i][2], matris[i][3]);
	printf("=========================================================\n\n");
	printf("TOPLAM FIYAT\t\t =%dTL", total);
	
	
	
	
	
	
	return 0;
}
