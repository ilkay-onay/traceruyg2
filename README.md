# traceruyg2
Cisco Packet Tracer üzerinde bir şirket ağı kurmak için verilen bilgileri kullanarak, Isparta ve Antalya şehirlerinde bulunan iki ofisi birbirine bağlayacağız. Bu kurulum, belirli adımları takip ederek gerçekleştirilir ve ağdaki cihazların birbirleriyle iletişim kurabilmesi sağlanır.
Ağa Genel Bakış

    Isparta Ofisi:
        PC1 (IP: 192.168.3.10)
        PC2 (IP: 192.168.3.11)
        Switch (Isparta)
        Router (Isparta):
            LAN Interface: 192.168.3.1
            WAN Interface: 10.0.0.1

    Antalya Ofisi:
        PC3 (IP: 192.168.4.10)
        PC4 (IP: 192.168.4.11)
        Switch (Antalya)
        Router (Antalya):
            LAN Interface: 192.168.4.1
            WAN Interface: 10.0.0.2

Adım Adım Kurulum
1. Cihazların Yerleştirilmesi ve Bağlantıların Yapılması

    Isparta Ofisi:
        Router'ı (Isparta) yerleştirin ve WAN interface'ini 10.0.0.1 olarak ayarlayın.
        Switch'i (Isparta) router'a bağlayın.
        PC1 ve PC2'yi switch'e bağlayın ve IP adreslerini sırasıyla 192.168.3.10 ve 192.168.3.11 olarak ayarlayın.

    Antalya Ofisi:
        Router'ı (Antalya) yerleştirin ve WAN interface'ini 10.0.0.2 olarak ayarlayın.
        Switch'i (Antalya) router'a bağlayın.
        PC3 ve PC4'ü switch'e bağlayın ve IP adreslerini sırasıyla 192.168.4.10 ve 192.168.4.11 olarak ayarlayın.

2. IP Adresleri ve Alt Ağ Maskelerini Ayarlama

    Isparta Ofisi:
        Router Isparta:
            GigabitEthernet0/0: 192.168.3.1 /24
            Serial0/0/0: 10.0.0.1 /30
        PC1: IP: 192.168.3.10, Subnet Mask: 255.255.255.0, Default Gateway: 192.168.3.1
        PC2: IP: 192.168.3.11, Subnet Mask: 255.255.255.0, Default Gateway: 192.168.3.1

    Antalya Ofisi:
        Router Antalya:
            GigabitEthernet0/0: 192.168.4.1 /24
            Serial0/0/0: 10.0.0.2 /30
        PC3: IP: 192.168.4.10, Subnet Mask: 255.255.255.0, Default Gateway: 192.168.4.1
        PC4: IP: 192.168.4.11, Subnet Mask: 255.255.255.0, Default Gateway: 192.168.4.1

3. Yönlendirme (Routing) Ayarlarının Yapılması

Isparta Router:

    Static Route Eklenmesi:
        ip route 192.168.4.0 255.255.255.0 10.0.0.2
    Interface Configuration:
        interface GigabitEthernet0/0
        ip address 192.168.3.1 255.255.255.0
        no shutdown
        interface Serial0/0/0
        ip address 10.0.0.1 255.255.255.252
        no shutdown

Antalya Router:

    Static Route Eklenmesi:
        ip route 192.168.3.0 255.255.255.0 10.0.0.1
    Interface Configuration:
        interface GigabitEthernet0/0
        ip address 192.168.4.1 255.255.255.0
        no shutdown
        interface Serial0/0/0
        ip address 10.0.0.2 255.255.255.252
        no shutdown

4. Cihazların Test Edilmesi

    Ping Testleri:
        PC1'den PC3 ve PC4'e ping atarak bağlantıyı test edin.
        PC3'ten PC1 ve PC2'ye ping atarak bağlantıyı test edin.

Bu adımları izleyerek Cisco Packet Tracer'da Isparta ve Antalya ofisleri arasında başarılı bir şekilde bir şirket ağı kurabilirsiniz. Ağdaki cihazların birbirleriyle sorunsuz bir şekilde iletişim kurduğundan emin olmak için tüm bağlantı ve yönlendirme ayarlarının doğru yapıldığını kontrol etmelisiniz.
