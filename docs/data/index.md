## Data retrieval

Raw data is located at `/media/externalDisk/hlds/`

You can transfer any file from miniTRASGO to your local machine using `scp` from the local terminal, not the mingo one:

    scp <user>@<remote machine>:<remote file> <local directory>
  
  For example:

    scp rpcuser@192.168.3.216:gate/system/devices/RCP01/data/dcData/data/2023-07-13-EffMap.mat ~/


## About the units of the timeStamps
In MATLAB, the date format you provided, 739077.6528125, represents a serial date number. MATLAB uses serial date numbers to represent dates as the number of days since January 0, 0000 (a fictitious date). To convert the serial date number to a readable date, you can use the `datestr` function in MATLAB.


## Data stream


TRB3 ---> ethernet packets ---> Odroid SBC ---> DABC (Data acq backbone core) ---> /media/externalDisk/hlds/ --> hld files

CopyFiles copia los hlds (sólo si hay 2) a
~/gate/system/devices/TRB3/data/daqData/rawData/dat

Unpacker: sólo si hay 2 hlds
Copia a una carpeta temporal y desempaqueta ahi dentro
Se pueden correr varios en paralelo
Extrae a formato matlab las variables de los hlds y las copia a 
~/gate/system/devices/TRB3/data/daqData/rawData/mat
Vuelve a leer la info del disco: a partir de los epoch, coarse, fine times construye los tiempos finales.
También aplica las lookup tables (que incluyen parametros del propio telescopio) para escribir las variables de carga y tiempo en 
~/gate/system/devices/TRB3/data/daqData/varData
una pequeña rutina pasa estas variables a ascii en
~/gate/system/devices/TRB3/data/daqData/asci

script de analisis: ana.sh : cada 5 segundos se ejecuta solo
calcula para cada plano las vars: cargas, posiciones, etc (calibrados) (ver captura)

~/gate/system/devices/mingo01/data/ana$ ls
TT1  TT2  Vars

en tt1 están ordenados por día los archivos matlab con 2 cosos:
  outputvarplane: numero de cuentas detectadas y aceptadas, tiempo de ejecucion, tiempos y cargas calibrados, etc....
  outputvartelescope: eficiencias, por archivo
en tt2 lo mismo para self triger

el ana al final de calcular estas variables, distribuye a todos los dispositivos del sistema

detector control system
lee los valores de presion temp, flow etc, los unpackea, crea los logs y los archivos en formato matlab


--------------------

en ..../bin/ para crear y enviar el pdf:
./createReport.sh
./sendReport.sh
