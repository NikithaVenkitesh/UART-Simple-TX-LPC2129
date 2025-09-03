#include<LPC21XX.H>
void UART0_CONFIG(void);
void UART0_TX(unsigned char);
int main()
{
	PINSEL0=0X5;
	UART0_CONFIG();
	UART0_TX('A');
}
void UART0_CONFIG(void)
{
	U0LCR=0X83;
	U0DLL=97;
	U0DLM=0;
	U0LCR=0X03;
}void UART0_TX(unsigned char dat)
{
	while(((U0LSR>>5)&1)==0);
	U0THR=dat;
}
