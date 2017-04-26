# ROBOTSPACE
codigo orientado a desarrollo robotica 

  #include<SoftwareSerial.h>
  SoftwareSerial mySerial(0,1);
  
  int led=13;
  int dato_recibido1;
  void setup(){
    
  Serial.begin(9600); 
  pinMode(4,OUTPUT);// salida dc para led infrarrojo
  pinMode(5,INPUT);
  pinMode(6,OUTPUT); // salida pwm para servomotor
  pinMode(13,OUTPUT);
  
  }
  
  void loop(){
    digitalWrite(4,HIGH);
    delay(100);
    digitalWrite(4,HIGH);
    delay(200);
    
    if(Serial.available()){
      dato_recibido1=Serial.read();//almacena dato recibido  
    }
    
   if(dato_recibido1=='1'){
     
     mySerial.write('1'); //envia informacion al los 2
     //tercer  bluetooh
   }
   else{
     
     int i=0;
        do{
          i=i+30;
          analogWrite(4,i);
          delay(300);
          
          if(Serial.available()){
           dato_recibido1=Serial.read();
              }
        
     }
        while(dato_recibido1!='1');
        
        
         if(dato_recibido1=='1'){
           mySerial.write('i');
           
         }
     
     }
  
  }
