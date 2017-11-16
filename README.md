# Wpa_supplicant_android
Hack for start other istance of wpa_supplicant daemon

# Why?
  because you can start other wpa_supplicant istance with your options and/or with your compiled wpa_supplicant. I used it for some experiment for WIFI WPS WPA TESTER.
 
# How?
!! I'm not responsible about any problems after this little hack !!
I tested it with Oneplus 3.

-killall wpa_supplicant

    #killall wpa_supplicant
    
-change /data/misc/wifi/wpa_supplicant.conf

    from
    
            ctrl_interface=/data/misc/wifi/sockets
            
    to
    
            ctrl_interface=DIR=/data/misc/wifi/sockets GROUP=wifi

-remount /system to read/write

    #mount -o remount,rw /system
    
    
-change name of /system/bin/wpa_supplicant to /system/bin/wpa_supplicant2 ('cause android restart connection after kill)

    #mv /system/bin/wpa_supplicant /system/bin/wpa_supplicant2

-start daemon

    #wpa_supplicant2 -iwlan0 -Dnl80211 -c/data/misc/wifi/wpa_supplicant.conf -ddddddddddddddddd
    

-start wpa_cli with global ctrl_interface

     #wpa_cli -g/data/misc/wifi/sockets/wlan0
     
-enable wlan0

     #ifconfig wlan0 up
     

END. You can connect with wpa_cli


For remove changes and restart all functionatilities of Android Wi-Fi:


-change /data/misc/wifi/wpa_supplicant.conf

    from
    
            ctrl_interface=/data/misc/wifi/sockets  GROUP=wifi
            
    to
    
            ctrl_interface=DIR=/data/misc/wifi/sockets
            
-rename wpa_supplicant

    mv /system/bin/wpa_supplicant2 /system/bin/wpa_supplicant
    
    
reboot device
