# Treść zadania projektowego
Opracować zestaw programów typu producent - konsument realizujących przy wykorzystaniu  
mechanizmu semaforów i pamięci dzielonej, następujący schemat komunikacji międzyprocesowej:  
<pre>
Proces 1: czyta dane (pojedyncze wiersze) ze standardowego strumienia wejściowego 
          lub pliku i przekazuje je w niezmienionej formie do procesu 2.  
Proces 2: pobiera dane przesłane przez proces 1. Oblicza ilość znaków 
          w każdej linii i wyznaczoną liczbę przekazuje do procesu 3.    
Proces 3: pobiera dane wyprodukowane przez proces 2 i umieszcza je w standardowym strumieniu wyjściowym. 
          Każda odebrana jednostka danych powinna zostać wyprowadzona w osobnym wierszu.
 </pre>         
Należy zaproponować i zaimplementować mechanizm informowania się procesów o swoim stanie.  
Należy wykorzystać do tego dostępny mechanizm sygnałów i łączy komunikacyjnych (pipes).  
Scenariusz powiadamiania się procesów o swoim stanie wygląda następująco:  
Do procesu 3 wysyłane są sygnały. Proces 3 przesyła otrzymany sygnał do procesu macierzystego.  
Proces macierzysty zapisuje wartość sygnału do łączy komunikacyjnych oraz wysyła powiadomienie  
do procesu 1 o odczytaniu zawartości łącza komunikacyjnego. Proces 1 po odczytaniu sygnału  
wysyła powiadomienie do procesu 2 o odczytanie łącza komunikacyjnego.  
Proces 2 powiadamia proces 3 o konieczności odczytu łącza komunikacyjnego.  
Wszystkie trzy procesy powinny być powoływane automatycznie z jednego procesu inicjującego.
