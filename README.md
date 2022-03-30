# Настройка VPN подключений Wireguard и IPSec/IKEv2

Выполнили: Завьялова, Казачкова, Ким.

## Wireguard

1. Создаем сервер на DigitalOcean.

![капля](https://user-images.githubusercontent.com/63861460/160569021-f0dba480-9af1-4645-8862-b4f9286701d2.png)

2. Подключаемся к серверу, генерируем пару ключей, которые позже используем в wg0.conf для сервера. 

3. То же самое проделываем для клиента, после чего файлы .conf принимают следующий вид:

![Сервер](https://user-images.githubusercontent.com/63861460/160569915-55ec6d38-95d5-4921-b2f0-3ef01138218c.jpg)

![Клиент](https://user-images.githubusercontent.com/63861460/160569938-a323de8c-0517-475b-a5ae-6731d7d69d67.jpg)

4. При помощи команды `wg show` проверяем подключение (совпадает для клиента и сервера):

![подключение](https://user-images.githubusercontent.com/63861460/160570976-5ff49216-d56d-4c75-bb7e-7439c18965c9.jpg)

5. Смотрим `ifconfig`:

![ifconfig](https://user-images.githubusercontent.com/63861460/160571743-7f5c2a94-c567-45f0-9e48-10c6819b7532.jpg)

6. Проверяем по 2ip:

![2ip](https://user-images.githubusercontent.com/63861460/160572064-0d2086b6-1bff-4365-a937-494a3953f186.jpg)

7. Затем запускаем Wireshark и держим примерно в течение минуты (проверяя рутрекер и инстаграм). 
Результаты работы Wireshark находятся в папке wireshark-tests.

![рутркер](https://user-images.githubusercontent.com/63861460/160572853-47133e7e-64b5-4931-8293-c86a36df0cb0.jpg)

![инста](https://user-images.githubusercontent.com/63861460/160572884-5a1652f6-c53d-4603-b444-f5b87a1008a6.jpg)

## IPSec/IKEv2

1. Также создаем сервер на DigitalOcean.

![капля](https://user-images.githubusercontent.com/63861460/160576702-68860b04-652a-4f5f-9534-ba688364caf8.png)

2. Подключаемся к серверу, используем `wget https://git.io/vpnsetup -qO vpn.sh && sudo sh vpn.sh`.

3. Получаем данные для подключения (ip, username, password).

4. Чтобы подключиться, нам необходим файл vpnclient.p12. Скачиваем его с сервера, используя FileZilla:

![filezilla](https://user-images.githubusercontent.com/63861460/160578471-af6c2cfd-a450-4d2e-b04d-3590bfdc490f.png)

5. Подключаемся с клиента (Windows):

![подключение](https://user-images.githubusercontent.com/63861460/160577719-bbb57b52-2ad1-4eb7-9468-ea1c0ed48cf6.png)

6. Проверяем по 2ip:

![2ip](https://user-images.githubusercontent.com/63861460/160577896-1f5bcf03-780f-49e9-b943-555bd2f4c579.png)

7. Запускаем Wireshark и держим примерно в течение минуты (также проверяя несколько адресов). 
Результаты работы Wireshark находятся в папке wireshark-tests.

![wireshark](https://user-images.githubusercontent.com/63861460/160579102-149d3d26-6f93-4963-a9ea-5482b54134bf.png)

8. `ipconfig`:

![изображение](https://user-images.githubusercontent.com/63861460/160748880-cf4e8f0c-d055-4a4c-b2a2-564792a54a49.png)

