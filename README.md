# otuslinuxproff_hw26

### Vagrant с двумя виртуальными машинами:
  - WEB: с сервером Nginx, настроенным filebeat на слежение за его логами, auditd следящий за конфиг-файлом nginx (просмотр командой ``` sudo auditctl -l)и отправка системных логов через journal-upload  
  
  - LOG: настроен на прием системных journald логов - просмотр командой ``` sudo journalctl -D /var/log/journal/remote ```
         и логов auditd от WEB - просмотр командой: ``` sudo grep web /var/log/audit/audit.log ```
или ``` sudo ausearch -hn web -l ```        
  
### docker-compose файл для запуска ELK-stack (без Logstash )
  -  для представления логов Nginx в графическом виде на локальной машине
    
### Запуск: 
  - ВАЖНО: в файле ``` ansible/group_vars/all.yml ```  измените значение переменной ```elastic_addr``` на ваш адрес в сети (адрес с ELK stack)
  - из директории ``` dc_elk ``` командой ``` docker-compose up -d ``` запустите стэк ELK
  - командой ``` vagrant up ```  запустите создание и настройку виртуальных машин

### Рекомендации:
  - образ машин nvkmv/rockylinux9 vers 2.0 собран с virtualbox-guest-additions 7.0.4, если нужен образ с virtualbox-guest-additions 7.0.6 - измените в vagrantfile версию бокса на "2.1"  
  - для загрузки образа виртуальной машины и установки filebeat нужен VPN 

```screen:```

![Screenshot_20230221_212301](https://user-images.githubusercontent.com/59445051/220955380-26c2b7ac-5862-4a6b-9f01-342a47d03fac.png)



![Screenshot_20230223_190232](https://user-images.githubusercontent.com/59445051/220962655-e0589432-6be9-4242-8542-c0a3afae3a6e.png)

![Screenshot_20230223_203620](https://user-images.githubusercontent.com/59445051/220985973-5c3d9036-bc86-42eb-968e-eb2f2a124877.png)



