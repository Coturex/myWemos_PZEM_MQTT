# WIFI MQTT ENERGY SMARTMETER
 * PZEM : Read Power Consumption/Production   (sample every 4seconds)
 * Dara sent to your Domotic Box, raspberry, PC... using MQTT
 * Publish all PZEM values on MQTT 'Pzem topic' and voltage/power on 'domoticz/in' topic (for Domoticz)
 * Display Power/Voltage/Hz on mini screen    (every 4s)
 * Wired into Rail-DIN box

![photo](https://user-images.githubusercontent.com/53934994/136688865-a3b4bae1-0c27-487a-a898-0a9e817c8b39.png)
![photo](https://user-images.githubusercontent.com/53934994/137083496-70fa6ab4-3972-4f08-b075-35438a764d2d.png)

 * Wifi Access Point WebServer and set custom parameters
 * WebOTA : On The Air firmware update (url http://<pzem_ip>:8080/webota)

![photo](https://user-images.githubusercontent.com/53934994/139536819-df299a4f-86d1-45ee-afe6-58e61d8bed9b.png)

## Hardware requirements:

* PZEM Model : PZEM004T-100A v2.0, PZEM004T-100A v3.0   (v2.0 not yet supported)
   - PZEM-004T-v30         

* ESP Board : Wemos d1 mini (CH341 uart), esp8266
   - SoftSerial Method used on D5 D6 
   - When choosing GPIO pins to use, it's best to avoid GPIO 0, 2 and 15 (D3, D4, D8)

* Oled Shield 64x48 
   - I2C wired on D1-SCL D2-SDA

* AC-DC 5V 700mA-Small

* Plc RailDin Box ~8x37x59mm


## Wiring : 
        | Esp8266|...|PZEM004T-100A                     |    
        |--------|---|----------------------------------|
        | Vcc-5V |---|5V (1)  (violet)   ///      L-230V|
        | D5(TX) |->-|RX (2)  (vert)     ///      N-230V|      
        | D6(RX) |-<-|TX_(3)  (jaune)    ///        Coil|
        | GND    |---|GND (4) (bleu)     ///        Coil|
        

# BE CARREFULL 
# ON AC/dc CONNECTIONS

## FYI : 
some Linux distrib (Ubuntu 20.x) failed on connect Uart CH340/1 while flashing ESP8266

     -> "Timed out waiting for packet header"
fixed in kernels 5.13.14 and maybe upper 
(https://cdn.kernel.org/pub/linux/kernel/v5.x/ChangeLog-5.13.14)

Ubuntu 21.x : even worse

## Todo :
   - fritz schematic
   - Add deprecated  PZEM version v2.0 (I have 2 left)
   - On MQTT Command Msg : change domoticz idx, start AccessPoint, etc...
   - Add OTA, On The Air flash firmware
   - release