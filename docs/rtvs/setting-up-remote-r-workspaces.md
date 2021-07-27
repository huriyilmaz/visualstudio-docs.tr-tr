---
title: R için uzak çalışma alanları
description: Uzak R çalışma alanlarını ayarlama ve çalışma alanlarından Visual Studio.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 2bd4dd7f18ced67d1b6b1505859131d088709d2e
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114679718"
---
# <a name="set-up-remote-workspaces"></a>Uzak çalışma alanlarını ayarlama

Bu makalede SSL ve uygun bir R hizmeti ile uzak sunucu yapılandırma açıklanmıştır. Bu, Visual Studio için R Araçları (RTVS) sunucusunun uzak çalışma alanına bağlanmasına olanak sağlar.

## <a name="remote-computer-requirements"></a>Uzak bilgisayar gereksinimleri

- Windows 10, Windows Server 2016 veya R2 Windows Server 2012. RTVS ayrıca
- [.NET Framework 4.6.1 veya](https://www.microsoft.com/download/details.aspx?id=49981) daha büyük

## <a name="install-an-ssl-certificate"></a>SSL sertifikası yükleme

RTVS, uzak sunucuyla yapılan tüm iletişimlerin HTTP üzerinden gerçekletir ve bunun için sunucuda SSL sertifikası gerekir. Güvenilen bir sertifika yetkilisi tarafından imzalanmış bir sertifika (önerilir) veya otomatik olarak imzalanan bir sertifika kullanabilirsiniz. (Otomatik olarak imzalanan bir sertifika, bağlıyken RTVS'nin uyarılara neden olur.) Bunlardan herhangi birini kullanarak, bunu bilgisayara yüklemeniz ve özel anahtarına erişime izin vermelisiniz.

### <a name="obtain-a-trusted-certificate"></a>Güvenilen sertifika alma

Güvenilen sertifika bir sertifika yetkilisi tarafından verildi (arka plan için [Wikipedia'da sertifika yetkililerine](https://en.wikipedia.org/wiki/Certificate_authority) bakın). Kamu kimlik kartı alma gibi, güvenilen bir sertifika verme işlemi de daha fazla işlem ve olası ücret gerektirir, ancak isteğin ve istekte bulunduranların orijinalliğini doğrular.

Sertifikada olması gereken anahtar alanı, R sunucusu bilgisayarınızın tam etki alanı adıdır. Sertifika yetkilisi, sunucusunun ait olduğu etki alanı için yeni bir sunucu oluşturma yetkinizin kanıtını gerektirir.

Daha fazla arka plan için [bkz. Wikipedia'da ortak](https://en.wikipedia.org/wiki/Public_key_certificate) anahtar sertifikaları.

## <a name="install-an-ssl-certificate-on-windows"></a>Windows'a SSL sertifikası Windows

SSL sertifikasının sunucuya el ile Windows. SSL sertifikası yüklemek için aşağıdaki yönergeleri izleyin.

### <a name="obtain-a-self-signed-certificate-windows"></a>Otomatik olarak imzalanan sertifika alma (Windows)

Güvenilen sertifikanız varsa bu bölümü atlayabilirsiniz. Güvenilir bir yetkiliden gelen sertifikayla karşılaştırıldığında, otomatik olarak imzalanan bir sertifika, kendiniz için bir kimlik kartı oluşturmaya benzer. Bu işlem elbette güvenilir bir yetkiliyle çalışmadan çok daha basittir, ancak güçlü kimlik doğrulamasına sahip değildir; başka bir ifadeyle saldırgan imzasız sertifika yerine kendi sertifikasını kullanabilir ve istemci ile sunucu arasındaki tüm trafiği yakalar. Bu *nedenle, otomatik olarak imzalanan sertifika yalnızca test senaryoları için, güvenilir* bir ağ üzerinde ve hiçbir zaman üretimde kullanılmadan kullanılmalıdır.

Bu nedenle RTVS otomatik olarak imzalanan bir sertifika ile sunucuya bağlanırken her zaman aşağıdaki uyarıyı verir:

![Otomatik olarak imzalanan sertifika uyarısı iletişim kutusu](media/workspaces-remote-self-signed-certificate-warning.png)

Otomatik olarak imzalanan sertifikayı yapmak için:

1. Yönetici hesabı kullanarak R server bilgisayarda oturum açın.
1. Yeni bir yönetici PowerShell komut istemi açın ve yerine sunucu bilgisayarınızın tam etki alanı `"remote-machine-name"` adını yazın.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Daha önce R server bilgisayarda PowerShell çalıştırmazsanız, komut çalıştırmayı açıkça etkinleştirmek için aşağıdaki komutu çalıştırın:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Arka plan için [bkz. Wikipedia'da otomatik olarak imzalanan](https://en.wikipedia.org/wiki/Self-signed_certificate) sertifikalar.

### <a name="install-the-certificate"></a>Sertifikayı yükleme

Sertifikayı uzak bilgisayara yüklemek için bir komut isteminden *certlm.msc* (sertifika yöneticisi) çalıştırın. Kişisel klasörüne sağ **tıklayın** ve Tüm Görevleri İçeri **Aktar**  >  **komutunu** seçin:

![Sertifikayı içeri aktar komutu](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>SSL sertifikasının özel anahtarını okuma izinleri verin

Sertifika içe aktarıldıktan sonra, hesap `NETWORK SERVICE` izinlerine aşağıdaki yönergelerde açıklandığı gibi özel anahtarı okuma izni verin. `NETWORK_SERVICE` , sunucu bilgisayarına gelen SSL bağlantılarını sonlandıran hizmet olan R Services aracısını çalıştırmak için kullanılan hesaptır.

1. Yönetici *komut isteminden certlm.msc* (Sertifika Yöneticisi) komutunu çalıştırın.
1. Kişisel   >  **Sertifikalar'ı** genişletin, sertifikanıza sağ tıklayın ve Tüm Görevler Özel **Anahtarları**  >  **Yönet'i seçin.**
1. Sertifikaya sağ tıklayın ve Tüm Görevler **altında Özel Anahtarları** Yönet komutunu **seçin.**
1. Görüntülenen iletişim kutusunda Ekle'yi **seçin** ve `NETWORK SERVICE` hesap adı olarak girin:

    ![Özel Anahtarları Yönet iletişim kutusu, NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. İletişim **kutularını kapatın** ve değişikliklerinizi işlemek için Tamam'ı iki kez seçin.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Ubuntu'da SSL sertifikası yükleme

Paket, `rtvs-daemon` yüklemenin bir parçası olarak varsayılan olarak otomatik olarak imzalanan bir sertifika yükleyecek.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Otomatik olarak imzalanan sertifika alma (Ubuntu)

Otomatik olarak imzalanan sertifika kullanmanın avantajları ve riskleri için bkz. Windows bakın. Paket, `rtvs-daemon` yükleme sırasında otomatik olarak imzalanan sertifikayı üretir ve yapılandırıyor. Bunu yalnızca otomatik olarak oluşturulan otomatik olarak imzalanan sertifikayı değiştirmek isterseniz tamamlamanız gerekir.

Otomatik olarak imzalanan bir sertifikayı kendiniz yapmak için:

1. SSH veya Linux makinenize oturum açma.
2. Paketi `ssl-cert` yükleme:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Varsayılan `make-ssl-cert` otomatik olarak imzalanan SSL sertifikasını oluşturmak için çalıştırın:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Oluşturulan anahtarı ve PEM dosyalarını PFX'e dönüştürebilirsiniz. Oluşturulan PFX, giriş klasörünüzde yer aladır:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>RTVS daemon'larını yapılandırma

SSL sertifika dosyası yolu (PFX yolu) üzerinde */etc/rtvs/rtvsd.config.jsayar gerekir.* ve `X509CertificateFile` `X509CertificatePassword` dosyasını sırasıyla dosya yolu ve parola ile güncelleştirin.

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

Dosyayı kaydedin ve daemon'u yeniden `sudo systemctl restart rtvsd` başlatın.

## <a name="install-r-services-on-windows"></a>R hizmetlerini Windows

R kodunu çalıştırmak için uzak bilgisayarda aşağıdaki gibi bir R yorumlayıcı yüklü olmalıdır:

1. Aşağıdakilerden birini indirip yükleyin:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [Windows için CRAN R](https://cran.r-project.org/bin/windows/base/)

     Her ikisi de aynı işlevlere sahip ancak Microsoft R Open, Intel Math Kernel Library sayesinde ek donanım hızlandırmalı doğrusal cebir [kitaplıklarından faydalanır.](https://software.intel.com/intel-mkl)

2. R Hizmetleri [yükleyicisini çalıştırın ve](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) istendiğinde yeniden başlatın. Yükleyici şunları yapar:

    - *%PROGRAMFILES%\Visual Studio için R Araçları\1.0 \\* içinde bir klasör oluşturun ve gerekli tüm ikili dosyaları kopyalayın.
    - Otomatik `RHostBrokerService` olarak başlayacak şekilde yükleyin ve `RUserProfileService` yapılandırabilirsiniz.
    - Hizmeti otomatik `seclogon` olarak başlayacak şekilde yapılandırma.
    - Varsayılan *Microsoft.R.Host.exe* *Microsoft.R.Host.Broker.exe* güvenlik duvarı gelen kurallarına varsayılan bağlantı noktası 5444'te güvenlik duvarı ekleme ve güvenlik duvarı ekleme.

Bilgisayar yeniden başlatıldığında R hizmetleri otomatik olarak başlatılır:

- **R Konak Aracısı Hizmeti,** R kodunun bilgisayarda Visual Studio ve işlem arasındaki tüm HTTPS trafiğini işler.
- **R Kullanıcı Profili Hizmeti,** kullanıcı profili oluşturmayla ilgili Windows bir bileşendir. Yeni bir kullanıcı R sunucusu bilgisayarda ilk kez oturum açtığında hizmet çağrılır.

Bu hizmetleri hizmetler yönetim konsolunda (*compmgmt.msc ) görüyorsunuz.*

## <a name="install-r-services-on-linux"></a>Linux'ta R Services'i yükleme

R kodunu çalıştırmak için uzak bilgisayarda aşağıdaki gibi bir R yorumlayıcı yüklü olmalıdır:

1. Aşağıdakilerden birini indirip yükleyin:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [Windows için CRAN R](https://cran.r-project.org/bin/linux/ubuntu/)

     Her ikisi de aynı işlevlere sahip ancak Microsoft R Open, Intel Math Kernel Library sayesinde ek donanım hızlandırmalı doğrusal cebir [kitaplıklarından faydalanır.](https://software.intel.com/intel-mkl)

2. Fiziksel Ubuntu bilgisayarları, Azure Ubuntu VM'leri, Linux için Windows Alt Sistemi (WSL) ve Azure Container Repository'de çalışanlar da dahil olmak üzere Docker kapsayıcılarını kapsayan Linux için [Uzak R](setting-up-remote-r-service-on-linux.md)Hizmeti yönergelerini izleyin.

## <a name="configure-r-services"></a>R hizmetlerini yapılandırma

Uzak bilgisayarda çalışan R hizmetleriyle kullanıcı hesapları oluşturmanız, güvenlik duvarı kuralları ayarlamanız, Azure ağ iletişimi yapılandırmanız ve SSL sertifikasını yapılandırmanız da gerekir.

1. Kullanıcı hesapları: Uzak bilgisayara erişen her kullanıcı için hesaplar oluşturun. Standart (ayrıcalıklı olmayan) yerel kullanıcı hesapları oluşturabilir veya R sunucusu bilgisayarınızı etki alanınıza ekleyebilir ve güvenlik grubuna uygun güvenlik gruplarını `Users` ekebilirsiniz.

1. Güvenlik duvarı kuralları: Varsayılan olarak, `R Host Broker` TCP bağlantı noktası 5444'te dinler. Bu nedenle, hem gelen Windows giden trafik için etkin güvenlik duvarı kuralları olduğundan emin olun (paketleri ve benzer senaryoları yüklemek için giden gereklidir).  R hizmetleri yükleyicisi, yerleşik güvenlik duvarı için bu kuralları Windows ayarlar. Ancak üçüncü taraf güvenlik duvarı kullanıyorsanız el ile 5444 bağlantı noktasını `R Host Broker` açın.

1. Azure yapılandırması: Uzak bilgisayarınız Azure'da bir sanal makine ise, azure ağı içinde gelen trafik için de 5444 bağlantı noktasını açın. Bu bağlantı noktası, güvenlik duvarının Windows açar. Ayrıntılar için Azure [belgelerinde Ağ güvenlik grubu ile ağ](/azure/virtual-network/virtual-networks-nsg) trafiğini filtreleme'ye bakın.

1. R Ana Bilgisayar Aracısı'nda hangi SSL sertifikasının yüklensin? Sertifikayı bir Intranet sunucusuna yüklüyorsanız, büyük olasılıkla sunucunuza tam etki alanı adı NETBIOS adıyla aynı olur. Bu durumda, yüklenen varsayılan sertifika olduğu için, hiçbir şey yapmak zorunda değildir.

    Ancak sertifikanızı İnternet'e yönelik bir sunucuya (Azure VM gibi) yüklüyorsanız, İnternet'e yönelik sunucunun FQDN'si hiçbir zaman NETBIOS adıyla aynı olduğundan, tam etki alanı adını (FQDN) kullanın.

    FQDN 'yi kullanmak için, R Services 'ın yüklü olduğu yere gidin (varsayılan olarak,*Visual Studio \ 1,0 için uzak hizmet* ), *Microsoft.R.Host.Broker.Config.js* dosyayı bir metin düzenleyicisinde açın ve içeriğini aşağıdaki gibi değiştirerek sunucunuzun FQDN 'sine her şeyi ekleyerek, örneğin `foo.westus.cloudapp.azure.com` :

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Değişiklikleri uygulamak için dosyayı kaydedin ve bilgisayarı yeniden başlatın.

## <a name="troubleshooting"></a>Sorun giderme

**Ç. R Server bilgisayarı yanıt vermiyor, ne yapmam gerekir?**

Uzak bilgisayara komut satırından ping işlemi yapmayı deneyin: `ping remote-machine-name` . Ping başarısız olursa, bilgisayarın çalıştığından emin olun.

**Ç. R etkileşimli penceresi uzak bilgisayarın açık olduğunu, ancak hizmetin neden çalışmadığını belirtir.**

Üç olası neden vardır:

- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) veya üzeri, bilgisayarda yüklü değil.
- `Microsoft.R.Host.Broker` `Microsoft.R.Host` Bağlantı noktası 5444 üzerinde hem gelen hem de giden bağlantılar için güvenlik duvarı kuralları etkinleştirilmemiş.
- Yüklü bir SSL sertifikası `CN=<remote-machine-name>` yüklü değil.

Yukarıdaki değişikliklerden herhangi birini yaptıktan sonra bilgisayarı yeniden başlatın. Bu durumda, `RHostBrokerService` ve ' `RUserProfileService` nin Görev Yöneticisi (Hizmetler sekmesi) veya *Services. msc* aracılığıyla çalıştığından emin olun.

**Ç. R Server 'a bağlanırken R etkileşimli penceresi neden "401 Erişim engellendi" deyin?**

Olası iki neden vardır:

- `NETWORK SERVICE`Hesabın, SSL sertifikasının özel anahtarına erişimi olmayabilir. Özel anahtara erişim izni vermek için önceki yönergeleri izleyin `NETWORK SERVICE` .
- `seclogon`Hizmetin çalıştığından emin olun. Otomatik olarak başlayacak şekilde yapılandırmak için *Services. msc* kullanın `seclogon` .

**Ç. R Server 'a bağlanırken R etkileşimli penceresi neden "404 bulunamadı" deyin?**

Bu hata, büyük olasılıkla eksik Visual C++ yeniden dağıtılabilir kitaplıklar nedeniyle olabilir. Eksik kitaplık (DLL) ile ilgili bir ileti olup olmadığını görmek için R etkileşimli penceresini denetleyin. Sonra VS 2015 Redistributable 'ın yüklü olduğundan ve R 'nin yüklü olduğundan emin olun.

**Ç. R etkileşimli penceresinden internet/kaynağa erişemiyorum, ne yapmam gerekir?**

Güvenlik Duvarı kurallarının `Microsoft.R.Host.Broker` `Microsoft.R.Host` bağlantı noktası 5444 ' de giden erişime izin verildiğinden emin olun. Değişiklikleri uyguladıktan sonra bilgisayarı yeniden başlatın.

**Ç. Tüm bu çözümleri denedim ve hala çalışmıyor. Şimdi ne?**

*c:\ Windows \serviceprofiles\networkservice\appdata\local\temp* konumundaki günlük dosyalarına bakın. Bu klasör, çalıştırılan R Broker hizmetinin her bir örneği için ayrı günlük dosyaları içerir. Hizmet her yeniden başlatıldığında yeni bir günlük dosyası oluşturulur. Neyin yanlış gittiğini öğrenmek için en son günlük dosyasını denetleyin.
