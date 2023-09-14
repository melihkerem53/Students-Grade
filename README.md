# Students-Grade
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>

#define BOYUT 25  //Sınıftaki Öğrenci Sayısı

//dizi[BOYUT] dizisini rasgele karıştırır
void func1(const char* dizi[BOYUT])
{
	srand(time(NULL));
	for (int i = 0; i < BOYUT; i++)
	{
		int j = rand() % (i + 1);

		const char* temp = dizi[i];
		dizi[i] = dizi[j];
		dizi[j] = temp;
	}
}

//Rastegele sayı üretir 0-100 arasında
int func2()
{
	return rand() % 100 + 0;
}

//Hesaplanan puanlara göre sıralamayı yapar
void func3(int dizigenel[BOYUT][15])
{
	for (int i = 0; i < BOYUT; i++)
	{
		for (int j = 0; j < BOYUT; j++)
		{
			if (dizigenel[i][12] > dizigenel[j][12])
			{
				for (int k = 0; k < 15; k++)
				{
					int temp = dizigenel[i][k];
					dizigenel[i][k] = dizigenel[j][k];
					dizigenel[j][k] = temp;
				}
			}
		}
	}
}

int main()
{
	const char* dizi[BOYUT] = { "Mukerrem Cagiran","Yalgin Tunceri","Tayyar Numanoglu","Tayfun Ozkok","Necmettin Erginsoy","Said Karadas","Muhsin Kirac ","Rahmi Yalcin","Kemal Demirbas","Ergun Eronat",
	"Figen Dalkiran","Nihan Atakoli","Misra Yesilkaya","Ulku Oztonga","Guldem Kormukcu","Demet Eksioglu","Ece Sezek","Ipek Erturk","Rahime Kuday","Almila Elciboga","Derin Duygulu","Guner Cetiner",
		"Cilay Agaoglu","Sema Elmastasoglu","Ela Uca" };

	func1(dizi); //isimleri karıştırıyoruz

	int diziboyut[BOYUT];
	for (int i = 0; i < BOYUT; i++)
	{
		diziboyut[i] = strlen(dizi[i]);//çıktının hizalı olması için isimlerin karakter sayısının hesaplıyoruz
	}


	int ODEV1[BOYUT];
	int ODEV2[BOYUT];
	int ODEV3[BOYUT];
	int ODEV4[BOYUT];
	int QUIZ1[BOYUT];
	int QUIZ2[BOYUT];
	int QUIZ3[BOYUT];
	int QUIZ4[BOYUT];
	int MIDTERM[BOYUT];
	int FINAL[BOYUT];

	//Notları rasgele üretiyoruz
	for (int i = 0; i < BOYUT; i++)
	{

		ODEV1[i] = func2();
		ODEV2[i] = func2();
		ODEV3[i] = func2();
		ODEV4[i] = func2();
		QUIZ1[i] = func2();
		QUIZ2[i] = func2();
		QUIZ3[i] = func2();
		QUIZ4[i] = func2();
		MIDTERM[i] = func2();
		FINAL[i] = func2();
	}

	//notlara göre puan hesabı yapıyoruz dizigenelde const char* değerler olduğu için puanı integer bir değer buluyoruz sonra double çevireceğiz
	int PUANILK[BOYUT];
	for (int i = 0; i < BOYUT; i++)
	{
		PUANILK[i] = (ODEV1[i] + ODEV2[i] + ODEV3[i] + ODEV4[i]) * 2 + (QUIZ1[i] + QUIZ2[i] + QUIZ3[i] + QUIZ4[i]) * 3 + MIDTERM[i] * 8 + FINAL[i] * 12;
	}

	const char* HarfNotları[8] = { "AA","BA","BB","CB","CC","DC","DD","FF" };//harf notları

	const char* KaldıGecti[BOYUT][2];
	for (int i = 0; i < BOYUT; i++)
	{

		if (PUANILK[i] >= 3000)
		{
			KaldıGecti[i][0] = HarfNotları[0];
			KaldıGecti[i][1] = "GECTI";
		}

		if (PUANILK[i] < 3000 && PUANILK[i] >= 2800)
		{
			KaldıGecti[i][0] = HarfNotları[1];
			KaldıGecti[i][1] = "GECTI";
		}

		if (PUANILK[i] < 2800 && PUANILK[i] >= 2600)
		{
			KaldıGecti[i][0] = HarfNotları[2];
			KaldıGecti[i][1] = "GECTI";
		}

		if (PUANILK[i] < 2600 && PUANILK[i] >= 2400)
		{
			KaldıGecti[i][0] = HarfNotları[3];
			KaldıGecti[i][1] = "GECTI";
		}

		if (PUANILK[i] < 2400 && PUANILK[i] >= 2120)
		{
			KaldıGecti[i][0] = HarfNotları[4];
			KaldıGecti[i][1] = "GECTI";
		}

       if (PUANILK[i] < 2120 && PUANILK[i] >= 1880)
		{
			KaldıGecti[i][0] = HarfNotları[5];
			KaldıGecti[i][1] = "GECTI";
		}

	   if (PUANILK[i] < 1880 && PUANILK[i] >= 1600)
	   {
		   KaldıGecti[i][0] = HarfNotları[6];
		   KaldıGecti[i][1] = "GECTI";
	   }

	   if ( PUANILK[i] < 1600)
	   {
		   KaldıGecti[i][0] = HarfNotları[7];
		   KaldıGecti[i][1] = "KALDI";
	   }
	}
	
	int dizigenel[BOYUT][15];

	for (int i = 0; i < BOYUT; i++)
	{
		dizigenel[i][0] = (int)dizi[i];
		dizigenel[i][1] = diziboyut[i];
		dizigenel[i][2] = ODEV1[i];//1.ödev
		dizigenel[i][3] = ODEV2[i];//2.ödev
		dizigenel[i][4] = ODEV3[i];//3.ödev
		dizigenel[i][5] = ODEV4[i];//4.ödev
		dizigenel[i][6] = QUIZ1[i];//1.quiz
		dizigenel[i][7] = QUIZ2[i];//2.quiz
		dizigenel[i][8] = QUIZ3[i];//3.quiz
		dizigenel[i][9] = QUIZ4[i];//4.quiz
		dizigenel[i][10] = MIDTERM[i];//Midterm
		dizigenel[i][11] = FINAL[i];//Final
		dizigenel[i][12] = PUANILK[i];//Ortalama*40(double veri giremiyoruz)
		dizigenel[i][13] = (int)KaldıGecti[i][0];
		dizigenel[i][14] = (int)KaldıGecti[i][1];
    }

	func3(dizigenel);//puanlara göre sıralama yapıyoruz

	double PUAN[BOYUT];
	for (int i = 0; i < BOYUT; i++)
	{
		PUAN[i] = (double)dizigenel[i][12] / 40; //puanların gerçek değerini hesaplıyoruz
	}  

	int sayi[BOYUT];
	int OD1U[BOYUT];
	int OD2U[BOYUT];
	int OD3U[BOYUT];
	int OD4U[BOYUT];
	int QUIZ1U[BOYUT];
	int QUIZ2U[BOYUT];
	int QUIZ3U[BOYUT];
	int QUIZ4U[BOYUT];
	int MIDTERMU[BOYUT];
	int FINALU[BOYUT];

	//bütün verilerin karakter uzunluklarını hesaplanır çıktı hizalı olsun diye
	for (int i = 0; i < BOYUT; i++)
	{
		sayi[i] = snprintf(NULL, 0, "%d", i + 1);
		OD1U[i] = snprintf(NULL, 0, "%d", dizigenel[i][2]);
		OD2U[i] = snprintf(NULL, 0, "%d", dizigenel[i][3]);
		OD3U[i] = snprintf(NULL, 0, "%d", dizigenel[i][4]);
		OD4U[i] = snprintf(NULL, 0, "%d", dizigenel[i][5]);
		QUIZ1U[i] = snprintf(NULL, 0, "%d", dizigenel[i][6]);
		QUIZ2U[i] = snprintf(NULL, 0, "%d", dizigenel[i][7]);
		QUIZ3U[i] = snprintf(NULL, 0, "%d", dizigenel[i][8]);
		QUIZ4U[i] = snprintf(NULL, 0, "%d", dizigenel[i][9]);
	  MIDTERMU[i] = snprintf(NULL, 0, "%d", dizigenel[i][10]);
		FINALU[i] = snprintf(NULL, 0, "%d", dizigenel[i][11]);
	}

	//en son bütün veriler sıralı bir şekilde yazdırılır
	printf("\033[33m%*s OGRENCI ADI %*s  OD1  OD2  OD3  OD4  Q1   Q2   Q3   Q4   MT  FINAL    ORT   HARF NOTU  GECTI/KALDI\033[0m\n", 3, "", 8, "");

	for (int i = 0; i < BOYUT; i++)
	{
		if (dizigenel[i][12] > 1600)
		{
			printf("%*s%d) %s %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %.2lf     %s         %s\n", 2 - sayi[i], "", i + 1, dizigenel[i][0], 20 - dizigenel[i][1], "", dizigenel[i][2], 3 - OD1U[i], "",
				dizigenel[i][3], 3 - OD2U[i], "", dizigenel[i][4], 3 - OD3U[i], "", dizigenel[i][5], 3 - OD4U[i], "", dizigenel[i][6], 3 - QUIZ1U[i], "", dizigenel[i][7], 3 - QUIZ2U[i], "",
				dizigenel[i][8], 3 - QUIZ3U[i], "", dizigenel[i][9], 3 - QUIZ4U[i], "", dizigenel[i][10], 3 - MIDTERMU[i], "", dizigenel[i][11], 5 - FINALU[i], "", PUAN[i], dizigenel[i][13], dizigenel[i][14]);
		}

		else
		{
			printf("\033[32m%*s%d) %s %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %d %*s %.2lf     %s         %s\033[0m\n", 2 - sayi[i], "", i + 1, dizigenel[i][0], 20 - dizigenel[i][1], "", dizigenel[i][2], 3 - OD1U[i], "",
				dizigenel[i][3], 3 - OD2U[i], "", dizigenel[i][4], 3 - OD3U[i], "", dizigenel[i][5], 3 - OD4U[i], "", dizigenel[i][6], 3 - QUIZ1U[i], "", dizigenel[i][7], 3 - QUIZ2U[i], "",
				dizigenel[i][8], 3 - QUIZ3U[i], "", dizigenel[i][9], 3 - QUIZ4U[i], "", dizigenel[i][10], 3 - MIDTERMU[i], "", dizigenel[i][11], 5 - FINALU[i], "", PUAN[i], dizigenel[i][13], dizigenel[i][14]);
		}
	}




	return 0;
}
