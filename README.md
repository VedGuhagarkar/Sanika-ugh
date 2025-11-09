# Sanika-ugh
Cuz sanika ugh


OUTPUT: 
 
#include <reg51.h> 
 
void delay(); 
 
void main() {     while(1) {         P2 = 0xFF;   // All LEDs OFF         delay(); 
        P2 = 0x00;   // All LEDs ON         delay(); 
    } 
} 
 
void delay() { 
    int i, j; 
    for(i = 0; i < 1000; i++) {         for(j = 0; j < 100; j++); 
    } 
} 

Generation of PWM signal for DC Motor control. 
CODE :- 
#include<PIC18F4550.h> 
#define SW1 PORTAbits.RA2 #define SW2 PORTAbits.RA3 void main(void) 
{ 
    ADCON1=0X0F; 
    TRISCbits.TRISC2 =0; 
    TRISAbits.TRISA2 =1; 
    TRISAbits.TRISA3 =1; 
    T2CON = 0X02;     PR2 = 149;     while(1) 
    { 
        if (SW1==0) 
        { 
            CCPR1L=37; 
            CCP1CON=0X1F;             TMR2ON=1;             if (SW2==0)                 break; 
        } 
         if (SW2==0) 
        { 
            CCPR1L=111; 
            CCP1CON=0X3F;             TMR2ON=1;             if (SW1==0)                 break;         } 
    } 
} 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
Interfacing of LCD to PIC 18FXXXX 
CODE :- 
#include<PIC18F4550.h> 
#define RS PORTAbits.RA0 
#define EN PORTAbits.RA1 #define ldata PORTB void delay(); void Sendcommand(unsigned char); void Senddata(unsigned char); 
 
 
void main() { 
ADCON1=0x0F; 
TRISB=0x00; 
TRISA=0x00; 
PORTAbits.RA5=0; 
    Sendcommand(0X38); 
    Sendcommand(0X01); 
    Sendcommand(0X0E); 
    Sendcommand(0X06); 
    Sendcommand(0X84); 
    Senddata('S'); 
    Senddata('P'); 
    Senddata('P'); 
    Senddata('U'); 
    Sendcommand(0XC4); 
    Senddata('W'); 
    Senddata('E'); 
    Senddata('L'); 
    Senddata('C');     Senddata('O'); 
    Senddata('M');     Senddata('E');     while(1); 
} void Sendcommand(unsigned char x) 
{       RS=0;     ldata=x;     EN=1;     delay();     EN=0;     delay(); } void Senddata(unsigned char y) 
{     RS=1;     ldata=y;     EN=1;     delay();     EN=0;     delay(); } void delay() { 
 int i; 
for(i=0;i<=1000;i++); 
} 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
Write a program for interfacing button, LED, relay & buzzer as follows 
CODE :- 
#include<PIC18F4550.h> 
#define Buzzer PORTAbits.RA5 
#define Relay PORTAbits.RA4 
#define switch1 PORTAbits.RA2 
#define switch2 PORTAbits.RA3 
#define LED PORTB  
 
void lefttoright(); void righttoleft(); void delay(); 
 
void main() 
{ 
ADCON1=0X0F;     
TRISB=0x00; 
TRISAbits.RA2=1; TRISAbits.RA1=1; 
 
TRISAbits.RA4=0; 
TRISAbits.RA5=0; 
PORTB=0x00; 
 
while(1) 
{ 
if(switch1==0) { while(1) { 
Buzzer=1; Relay=1; 
lefttoright(); if(switch2==0) break; } } if(switch2==0) { while(1) { 
Buzzer=0; Relay=0; 
righttoleft(); if(switch1==0) break; } 
} 
} } void lefttoright() { 
LED=0x80; 
delay(); 
LED=0x40; 
delay(); 
LED=0x20; 
delay(); 
LED=0x10; 
delay(); 
LED=0x08; 
delay(); 
LED=0x04; 
delay(); 
LED=0x02; 
delay(); 
LED=0x01; 
delay(); 
}   
 
void righttoleft() {     LED=0x01; 
    delay();     LED=0x02; 
    delay();     LED=0x04; 
    delay();     LED=0x08; 
    delay();     LED=0x10; 
    delay();     LED=0x20; 
    delay();     LED=0x40; 
    delay();     LED=0x80; 
    delay(); }  void delay() { unsigned int i; for(i=0;i<=60000;i++); 
} 


OUTPUT: 
 
#include <reg51.h> 
 
void delay(); 
 
void main() { 
    int i; 
    unsigned char a[10] = {0xBF,0x86,0xDB,0xCF,0xE6,0xED,0xFD,0x87,0xFF,0xEF};     P3 = 0x80;   
 
    while(1) { 
        for(i = 0; i < 10; i++) {             P2 = a[i];                delay(); 
        } 
    } 
} 
 
void delay() { 
    int j, k;     for(j = 0; j < 1000; j++) {         for(k = 0; k < 100; k++); 
    } 
} 


#include <reg51.h> 
 
void delay(); 
 
void main() {     unsigned char a[8] = {0x01,0x03,0x02,0x06,0x04,0x0C,0x08,0x09}; 
 
    while(1) { 
        int i; 
        for(i=0; i<8; i++) { 
            P1 = a[i];   // send pattern to Port 1             delay(); 
        } 
    } 
} 
 
void delay() { 
    int i, j; 
    for(i=0; i<1000; i++) {         for(j=0; j<100; j++); 
    } 
} 
