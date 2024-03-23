# Waggle Plugin for LI-COR SmartFlux System

## Li7500DS
The Li7500DS is a state-of-the-art open path gas analyzer designed by LI-COR Biosciences, specifically engineered for high precision measurements of carbon dioxide (CO2) and water vapor (H2O) concentrations in the atmosphere.

## Usage in Eddy Covariance Measurements
The Li7500DS, along with a sonic anemometer, is used in the eddy covariance system to measure fluxes of CO2 and H2O in the atmosphere. This approach involves calculating the covariance between vertical wind speed (obtained from the sonic anemometer) and the scalars CO2 and H2O concentrations measured by the Li7500DS. The setup allows for direct, real-time monitoring of gas exchange, offering invaluable insights into ecosystem, boundary layer fluxes, carbon, and water cycle in the atmosphere.

## Waggle Plugin for Li7500DS via SmartFlux
The plugin collects data from the LI-COR SmartFlux system over TCP/IP networks, enabling the reading, parsing, and publishing of the data to the Waggle beehive for further analysis and storage. Additionally, the plugin is designed to securely transfer `.ghg` and `.zip` files generated by flux calculations to the beehive. These files containing SmartFlux calculations for analysis of the eddy covariance data.

### File Transfer 
After every flux calculation, the plugin automatically copies the relevant `.ghg` and `.zip` files from the LI-COR SmartFlux device and uploaded to the Waggle beehive.

### SmartFlux Configuration
For seamless data transfer, the SmartFlux device must be configured using the vendor's software. You need to make setup so that the client to receives the `flux status` string over TCP which has file name in it.

### Usage
#### Example Command

```bash
python3 /app/app.py --ip 192.168.1.100 --port 7200 --sensor 'LI7500DS/Gill'
```

- --ip: IP address of the SmartFlux device.
- --port: Port number for TCP/IP connection (default: 7200).
- --sensor: Type of sensor used, defaulting to LI7500DS for specific gas analysis.

With all the options

```bash
python3 /app/app.py --ip 192.168.1.100 --port 7200 --sensor "LI7500DS + Mitek" --interval 1 --user licor --passwd licor --local_dir "/data/" --licor_dir "/home/licor/data/"
```

  -  --ip: SmartFlux device IP.
  -  --port: TCP/IP port, default 7200.
  -  --sensor: Sensor types, e.g., "LI7500DS + Mitek".
  -  --interval: Publishing interval in seconds, default 1.
  -  --user: LI-COR SmartFlux username, default licor.
  -  --passwd: LI-COR SmartFlux password.
  -  --local_dir: Local directory for file storage, /data/.
  -  --licor_dir: SmartFlux device data directory.