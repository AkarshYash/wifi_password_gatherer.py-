# wifi_password_gatherer.py-

import wifi

def get_wifi_passwords():
    networks = wifi.Cell.all('wlan0')

    wifi_passwords = []

    for network in networks:
        if network.ssid and network.key:
            wifi_passwords.append({
                'ssid': network.ssid,
                'password': network.key
            })

    return wifi_passwords

if _name_ == '_main_':
    wifi_passwords = get_wifi_passwords()

    if not wifi_passwords:
        print("No Wi-Fi passwords found.")
    else:
        print("Wi-Fi Passwords:")
        for password in wifi_passwords:
            print(f"SSID: {password['ssid']}, Password: {password['password']}")
