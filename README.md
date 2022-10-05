# MQTT-OpenWrt
https://youtu.be/azGaeTgGddo

Soft Factory Reset
firstboot -y && reboot now

opkg update
opkg install mosquitto-ssl
opkg install mosquitto-client-ssl libmosquitto-ssl



/etc/init.d/mosquitto enable
/etc/init.d/mosquitto restart

mosquitto_passwd -c /etc/mosquitto/passwords.txt Thing01

pass  159951

mosquitto.conf 


per_listener_settings true
# Default listener
port 1883
# PSK listener
listener 8884
psk_hint "mqttbroker"
use_identity_as_username true
persistence true
persistence_file mosquitto.db
log_dest file /tmp/mosquitto.log
allow_anonymous false
autosave_interval 30
#log_dest syslog
#log_facility 5
log_type debug
#log_type error
#log_type warning
#log_type notice
#log_type information
password_file /etc/mosquitto/passwords.txt
psk_file /etc/mosquitto/preshared.keys



mosquitto_pub -h 127.0.0.1 -p 1883 -t news -m "Hello I am alive"
