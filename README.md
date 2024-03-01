# cryptography_19CS412_classical_techni
## CEASER CIPHER:

AIM : 

To implement the simple substitution technique named Caesar cipher using C
language.


ALGORITHM :

Step 1 : 

Read the plain text from the user.

Step 2 :
 Read the key value from the user

Step 3 :

If the key is positive then encrypt the text by adding the key with
each character in the plain text

Step 4 :

Else subtract the key from the plain text.

Step 5 :

Display the cipher text obtained above.


PROGRAM : 

```
#include<stdio.h>
#include <string.h>
#include<conio.h>
#include <ctype.h>
int main()
{
char plain[10], cipher[10];
int key,i,length;
int result;
printf("\n Enter the plain text:");
scanf("%s", plain);
printf("\n Enter the key value:");
scanf("%d", &key);
printf("\n \n \t PLAIN TEXt: %s",plain);
printf("\n \n \t ENCRYPTED TEXT: ");
for(i = 0, length = strlen(plain); i < length; i++)
{
cipher[i]=plain[i] + key;
if (isupper(plain[i]) && (cipher[i] > 'Z'))
cipher[i] = cipher[i] - 26;
if (islower(plain[i]) && (cipher[i] > 'z'))
cipher[i] = cipher[i] - 26;
printf("%c", cipher[i]);
}
printf("\n \n \t AFTER DECRYPTION : ");
for(i=0;i<length;i++)
{
plain[i]=cipher[i]-key;
if(isupper(cipher[i])&&(plain[i]<'A'))
plain[i]=plain[i]+26;
if(islower(cipher[i])&&(plain[i]<'a'))
plain[i]=plain[i]+26;
printf("%c",plain[i]);
}
return 0;
}
```
OUTPUT :

![image](https://github.com/singaravetrivelsenthilkumar/cryptography_19CS412_classical_techni/assets/120572270/09b6c2df-cc34-4939-a26e-cb006cee1a68)



RESULT : 

Thus the implementation of Caesar cipher had been executed successfully















## PLAYFAIR CIPHER: 

AIM :

To write a C program to implement the Playfair Substitution technique.

ALGORITHM :

Step 1 :

Read the plain text from the user

Step 2 :

Read the keyword from the user 

Step 3 :

Arrange the keyword without duplicates in a 5*5 matrix in the row
 
order and fill the remaining cells with missed out letters in

alphabetical order. Note that ‘i’ and ‘j’ takes the same cell. 

Step 4 :

Group the plain text in pairs and match the corresponding corner

letters by forming a rectangular grid.

step 5 :

Display the obtained cipher text

PROGRAM : 

```
#include<stdio.h>
#include<conio.h>
#include<string.h>
#include<ctype.h>
#define MX 5
void playfair(char ch1,char ch2, char key[MX][MX])
{
int i,j,w,x,y,z;
FILE *out;
if((out=fopen("cipher.txt","a+"))==NULL)
{
printf("File Corrupted.");
}
for(i=0;i<MX;i++)
{
for(j=0;j<MX;j++)
{
if(ch1==key[i][j])
{
w=i;
x=j;
}
else if(ch2==key[i][j])
{
y=i;
z=j;
}}}
//printf("%d%d %d%d",w,x,y,z);
if(w==y)
{
x=(x+1)%5;z=(z+1)%5;
printf("%c%c",key[w][x],key[y][z]);
fprintf(out, "%c%c",key[w][x],key[y][z]);
}
else if(x==z)
{
w=(w+1)%5;y=(y+1)%5;
printf("%c%c",key[w][x],key[y][z]);
fprintf(out, "%c%c",key[w][x],key[y][z]);
}
else
{
printf("%c%c",key[w][z],key[y][x]);
fprintf(out, "%c%c",key[w][z],key[y][x]);
}
fclose(out);
}
int main()
{
int i,j,k=0,l,m=0,n;
char key[MX][MX],keyminus[25],keystr[10],str[25]={0};
char
alpa[26]={'A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z'};
printf("\nEnter key:");
gets(keystr);
printf("\nEnter the plain text:");
gets(str);
n=strlen(keystr);
//convert the characters to uppertext
for (i=0; i<n; i++)
{
if(keystr[i]=='j')keystr[i]='i';
else if(keystr[i]=='J')keystr[i]='I';
keystr[i] = toupper(keystr[i]);
}
//convert all the characters of plaintext to uppertext
for (i=0; i<strlen(str); i++)
{
if(str[i]=='j')str[i]='i';
else if(str[i]=='J')str[i]='I';
str[i] = toupper(str[i]);
}
j=0;
for(i=0;i<26;i++)
{
for(k=0;k<n;k++)
{
if(keystr[k]==alpa[i])
break;
else if(alpa[i]=='J')
break;
}
if(k==n)
{
keyminus[j]=alpa[i];j++;
}
}
//construct key keymatrix
k=0;
for(i=0;i<MX;i++)
{
for(j=0;j<MX;j++)
{
if(k<n)
{
key[i][j]=keystr[k];
k++;}
else
{
key[i][j]=keyminus[m];m++;
}
printf("%c ",key[i][j]);
}
printf("\n");
}
printf("\n\nEntered text :%s\nCipher Text :",str);
for(i=0;i<strlen(str);i++)
{
if(str[i]=='J')str[i]='I';
if(str[i+1]=='\0')
playfair(str[i],'X',key);
else
{
if(str[i+1]=='J')str[i+1]='I';
if(str[i]==str[i+1])
playfair(str[i],'X',key);
else
{
playfair(str[i],str[i+1],key);
i++;
}}
}
return 0;
}
```
OUTPUT :

![image](https://github.com/singaravetrivelsenthilkumar/cryptography_19CS412_classical_techni/assets/120572270/168163c8-584d-493c-8fee-e864d6fa0de1)



RESULT :
 Thus the Playfair cipher substitution technique had been implemented successfully.



## HILL CIPHER 

AIM : 

To write a C program to implement the hill cipher substitution techniques.

ALGORITHM :

Step 1 :

Read the plain text and key from the user.

Step 2 :

Split the plain text into groups of length three


Step 3 :

Arrange the keyword in a 3*3 matrix.

Step 4 :

Multiply the two matrices to obtain the cipher text of length three.

Step 5 :

Combine all these groups to get the complete cipher text.


PROGRAM :

```
#include<stdio.h>
#include<conio.h>
#include<string.h>
int main(){
unsigned int a[3][3]={{6,24,1},{13,16,10},{20,17,15}};
unsigned int b[3][3]={{8,5,10},{21,8,21},{21,12,8}};
int i,j, t=0;
unsigned int c[20],d[20];
char msg[20];
printf("Enter plain text: ");
scanf("%s",msg);
for(i=0;i<strlen(msg);i++)
{
c[i]=msg[i]-65;
unsigned int a[3][3]={{6,24,1},{13,16,10},{20,17,15}};
unsigned int b[3][3]={{8,5,10},{21,8,21},{21,12,8}};
printf("%d ",c[i]);
}
for(i=0;i<3;i++)
{ t=0;
for(j=0;j<3;j++)
{
t=t+(a[i][j]*c[j]);
}
d[i]=t%26;
}
printf("\nEncrypted Cipher Text :");
for(i=0;i<3;i++)
printf(" %c",d[i]+65);
for(i=0;i<3;i++)
{
t=0;
for(j=0;j<3;j++)
{
t=t+(b[i][j]*d[j]);
}
c[i]=t%26;
}
printf("\nDecrypted Cipher Text :");
for(i=0;i<3;i++)
printf(" %c",c[i]+65);
getch();
return 0;
}
```

OUTPUT :

![image](https://github.com/singaravetrivelsenthilkumar/cryptography_19CS412_classical_techni/assets/120572270/da80553b-3fe4-419b-938b-977ec56fd226)



RESULT :

 Thus the hill cipher substitution technique had been implemented successfully


## Vigenere Cipher 


AIM : 

To implement the Vigenere Cipher substitution technique using C program


ALGORITHM :

Step 1 :

Arrange the alphabets in row and column of a 26*26 matrix

Step 2 : 

Circulate the alphabets in each row to position left such that the first letter

is attached to last.

Step 3 :

Repeat this process for all 26 rows and construct the final key matrix.

Step 4 :

The keyword and the plain text is read from the user.

Step 5 :

The characters in the keyword are repeated sequentially so as to

match with that of the plain text.

Step  6 :

 Pick the first letter of the plain text and that of the keyword as the row
 
indices and column indices respectively.

Step 7 :

The junction character where these two meet forms the cipher character

Step 8 :

Repeat the above steps to generate the entire cipher text.

PROGRAM :

```
#include <stdio.h>
#include<conio.h>
#include <ctype.h>
#include <string.h>
void encipher();
void decipher();
int main()
{
int choice;
while(1)
{
printf("\n1. Encrypt Text");
printf("\n2. Decrypt Text");
printf("\n3. Exit");
printf("\n\nEnter Your Choice : ");
scanf("%d",&choice);
if(choice == 3)
exit(0);
else if(choice == 1)
encipher();
else if(choice == 2)
decipher();
else
printf("Please Enter Valid Option.");
}
}
void encipher()
{
unsigned int i,j;
char input[50],key[10];
printf("\n\nEnter Plain Text: ");
scanf("%s",input);
printf("\nEnter Key Value: ");
scanf("%s",key);
printf("\nResultant Cipher Text: ");
for(i=0,j=0;i<strlen(input);i++,j++)
{
if(j>=strlen(key))
{ j=0;
}
printf("%c",65+(((toupper(input[i])-65)+(toupper(key[j])-
65))%26));
}}
void decipher()
{
unsigned int i,j;
char input[50],key[10];
int value;
printf("\n\nEnter Cipher Text: ");
scanf("%s",input);
printf("\n\nEnter the key value: ");
scanf("%s",key);
for(i=0,j=0;i<strlen(input);i++,j++)
{
if(j>=strlen(key))
{ j=0; }
value = (toupper(input[i])-64)-(toupper(key[j])-64);
if( value < 0)
{ value = value * -1;
}
printf("%c",65 + (value % 26));
}
return 0;
}
```

OUTPUT :

![image](https://github.com/singaravetrivelsenthilkumar/cryptography_19CS412_classical_techni/assets/120572270/29d52231-8a20-44fc-854d-582af3693e6b)


RESULT :

Thus , The program is executed perfectly and output is verified.


## Rail Fence Cipher

AIM :

To write a C program to implement the rail fence transposition technique.


ALGORRITHM :

Step 1 :

Read the Plain text.


Step 2 :

Arrange the plain text in row columnar matrix format

Step 3 :

Now read the keyword depending on the number of columns of the plain text

Step 4 :

Arrange the characters of the keyword in sorted order and the

corresponding columns of the plain text.

Step 5 :

Read the characters row wise or column wise in the former order to get the

cipher text.

PROGRAM :

```
#include<stdio.h>
#include<conio.h>
#include<string.h>
int main()
{
int i,j,k,l;
char a[20],c[20],d[20];
printf("\n\t\t RAIL FENCE TECHNIQUE");
printf("\n\nEnter the input string : ");
gets(a);
l=strlen(a);
/Ciphering/
for(i=0,j=0;i<l;i++)
{
if(i%2==0)
c[j++]=a[i];
}
for(i=0;i<l;i++)
{
if(i%2==1)
c[j++]=a[i];
}
c[j]='\0';
printf("\nCipher text after applying rail fence :");
printf("\n%s",c);
/Deciphering/
if(l%2==0)
k=l/2;
else
k=(l/2)+1;
for(i=0,j=0;i<k;i++)
{
d[j]=c[i];
j=j+2;
}
for(i=k,j=1;i<l;i++)
{
d[j]=c[i];
j=j+2;
}
d[l]='\0';
printf("\nText after decryption : ");
printf("%s",d);
return 0;
}
```


OUTPUT :

![image](https://github.com/singaravetrivelsenthilkumar/cryptography_19CS412_classical_techni/assets/120572270/63cd3d0a-2060-4282-9af6-d7c1eaf7567f)



RESULT :

Thus the rail fence algorithm had been executed successfully

