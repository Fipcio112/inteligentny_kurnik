# Inteligentny Kurnik

Dopiero początek projektu ~~[TODO](./todo.md)~~

Inteligentny kurnik to projekt który symuluje dzień i noc. Główne funkcje naszego programu:
- Sterowanie oświetleniem symulującym słońce
- płynne rozświetlanie i gaszenie lamp
- ~~możliwość ustawienia długości doby~~
- sygnał sterujący do sterowani drzwiami
  
  ## Lider grupy
    Liderem grupy jest Andrzej Szyler 
  
   Przedstawiony przez nas inteligentny kurnik pracuje w oparciu o 8-bitowy kontroler AVR Atmega328P z 32-kilobajtami pamięci flash.
  Jest obsługiwany przez kod oparty na środowisku Visual Studio Code w języku C.
  
    ![in](./ATM328p.png)
    ATmega328P

  
    ## Wyjścia i wejścia cyfrowe

    ### Wejścia:
    
    -SCK\
    -MISO\
    -MOSI\
    -CS\
    }(Zegar odmierzający dobę)\
    -PD0 (W połączeniu z diodą LED0 sygnalizuje czy kurnik jest zamknięty bądź otwarty)

    ### Wyjścia
    -PB5-1\
    -LED0\

    ## Wejścia Temperaturowe
    -~~PB0(Reguluje temperature w dzień i noc automatycznie)~~\

    ## Wejścia anaglowe
   -SW0(Przełącznik otwacia i zamknięcia kurnika)\
   -Regulator temperatury(nie wiem jak było to opisane na płytce w kazdym razie gałka analogowa)(Reguluje temprature na zawołanie)\

    ~~Struktura pliku: tutaj bedzie jakis plik chyba~~

    ```c
    #define __AVR_ATmega328P__
    #define F_CPU 16000000
    
    #include <avr/io.h>
    #include <util/delay.h>
    
    int main(void)
    {
      PORT_Init();
      PORT_Start();
      int x = 0;
      DDRD |= (1 << 3);
      DDRB &= ~(1 << 2);
      PORTB |= (1 << 2);
      while (1)
      {
        for (int j = 0; j < 24; j++)
        {
          for (int i = 0; i < 60; i++)
          {
            SEG7_Sign(0, j, false);
            SEG7_Sign(2, i, false);
    
            if (j >= 6 && x != 60 && j < 18)
            {
              x = 2 * i;
              PWM_SetA(x);
              PORTB |= (1 << 5);
            }
            if (j >= 18 && x != 0 && j < 6)
            {
              x = 60 - 2 * i;
              PWM_SetA(x);
              PORTB &= ~(1 << 5);
            }
            _delay_ms(3);
          }
        }
      }
    }
    ```
