# Installing the lm-sensors Package :
```
$ apt-get install lm-sensors
```
# Geting the HDD temperature :
```
$ modprobe drivetemp
$ echo drivetemp | tee -a /etc/modules
```
# Creating a long-lived access token :

In HA, click your profile at the left and scroll down to Long-Lived Access Tokens. Click Create Token, give it a name and copy the generated character string.

# Creating the sensors script : 
```
$ nano proxomox_cpu_temp.sh
```
```
#!/bin/bash

# Home Assistant Settings
url_base="http://192.168.0.123:8123/api/states"
token="asdfaGDfdsgfcCI6IkpX-dUrka1Eis"

# Server name
srv_name="pve"

# Constants for device info
DEVICE_IDENTIFIERS='["n100_server"]'
DEVICE_NAME="Intel N100"
DEVICE_MANUFACTURER="AC8-N"
DEVICE_MODEL="N100 16 512"


# Function to send data to Home Assistant
send_to_ha() {
  local sensor_name=$1
  local temperature=$2
  local friendly_name=$3
  local icon=$4
  local unique_id=$5

  local url="${url_base}/${sensor_name}"
  local device_info="{\"identifiers\":${DEVICE_IDENTIFIERS},\"name\":\"${DEVICE_NAME}\",\"manufacturer\":\"${DEVICE_MANUFACTURER}\",\"model\":\"${DEVICE_MODEL}\"}"
  local payload="{\"state\":\"${temperature}\",\"attributes\": {\"friendly_name\":\"${friendly_name}\",\"icon\":\"${icon}\",\"state_class\":\"measurement\",\"unit_of_measurement\":\"°C\",\"device_class\":\"temperature\",\"unique_id\":\"${unique_id}\"},\"device\":${device_info}}"
  
  curl -X POST -H "Authorization: Bearer ${token}" -H 'Content-type: application/json' --data "${payload}" "${url}"
}

# Send CPU package temperature
cpu_temp=$(sensors | grep 'Package id 0' | awk '{print $4}' | sed 's/+//;s/°C//')
send_to_ha "sensor.${srv_name}_cpu_temperature" "${cpu_temp}" "CPU Package Temperature" "mdi:cpu-64-bit" "${srv_name}_cpu_temp"
```
```
$ chmod +x proxomox_cpu_temp.sh
```
To check the output of the script, run the following command:
```
$ /root/proxomox_cpu_temp.sh
```
# Creating a automated cronjob
```
$ crontab -e
```
The following code will make the script run once per minute
```
$ */1 * * * * /root/ha_post_temp.sh
```
```
$ systemctl restart cron.service
$ systemctl status cron.service
```
The sensors are automatically added to Home Assistant without any additional steps.
