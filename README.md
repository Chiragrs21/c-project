#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
#include<string.h>
#include<windows.h>
#include<time.h>
typedef struct {
	char name[50];
	int train_num;
	int num_of_seats;
}pd;
void reservation(void);							//main reservation function
void viewdetails(void);	//view details of all the trains
void seats(char name[], int, int);
void cancel(void);
void printticket(char name[], int, int, float);	//print ticket 
void specifictrain(int);						//print data related to specific train
float charge(int, int);							//charge automatically w.r.t number of seats and train
void login();
void welcome();
void main()
{
	system("cls");//clear screen is not work clrscr
	printf("\t\t=================================================\n");
	printf("\t\t|                                               |\n");
	printf("\t\t|        -----------------------------          |\n");
	printf("\t\t|           TRAIN TICKET RERS. SYSTEM           |\n");
	printf("\t\t|        -----------------------------          |\n");
	printf("\t\t|                                               |\n");

	printf("\t\t|                                               |\n");
	printf("\t\t|                                               |\n");
	printf("\t\t|              BROUGHT TO YOU BY                |\n");
	printf("\t\t|           |  CODEHACKERS BNMIT  |             |\n");
	printf("\t\t|                                               |\n");
	printf("\t\t=================================================\n\n\n");
	int h = 0, m = 0, s = 10;
	while (1)
	{
		printf("\r\t\t\t\t%2d : %2d: %2d", h, m, s);
		s--;
		Sleep(1000);
		if (s == 0)
		{
			break;
		}
	}
	system("cls");
	login();
	int menu_choice,menu_choice1,choice_return;
	system("cls");
	start1:
	printf("\n=================================\n");
	printf("    TRAIN RESERVATION SYSTEM");
	printf("\n=================================");
	printf("\n1>> Reserve A Ticket");
	printf("\n------------------------");
	printf("\n2>> View All Available Trains");
	printf("\n------------------------");
	printf("\n3>> Exit");
	printf("\n------------------------");
	printf("\n\n-->");
	scanf("%d", &menu_choice);
	switch (menu_choice)
	{
	case 1:
		reservation();		//Fucntion still not added
		break;
	case 2:
		viewdetails();
		printf("\n\nPress any key to go to Main Menu..");
		_getch();
		break;
	case 3:
		return(0);
	default:
		printf("\nInvalid choice");
	}
	if (menu_choice == 2)
	{
		system("cls");
		goto start1;
	}
	else
	{
	start:
		system("cls");
		printf("\n=================================\n");
		printf("    TRAIN RESERVATION SYSTEM");
		printf("\n=================================");
		printf("\n1>> Reserve A Ticket");
		printf("\n------------------------");
		printf("\n2>> View All Available Trains");
		printf("\n------------------------");
		printf("\n3>> Cancel Reservation");
		printf("\n------------------------");
		printf("\n4>> Exit");
		printf("\n------------------------");
		printf("\n\n-->");
		scanf("%d", &menu_choice1);
		switch (menu_choice1)
		{
		case 1:
			reservation();		//Fucntion still not added
			break;
		case 2:
			viewdetails();
			printf("\n\nPress any key to go to Main Menu..");
			_getch();
			break;
		case 3:
			cancel();
			//function not added. code has been removed due to some errors
			break;
		case 4:
			return(0);
		default:
			printf("\nInvalid choice");
		}
		goto start;
	}
	return(0);
}
/*********************************************VIEWDETAILS()*************************************************/

//The function is yet not completed, need more details to be added!
//timings of the trains are still missing 

void viewdetails(void)
{
	printf("\n =======================       TRAIN TICKET RESERVATION      =======================\n");
	char sta[50];
	printf("\nEnter your station name:");
	scanf("%s", sta);
	printf("\nPRESS ENTER KEY TO CONTINUE>>>>>>>\n");
	_getch();
	system("cls");
	printf("\n =======================       %s RAILWAY STATION      =======================\n", sta);
	printf("------------------------------------------------------------------------------------------------------");
	printf("\nTr.No\tName\t\t\t\tDestinations\t\t\tArriving time\tDeparture Time\n");
	printf("------------------------------------------------------------------------------------------------------");
	printf("\n1001\tRANNI CHENAMMA EXPRESS    \t%s to CHITRADURGA     \t8:30am\t\t9:00am", sta);
	printf("\n1002\tINTERSCITY                \t%s To TUMKURU         \t11:45am\t\t12:50pm", sta);
	printf("\n1003\tJAN SHATHABDI EXPRESS     \t%s To GULBARGA        \t6:00am\t\t8:30am", sta);
	printf("\n1004\tRAJDHANI EXPRESS          \t%s To DAVANGERE       \t10:50am\t\t11:00am", sta);
	printf("\n1005\tKARNATAKA EXPRESS         \t%s To NEW DELHI         \t6:20am\t\t7:00am", sta);
	printf("\n1006\tBAGMATHI EXPRESS	      \t%s To BIRUR JN         \t --\t\t9:30am", sta);
	printf("\n1007\tCHAMUNDI EXPRESS	      \t%s To ARSEKERE JN      \t12:55pm\t\t1:00pm", sta);
	printf("\n1008\tUDYAN EXPRESS	          \t%s To CHENNAI           \t3:15pm\t\t4:00pm", sta);
	printf("\n1009\tBRINDAVANA EXPRESS	\t%s To MUMBAI          \t2:30pm\t\t3:35pm", sta);
	printf("\n1009\tHAMPI EXPRESS	        \t%s To HYDERABAD         \t4:10pm\t\t4:15pm", sta);
}

/*********************************************RESERVATION()*************************************************/

void reservation(void)
{
	char confirm;
	int i = 0;
	char str[50] = { "BOOKING........" };
	float charges;
	pd passdetails;
	FILE* fp;
	fp = fopen("seats_reserved.txt", "a");
	system("cls");
	printf("\n =======================       TRAIN TICKET RESERVATION      =======================\n");
	printf("\n\t\t\tENTER COUSTOMER NAME: ");
	scanf("%s", &passdetails.name);
	fflush(stdin);
	printf("\n\t\t\tENTER QUANTITY: ");
	scanf("%d", &passdetails.num_of_seats);
	_getch();
	system("cls");
	viewdetails();
	printf("\n\nTRAIN NUMBER:>   ");
start1:
	scanf("%d", &passdetails.train_num);
	if (passdetails.train_num >= 1001 && passdetails.train_num <= 1010)
	{

		if (passdetails.train_num == 1001)
		{
			char x[50] = { "RANNI CHENNAMMA" };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1002)
		{
			char x[50] = { "INTERSCITY " };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1003)
		{
			char x[50] = { "JAN SHATHABDI EXPRESS " };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1004)
		{
			char x[50] = { "RAJDHANI EXPRESS" };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1005)
		{
			char x[50] = { "KARNATAKA EXPRESS" };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1006)
		{
			char x[50] = { "BAGMATHI EXPRESS" };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1007)
		{
			char x[50] = { "CHAMUNDI EXPRESS" };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1008)
		{
			char x[50] = { "UDYAN EXPRESS" };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1009)
		{
			char x[50] = { "BRINDAVANA EXPRESS" };
			calc(passdetails.train_num, x);
		}
		else if (passdetails.train_num == 1010)
		{
			char x[50] = { "HAMPI EXPRESS" };
			calc(passdetails.train_num, x);
		}
		charges = charge(passdetails.train_num, passdetails.num_of_seats);
		printticket(passdetails.name, passdetails.num_of_seats, passdetails.train_num, charges);
	}
	else
	{
		printf("\nInvalid train Number!\n\nEnter again--> ");
		goto start1;
	}
	printf("\n\nConfirm Ticket (Y/N):>");
start:
	scanf(" %c", &confirm);
	if (confirm == 'Y')
	{
		char str[50] = { "B O O K I N G ......." };
		printf("\n\n\t\t\t\t");
		fprintf(fp, "%s\t\t%d\t\t%d\t\t%.2f\n", &passdetails.name, passdetails.num_of_seats, passdetails.train_num, charges);
		for (int i = 0; i < strlen(str) - 1; i++)
		{
			printf("%c", str[i]);
			Sleep(250);
		}
		printf("\n\nReservation Done\n");
		printf("=========================\n\n");
		int h = 0, m = 0, s = 5;
		while (1)
		{
			printf("\r\t\t\t\t%2d : %2d: %2d", h, m, s);
			s--;
			Sleep(1000);
			if (s == 0)
			{
				break;
			}
		}
	}
	else
	{
		if (confirm == 'N') {
			printf("\nReservation Not Done!\nPress any key to go back to  Main menu!");
		}
		else
		{
			printf("\nInvalid choice entered! Enter again-----> ");
			goto start;
		}
	}
	fclose(fp);

}
/*********************************************calculation*********************************************/
int calc(int t, char* y)
{
	char a[50] = { "2S" };
	char b[50] = { "SL" };
	char c[50] = { "3A" };
	char d[50];
	int r = 250.0, s = 360.0, f = 900, i, x;
	printf("\n\tTRAIN NUMBER:%d\n", t);
	printf("\n\tTRAIN NAME:%s\n", y);
	printf("\n\tSEATS>>>>>>    \t2S         \tSL         \t3A\n");
	printf("\n\tCHARGE>>>>>    \t$250       \t$360       \t$900\n");
	printf("\n\tENTER YOUR SEAT\n\t");
	scanf("%s", d);
	i = strcmp(d, a);
	x = strcmp(d, b);
	if (i == 0)
	{
		return r;
	}
	else if (x == 0)
	{
		return s;
	}
	else
	{
		return f;
	}
}
/*********************************************seats()**************************************************/
/*********************************************CHARGE()*************************************************/

float charge(int train_num, int num_of_seats)
{
	if (train_num == 1001)
	{
		return(366.25 * num_of_seats);
	}
	if (train_num == 1002)
	{
		return(450.0 * num_of_seats);
	}
	if (train_num == 1003)
	{
		return(420.69 * num_of_seats);
	}
	if (train_num == 1004)
	{
		return(595.85 * num_of_seats);
	}
	if (train_num == 1005)
	{
		return(4265.0 * num_of_seats);
	}
	if (train_num == 1006)
	{
		return(400.0 * num_of_seats);
	}
	if (train_num == 1007)
	{
		return(350.0 * num_of_seats);
	}
	if (train_num == 1008)
	{
		return(3500.0 * num_of_seats);
	}
	if (train_num == 1009)
	{
		return(2500.0 * num_of_seats);
	}
	if (train_num == 1010)
	{
		return(600.0 * num_of_seats);
	}
}


/*********************************************PRINTTICKET()*************************************************/

void printticket(char name[], int num_of_seats, int train_num, float charges)
{
	system("cls");
	printf("-------------------\n");
	printf("\tTICKET\n");
	printf("-------------------\n\n");
	printf("Name:\t\t\t%s", name);
	printf("\nNumber Of Seats:\t%d", num_of_seats);
	printf("\nTrain Number:\t\t%d", train_num);
	time_t t = time(NULL);
	printf("\nDate and time:\t\t%s",ctime(&t));
	specifictrain(train_num);
	printf("\nCharges:\t\t%.2f", charges);
}

/*********************************************SPECIFICTRAIN()*************************************************/

void specifictrain(int train_num)
{

	if (train_num == 1001)
	{
		printf("Train:\t\t\tRANNI CHENAMMA EXPRESS");
		printf("\nDestination:\t\tTo CHITRADURGA");
		printf("\nDeparture:\t\t9am ");
	}
	if (train_num == 1002)
	{
		printf("Train:\t\t\tINTERSCITY");
		printf("\nDestination:\t\tTO TUMKURU");
		printf("\nDeparture:\t\t12:50pm");
	}
	if (train_num == 1003)
	{
		printf("Train:\t\t\tJAN SHATHABDI EXPRESS");
		printf("\nDestination:\t\tTO GULBARGA");
		printf("\nDeparture:\t\t8:30am");
	}
	if (train_num == 1004)
	{
		printf("Train:\t\t\tRAJDHANI EXPRESS");
		printf("\nDestination:\t\tTO DAVANGERE");
		printf("\nDeparture:\t\t11:00am ");
	}
	if (train_num == 1005)
	{
		printf("Train:\t\t\KARNATAKA EXPRESS");
		printf("\nDestination:\t\tTO NEW DELHI");
		printf("\nDeparture:\t\t7:00am");
	}
	if (train_num == 1006)
	{
		printf("train:\t\t\tBAGMATHI EXPRESS");
		printf("\nDestination:\t\tTO BIRUR JN");
		printf("\nDeparture:\t\t9:30am ");
	}
	if (train_num == 1007)
	{
		printf("train:\t\t\tCHAMUNDI EXPRESS");
		printf("\nDestination:\t\tTO ARSEKERE JN");
		printf("\nDeparture:\t\t1:00pm ");
	}
	if (train_num == 1008)
	{
		printf("train:\t\t\tUDYAN EXPRESS");
		printf("\n Destination:\t\tTO CHENNAI");
		printf("\nDeparture:\t\t4:00pm ");
	}
	if (train_num == 1009)
	{
		printf("train:\t\t\tBRINDAVANA EXPRESS");
		printf("\nDestination:\t\tTO MUMBAI");
		printf("\nDeparture:\t\t3:35pm ");
	}
	if (train_num == 1010)
	{
		printf("train:\t\t\tHAMPI EXPRESS");
		printf("\nDestination:\t\tTO HYDERABAD");
		printf("\nDeparture:\t\t1:15 ");
	}
}

void login()
{
	int a = 0, i = 0;
	char uname[50], c = ' ';
	char pword[10], code[10];
	char user[10];
	char pass[10];
	int dob;
	int m;
	//REGISTRATION FORM
strat:
	{
		printf("\n=======================  REGISTRATION FORM  =======================\n");
		printf(" \n                     ENTER USERNAME:-");
		scanf("%s", &user);
		printf(" \n                     ENTER YOUR AGE:-");
		scanf("%d", &dob);
		printf(" \n                     ENTER MOBILE NUMBER:-");
		scanf("%d", &m);
		printf(" \n                     CREATE YOUR PASSWORD:-");
		i = 0;
		while (i < 10)
		{
			pass[i] = _getch();
			c = pass[i];
			if (c == 13)
				break;
			else
				printf("*");
			i++;
		}
		pass[i] = '\0';
		printf("\n");
		printf("\n                   REGISTRATION SUCCESSFULL                      \n\n");
		printf("\n=======================       THANK YOU       =======================\n");
		_getch();
		welcome();
	}
	do
	{
		system("cls");
		printf("\n\=======================  LOGIN FORM  =======================\n  ");
		printf(" \n                   ENTER USERNAME:-");
		scanf("%s", &uname);
		printf(" \n                   ENTER PASSWORD:-");
		i = 0;
		while (i < 10)
		{
			pword[i] = _getch();
			c = pword[i];
			if (c == 13)
				break;
			else
				printf("*");
			i++;
		}
		pword[i] = '\0';
		//char code=pword;
		//scanf("%s",&pword); 
		if (strcmp(uname, user) == 0 && strcmp(pword, pass) == 0)
		{
			printf("  \n\n\n       WELCOME TO OUR SYSTEM !! YOUR LOGIN IS SUCCESSFUL\n\n");
			int h = 0, m = 0, s = 5;
			while (1)
			{
				printf("\r\t\t\t\t%2d : %2d: %2d", h, m, s);
				s--;
				Sleep(1000);
				if (s == 0)
				{
					break;
				}
			}
			break;
		}
		else
		{
			printf("\n\n       SORRY !!!!  LOGIN IS UNSUCESSFUL\n");
			printf("\n         TRY AGAIN!!!                    \n");
			a++;
			_getch();//holds the screen
			system("cls");
		}
	}
	while (a <= 1);
	if (a > 1)
	{
		printf("\nSorry you have entered the wrong username and password for three times!!!\n\n");
		printf("\n\n\t\t\tRESET YOUR PASSWORD:");
		goto strat;
		_getch();
	}
	system("cls");
}
void cancel(void)
{
	system("cls");
	printf("\n =======================       TRAIN TICKET RESERVATION      =======================\n");
	int trainnum;
	printf("-----------------------\n");
	printf("Enter the train number: \n");
	printf("-----------------------\n");
	fflush(stdin);
	scanf("%i", &trainnum);
	if (trainnum == 1001)
	{
		char x[100] = { "YOUR SEAT ON TRAIN RANNI CHENNAMMA EXPRESS HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	else if (trainnum == 1002)
	{
		char x[100] = { "YOUR SEAT ON TRAIN INTERCITY HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	else if (trainnum == 1003)
	{
		char x[100] = { "YOUR SEAT ON TRAIN JAN SHATHABDI EXPRESS HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	else if (trainnum == 1004)
	{
		char x[100] = { "YOUR SEAT ON TRAIN RAJDHANI EXPRESS HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	else if (trainnum == 1005)
	{
		char x[100] = { "YOUR SEAT ON TRAIN KARNATAKA EXPRESS HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	else if (trainnum == 1006)
	{
		char x[100] = { "YOUR SEAT ON TRAIN BAGMATHI EXPRESS HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	else if (trainnum == 1007)
	{
		char x[100] = { "YOUR SEAT ON TRAIN CHAMUNDI EXPRESS HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	else if (trainnum == 1008)
	{
		char x[100] = { "YOUR SEAT ON TRAIN UDYAN EXPRESS HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	else if (trainnum == 1009)
	{
		char x[100] = { "YOUR SEAT ON TRAIN BRINDHAVAN EXPRESS HAS BEEN CANCELLED\n" };
		printf("%s", x);
	}
	printf("\n\nCancelled");
	_getch();
}
void welcome(void)
{
	char str[50] = { "W  E  L  C  O  M  E  ..........." };
	char str1[50] = { "T 0" };
	char str2[50] = { "TRAIN TICKET RERS. SYSTEM" };
	system("cls");
	printf("\n\n\n\n\n\n\t\t\t\t");
	for (int i = 0; i < strlen(str) - 1; i++)
	{

		printf("%c", str[i]);
		Sleep(150);
	}
	printf("\n\n\t\t\t\t\t");
	for (int i = 0; i < strlen(str) - 1; i++)
	{

		printf("%c", str1[i]);
		Sleep(10);
	}
	printf("\n\n\t\t\t\t");
	for (int i = 0; i < strlen(str) - 1; i++)
	{

		printf("%c", str2[i]);
		Sleep(150);
	}
	_getch();
	system("cls");
}

