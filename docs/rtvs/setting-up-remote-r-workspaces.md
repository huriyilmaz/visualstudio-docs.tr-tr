---
title: R için uzak çalışma alanları
description: Uzaktan R çalışma alanları nasıl ayarlanacak ve Visual Studio'dan ona bağlanma.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 686f98aaaade035f1632139d255ccff8b37eddf3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75850061"
---
# <a name="set-up-remote-workspaces"></a>Uzak çalışma alanlarını ayarlama

Bu makalede, uzak bir sunucunun SSL ve uygun bir R hizmetiyle nasıl yapılandırılacak ıldığı açıklanmaktadır. Bu, Visual Studio için R Tools'un (RTVS) bu sunucudaki uzak bir çalışma alanına bağlanmasını sağlar.

## <a name="remote-computer-requirements"></a>Uzak bilgisayar gereksinimleri

- Windows 10, Windows Server 2016 veya Windows Server 2012 R2. RTVS de gerektirir
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) veya üzeri

## <a name="install-an-ssl-certificate"></a>SSL sertifikası yükleme

RTVS, uzak bir sunucuyla yapılan tüm iletişimin HTTP üzerinden gerçekleşmesini gerektirir ve bu da sunucuda Bir SSL sertifikası gerektirir. Güvenilir bir sertifika yetkilisi (önerilir) tarafından imzalanmış bir sertifika veya kendi imzalı bir sertifika kullanabilirsiniz. (Kendi imzalı bir sertifika, RTVS'nin bağlandığında uyarı lar yayınlamasına neden olur.) Her ikisiyle de, bilgisayara yüklemeniz ve özel anahtarına erişmenize izin vermeniz gerekir.

### <a name="obtain-a-trusted-certificate"></a>Güvenilir bir sertifika alma

Güvenilir bir sertifika bir sertifika yetkilisi tarafından verilir (arka plan için [Vikipedi'deki sertifika yetkililerine](https://en.wikipedia.org/wiki/Certificate_authority) bakın). Bir devlet kimlik kartı almak gibi, güvenilir bir sertifika veren daha fazla işlem ve olası ücretler içerir, ancak istek ve istek doğrulamasını doğrular.

Sertifikada olması gereken temel alan, R sunucu bilgisayarınızın tam nitelikli alan adıdır. Sertifika yetkilisi, sunucunuzun ait olduğu etki alanı için yeni bir sunucu oluşturma yetkisine sahip olduğunuza dair kanıt gerektirir.

Daha fazla arka plan için Vikipedi'deki [ortak anahtar sertifikalarına](https://en.wikipedia.org/wiki/Public_key_certificate) bakın.

## <a name="install-an-ssl-certificate-on-windows"></a>Windows'a SSL sertifikası yükleme

SSL sertifikasının Windows'a el ile yüklenmesi gerekir. Bir SSL sertifikası yüklemek için aşağıdaki yönergeleri izleyin.

### <a name="obtain-a-self-signed-certificate-windows"></a>Kendi imzalı sertifika (Windows) edinin

Güvenilir bir sertifikanız varsa bu bölümü atlayın. Güvenilir bir yetkilinin sertifikasıyla karşılaştırıldığında, kendi imzalı bir sertifika kendiniz için bir kimlik kartı oluşturmak gibidir. Bu süreç, tabii ki, güvenilir bir makamla çalışmaktan çok daha basittir, ancak aynı zamanda güçlü bir kimlik doğrulaması da yoktur, bu da saldırganın imzasız sertifika için kendi sertifikasını değiştirebileceği ve istemci ile müşteri arasındaki tüm trafiği yakalayabileceği anlamına gelir. Sunucu. Bu nedenle, *kendi imzalı sertifika yalnızca güvenilir bir ağda ve hiçbir zaman üretimde senaryoları sınaması için kullanılmalıdır.*

Bu nedenle, RTVS kendi imzalı sertifikası olan bir sunucuya bağlanırken her zaman aşağıdaki uyarıyı yayınlar:

![Kendi imzalı sertifika uyarı iletişim kutusu](media/workspaces-remote-self-signed-certificate-warning.png)

Kendi imzalı sertifika vermek için:

1. Yönetici hesabını kullanarak R sunucu bilgisayarında oturum açın.
1. Sunucu bilgisayarınızın tam nitelikli etki alanı adı ile `"remote-machine-name"` değiştirerek yeni bir yönetici PowerShell komut istemi açın ve aşağıdaki komutu sorun.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. PowerShell'i daha önce R sunucu bilgisayarında çalıştırmadıysanız, komutların açıkça çalıştırılmasını sağlamak için aşağıdaki komutu çalıştırın:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Arka plan için Vikipedi'de [kendi imzalı sertifikalara](https://en.wikipedia.org/wiki/Self-signed_certificate) bakın.

### <a name="install-the-certificate"></a>Sertifikayı yükleme

Sertifikayı uzak bilgisayara yüklemek için bir komut isteminden *certlm.msc* (sertifika yöneticisi) çalıştırın. **Kişisel** klasöre sağ tıklayın ve **Tüm Görevler** > **Alma** komutunu seçin:

![Alma sertifikası komutu](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>SSL sertifikasının özel anahtarını okumak için izin verme

Sertifika alındıktan sonra, `NETWORK SERVICE` hesap adedini aşağıdaki yönergelerde açıklandığı şekilde okumak için izin ver. `NETWORK_SERVICE`sunucu bilgisayarına gelen SSL bağlantılarını sonlandıran hizmet olan R Services aracısını çalıştırmak için kullanılan hesaptır.

1. Yönetici komut isteminden *certlm.msc'yi* (Sertifika Yöneticisi) çalıştırın.
1. **Kişisel** > **Sertifikaları**genişletin, sertifikanızı sağ tıklatın ve Tüm **Görevleri** > Yönet Özel**Tuşları**seçin.
1. Sertifikaya sağ tıklayın ve **Tüm Görevler**altında Özel **Tuşları Yönet** komutunu seçin.
1. Görünen iletişim **kutusunda, Ekle'yi** seçin `NETWORK SERVICE` ve hesap adı olarak girin:

    ![Özel Anahtarlar iletişim kutusunu yönet, NETWORK_SERVICE ekleme](media/workspaces-remote-manage-private-key-dialog.png)

1. İletişim işllerini kapatmak ve değişikliklerinizi süreyle kaydetmek için Iki defa **Tamam'** ı seçin.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Ubuntu'ya SSL sertifikası yükleme

Paket, `rtvs-daemon` yüklemenin bir parçası olarak varsayılan olarak kendi imzalı bir sertifika yükler.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Kendi imzalı sertifika (Ubuntu) edinin

Kendi imzalı sertifika kullanmanın avantajları ve riskleri için Windows açıklamasına bakın. Paket, `rtvs-daemon` yükleme sırasında kendi imzalı sertifikayı oluşturur ve yapılandırır. Bunu yalnızca otomatik olarak oluşturulan kendi imzalı sertifikayı değiştirmek istiyorsanız yapmanız gerekir.

Kendi imzalı bir sertifikayı kendiniz vermek için:

1. SSH veya Linux makinenize giriş yapın.
2. Paketi `ssl-cert` yükleyin:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Varsayılan `make-ssl-cert` kendi imzalı SSL sertifikasını oluşturmak için çalıştırın:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Oluşturulan anahtar ve PEM dosyalarını PFX'e dönüştürün. Oluşturulan PFX ev klasöründe olmalıdır:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>RTVS daemon yapılandırılması

SSL sertifika dosya yolu (PFX yolu) */etc/rtvs/rtvsd.config.json*olarak ayarlanmalıdır. Dosya `X509CertificateFile` `X509CertificatePassword` yolunu ve parolayı sırasıyla güncelleştirin.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Dosyayı kaydedin ve daemon'u `sudo systemctl restart rtvsd`yeniden başlatın.

## <a name="install-r-services-on-windows"></a>Windows'a R hizmetleri yükleme

R kodunu çalıştırmak için, uzak bilgisayarın aşağıdaki gibi yüklü bir R yorumlayıcısı olması gerekir:

1. Aşağıdakilerden birini indirin ve yükleyin:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [Windows için CRAN R](https://cran.r-project.org/bin/windows/base/)

     Her ikisi de aynı işlevselliğe sahip, ancak Microsoft R Açık ek donanım [Intel Math Kernel Library](https://software.intel.com/intel-mkl)sayesinde doğrusal cebir kütüphaneleri sayesinde hızlandırılmış yararları .

2. R [Hizmetleri yükleyicisini](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) çalıştırın ve istendiğinde yeniden başlatın. Yükleyici aşağıdakileri yapar:

    - *Visual Studio\1.0\\ için %PROGRAMFILES%\R Tools'ta* bir klasör oluşturun ve gerekli tüm ikilileri kopyalayın.
    - Otomatik `RHostBrokerService` `RUserProfileService` olarak başlayacak şekilde yükleyin ve yapılandırın.
    - `seclogon` Hizmeti otomatik olarak başlayacak şekilde yapılandırın.
    - Varsayılan bağlantı noktası 5444'teki güvenlik duvarı gelen kurallarına *Microsoft.R.Host.exe* ve *Microsoft.R.Host.Broker.exe'yi* ekleyin.

Bilgisayar yeniden başlatıldığında R hizmetleri otomatik olarak başlar:

- **R Host Broker Hizmeti,** Visual Studio ile R kodunun bilgisayarda çalıştığı işlem arasındaki tüm HTTPS trafiğini işler.
- **R Kullanıcı Profili Hizmeti,** Windows kullanıcı profili oluşturma işlemlerini sağlayan ayrıcalıklı bir bileşendir. Yeni bir kullanıcı r sunucu bilgisayarında ilk oturum açtığında hizmet çağrılır.

Bu hizmetleri hizmet yönetim konsolunda *(compmgmt.msc)* görebilirsiniz.

## <a name="install-r-services-on-linux"></a>Linux'a R Hizmetleri Yükleme

R kodunu çalıştırmak için, uzak bilgisayarın aşağıdaki gibi yüklü bir R yorumlayıcısı olması gerekir:

1. Aşağıdakilerden birini indirin ve yükleyin:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [Windows için CRAN R](https://cran.r-project.org/bin/linux/ubuntu/)

     Her ikisi de aynı işlevselliğe sahip, ancak Microsoft R Açık ek donanım [Intel Math Kernel Library](https://software.intel.com/intel-mkl)sayesinde doğrusal cebir kütüphaneleri sayesinde hızlandırılmış yararları .

2. Fiziksel Ubuntu bilgisayarları, Azure Ubuntu VM'leri, Linux için Windows Alt Sistemi (WSL) ve Azure Kapsayıcı Deposu'nda çalışanlar da dahil olmak üzere Docker kapsayıcılarını kapsayan [Linux için Uzak R Hizmeti](setting-up-remote-r-service-on-linux.md)yönergelerini izleyin.

## <a name="configure-r-services"></a>R hizmetlerini yapılandırma

Uzak bilgisayarda çalışan R hizmetleriyle, kullanıcı hesapları oluşturmanız, güvenlik duvarı kuralları belirlemeniz, Azure ağlarını yapılandırmanız ve SSL sertifikasını yapılandırmanız gerekir.

1. Kullanıcı hesapları: Uzak bilgisayara erişen her kullanıcı için hesap oluşturun. Standart (ayrıcalıklı olmayan) yerel kullanıcı hesapları oluşturabilir veya R sunucu bilgisayarınızı etki alanınıza katabilir ve `Users` güvenlik grubuna uygun güvenlik gruplarını ekleyebilirsiniz.

1. Güvenlik duvarı kuralları: Varsayılan `R Host Broker` olarak, TCP bağlantı noktası 5444'te dinler. Bu nedenle, hem gelen hem de giden trafik için etkinleştirilen Windows güvenlik duvarı kuralları olduğundan emin olun (paket ve benzeri senaryoları yüklemek için giden gerekli olan giden).  R hizmetleri yükleyici, yerleşik Windows güvenlik duvarı için bu kuralları otomatik olarak ayarlar. Ancak, bir üçüncü taraf güvenlik duvarı kullanıyorsanız, el ile `R Host Broker` açılan bağlantı noktası 5444'ü açın.

1. Azure yapılandırması: Uzak bilgisayarınız Azure'da sanal bir makineyse, Windows güvenlik duvarından bağımsız olan Azure ağı içindeki gelen trafik için 5444 no'yu açın. Ayrıntılar için Azure belgelerinde [ağ güvenliği grubuyla](/azure/virtual-network/virtual-networks-nsg) filtre ağı trafiğine bakın.

1. R Host Broker'a hangi SSL sertifikasını yükleyeceğini söyleyin: Sertifikayı bir Intranet sunucusuna yüklüyorsanız, sunucunuzun tam nitelikli alan adının NETBIOS adı ile aynı olma olasılığı yüksektir. Bu durumda, bu yüklenen varsayılan sertifika olduğundan, yapmanız gereken hiçbir şey yoktur.

    Ancak, sertifikanızı Internet'e bakan bir sunucuya (Azure VM gibi) yüklüyorsanız, Internet'e bakan bir sunucunun FQDN'si hiçbir zaman NETBIOS adı ile aynı olmadığından sunucunuzun tam nitelikli etki alanı adını (FQDN) kullanın.

    FQDN'yi kullanmak için, R Hizmetlerinin yüklendiği yere gidin *(Visual Studio\1.0 için %PROGRAM FILES%\R Remote Service by Visual Studio\1.0),* *Microsoft.R.Host.Broker.Config.json* dosyasını bir metin düzenleyicisinde `foo.westus.cloudapp.azure.com`açın ve içeriğini aşağıdakilerle değiştirin, sunucunuzun FQDN'si ne olursa olsun CN'yi şu şekilde:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Dosyayı kaydedin ve değişiklikleri uygulamak için bilgisayarı yeniden başlatın.

## <a name="troubleshooting"></a>Sorun giderme

**S. R sunucu bilgisayarı yanıt vermiyor, ne yapmalıyım?**

Komut satırından uzak bilgisayarı ping `ping remote-machine-name`deneyin: . Ping başarısız olursa, bilgisayarın çalıştığını unutmayın.

**S. R etkileşimli pencere uzak bilgisayar olduğunu söylüyor, ama neden hizmet çalışmıyor?**

Üç olası nedeni vardır:

- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) veya üzeri bilgisayarda yüklü değildir.
- 5444 `Microsoft.R.Host.Broker` `Microsoft.R.Host` bağlantı noktasındaki hem gelen hem de giden bağlantılar için güvenlik duvarı kuralları ve bunlar etkinleştirilir.
- Yüklü bir SSL sertifikası `CN=<remote-machine-name>` yüklenmedi.

Yukarıdaki değişikliklerden herhangi birini yaptıktan sonra bilgisayarı yeniden başlatın. Sonra emin `RHostBrokerService` olun `RUserProfileService` ve görev yöneticisi (hizmetler sekmesi) veya *services.msc*üzerinden çalışıyor .

**S. R etkileşimli penceresinde r sunucusuna bağlanırken neden "401 Access reddedildi" diyor?**

İki olası nedeni vardır:

- Hesabın SSL `NETWORK SERVICE` sertifikasının özel anahtarına erişimi olmaması büyük olasılıkla. Özel anahtara `NETWORK SERVICE` erişim izni vermek için önceki yönergeleri izleyin.
- Hizmetin `seclogon` çalışmadığından emin olun. Otomatik olarak başlamak `seclogon` için yapılandırmak için *services.msc* kullanın.

**S. R etkileşimli penceresinde r sunucusuna bağlanırken neden "404 bulunamadı" diyor?**

Bu hata büyük olasılıkla Visual C++ yeniden dağıtılabilir kitaplıkların kaybolmasından kaynaklanmaktadır. Eksik kitaplıkla (DLL) ilgili bir ileti olup olmadığını görmek için R etkileşimli penceresini denetleyin. Ardından VS 2015 yeniden dağıtılabilir yüklendiğinden ve R yüklü olup olmadığını kontrol edin.

**S. R etkileşimli pencereden internet/kaynağa erişemiyorum, ne yapmalıyım?**

Güvenlik duvarının 5444 bağlantı noktası için `Microsoft.R.Host.Broker` kurallar alabilmesini ve `Microsoft.R.Host` giden erişime izin verdiğinden emin olun. Değişiklikleri uyguladıktan sonra bilgisayarı yeniden başlatın.

**S. Ben tüm bu çözümleri denedim ve hala çalışmıyor. Şimdi ne oldu?**

*C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp'deki*günlük dosyalarına bakın. Bu klasör, çalıştırılanan R Broker Hizmetinin her örneği için ayrı günlük dosyaları içerir. Hizmet yeniden başlatıldığında yeni bir günlük dosyası oluşturulur. Neyin yanlış olabileceğine dair ipuçları için en son günlük dosyasını denetleyin.
