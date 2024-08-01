# Linux Üzerinde Ping İsteklerini Engelleme

Bu depo, Linux sistemlerinde gelen ICMP echo isteklerini (ping) engellemek için scriptler ve talimatlar içerir. Ping isteklerini engellemek, sunucunuzu ağ üzerinde daha az görünür hale getirerek güvenliği artırabilir ve belirli saldırı türlerini engelleyebilir.

## Ping İsteklerini Neden Engellemelisiniz?

Ping isteklerini engellemenin çeşitli faydaları olabilir:

- **Gizlilik:** Sunucunuzun, ağ taramalarıyla aktif sistemleri tespit etmeye çalışanlara karşı gizlenmesini sağlar.
- **Güvenlik:** ICMP'yi kötüye kullanan belirli türde DDoS saldırılarını önlemeye yardımcı olabilir.
- **Kaynak Yönetimi:** Gereksiz trafik ve sunucu yükünü azaltır.

## Ping İsteklerini Engelleme Yöntemleri

Ping isteklerini engellemenin iki ana yolu vardır: geçici ve kalıcı olarak.

### Geçici Yöntem

Ping isteklerini geçici olarak engellemek için (sistem yeniden başlatıldığında sıfırlanacaktır):

```bash
sudo sysctl -w net.ipv4.icmp_echo_ignore_all=1
```

Ping isteklerine yeniden izin vermek için:


```bash
sudo sysctl -w net.ipv4.icmp_echo_ignore_all=0
```

### Kalıcı Yöntem

Ping isteklerini kalıcı olarak engellemek için şu adımları izleyin:

1. /etc/sysctl.conf dosyasını düzenleyin:

```bash
sudo nano /etc/sysctl.conf
```

2. Dosyanın sonuna şu satırı ekleyin:

```bash
net.ipv4.icmp_echo_ignore_all=1
```

3. Değişiklikleri uygulayın:

```bash
sudo sysctl -p
```

### Testler

![image](https://github.com/user-attachments/assets/878f3208-8f4a-4633-841d-b0781910b22b)




## Dikkat Edilmesi Gerekenler

- **Sorun Giderme:** ICMP'yi devre dışı bırakmak, `ping` ve `traceroute` gibi araçların ICMP yanıtlarına ihtiyaç duyması nedeniyle ağ sorunlarını gidermeyi zorlaştırabilir.
- **Ağ İzleme:** Bazı izleme araçları, sunucu kullanılabilirliğini kontrol etmek için ICMP kullanır. ICMP'yi devre dışı bırakmak bu araçların çalışmasını engelleyebilir.
- **Güvenlik:** Ping isteklerini engellemek bir güvenlik katmanı ekler, ancak tek başına güvenlik önlemi olarak yeterli değildir. Her zaman kapsamlı güvenlik uygulamaları gerçekleştirilmelidir.


## Katkıda Bulunma

İyileştirme veya ek özellik önerileriniz varsa, lütfen sorun veya çekme isteği açmaktan çekinmeyin.




