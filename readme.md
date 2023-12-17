# Inteligentny Kurnik

Dopiero początek projektu [TODO](./todo.md)

Inteligentny kurnik to projekt który symuluje dzień i noc. Główne funkcje naszego programu:
- Sterowanie oświetleniem symulującym słońce
- płynne rozświetlanie i gaszenie lamp
- możliwość ustawienia długości doby 
- sygnał sterujący do sterowani drzwiami
  
  ## Lider grupy
    Liderem grupy jest Andrzej Szyler 
  
   Przedstawiony przez nas inteligentny kurnik pracuje w oparciu o 8-bitowy kontroler AVR Atmega328P z 32-kilobajtami pamięci flash.
  Jest obsługiwany przez kod oparty na środowisku Visual Studio Code w języku C.
  
    ![in](./image/ddd.jpg)
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
    -PB0(Reguluje temperature w dzień i noc automatycznie)\

    ## Wejścia anaglowe
   -SW0(Przełącznik otwacia i zamknięcia kurnika)\
   -Regulator temperatury(nie wiem jak było to opisane na płytce w kazdym razie gałka analogowa)(Reguluje temprature na zawołanie)\

    Struktura pliku: tutaj bedzie jakis plik chyba 
