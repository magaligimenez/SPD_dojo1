
## Integrantes 
- Jonathan Fernandez
- Santiago Amato
- Joaquin Carnelos Duarte
- Magali Gimenez

## Descripción
1- El semáforo tiene que tener 2 leds de cada color como mínimo, en caso de que uno se  rompa. 
2- Tiene que implementar los tiempos correctos como se detallan a continuación. 3- El verde dura 5 segundos. 
4- El amarillo dura 3 segundos. 
5- Rojo dura 5 segundos. 
6- Tiene que tener señalización para personas no videntes como se detalla a  continuación. (Buzzer o piezo)
7- Durante el rojo: Tiene que sonar 2 vez por segundo en un tono FUERTE. 

## Función principal:
## definicion de los leds y buzzer
#define LEDROJO1 2
#define LEDROJO2 3
#define LEDAMARILLO1 4
#define LEDAMARILLO2 5
#define LEDVERDE1 6
#define LEDVERDE2 7
#define PIEZO1 11

## definicion de tiempos
const int TIEMPO_VERDE = 5000;
const int TIEMPO_AMARILLO = 3000;
const int TIEMPO_ROJO = 5000;
const int PIEZO_ENCENDER = 500;
const int PIEZO_APAGAR = 500;

~~~ C (lenguaje en el que esta escrito)
void setup() {
  pinMode(LEDVERDE1, OUTPUT);
  pinMode(LEDVERDE2, OUTPUT);
  pinMode(LEDAMARILLO1, OUTPUT);
  pinMode(LEDAMARILLO2, OUTPUT);
  pinMode(LEDROJO1, OUTPUT);
  pinMode(LEDROJO2, OUTPUT);
  pinMode(PIEZO1, OUTPUT);
}

void loop() {
  faseVerde();
  faseAmarilla();
  faseRoja();
}

//funcion que enciende led depende el tiempo y el pin
void encenderLed(int pin, int pin2, int tiempo) {
  digitalWrite(pin, HIGH);
  digitalWrite(pin2, HIGH);
  delay(tiempo);
}

//funcion que apaga el led depende el tiempo y el pin
void apagarLed(int pin, int pin2, int tiempo) {
  digitalWrite(pin, LOW);
  digitalWrite(pin2, LOW);
  delay(tiempo);
}

//Activar el buzzer en determinado momento
void activarPiezo(int tiempo) {
  for (int i = 0; i < tiempo; i += PIEZO_ENCENDER + PIEZO_APAGAR){
  digitalWrite(PIEZO1, HIGH);
  delay(PIEZO_ENCENDER);
  digitalWrite(PIEZO1, LOW);
  delay(PIEZO_APAGAR);
  }
}

//FASE VERDE
void faseVerde() {
  apagarLed(LEDROJO1, LEDROJO2, 0);
  encenderLed(LEDVERDE1, LEDVERDE2, TIEMPO_VERDE);
  activarPiezo(0);
}

//FASE AMARILLA
void faseAmarilla() {
  apagarLed(LEDVERDE1, LEDVERDE2, 0);
  encenderLed(LEDAMARILLO1, LEDAMARILLO2, TIEMPO_AMARILLO);
  activarPiezo(0);
}

//FASE ROJA
void faseRoja() {
  apagarLed(LEDAMARILLO1, LEDAMARILLO2, 0);
  encenderLed(LEDROJO1, LEDROJO2, 0);
  activarPiezo(TIEMPO_ROJO);
}
~~~

## Link al proyecto:
- [proyecto](https://www.tinkercad.com/things/k3XGrMJ1xpu-cool-bombul/editel?sharecode=YNFJ6pwXGRORs6YUBkpM7HFGpfVLve3ughbAV4BknxM)

