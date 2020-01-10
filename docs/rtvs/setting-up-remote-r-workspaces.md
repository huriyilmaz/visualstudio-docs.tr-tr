---
title: R için uzak çalışma alanları
description: Uzak R çalışma alanlarını ayarlama ve Visual Studio 'dan bağlama.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 686f98aaaade035f1632139d255ccff8b37eddf3
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850061"
---
# <a name="set-up-remote-workspaces"></a>Uzak çalışma alanlarını ayarlama

Bu makalede, bir uzak sunucunun SSL ve uygun R hizmeti ile nasıl yapılandırılacağı açıklanmaktadır. Bu, Visual Studio için R Araçları (RTVS) sunucusunun bu sunucudaki uzak çalışma alanına bağlanmasını sağlar.

## <a name="remote-computer-requirements"></a>Uzak bilgisayar gereksinimleri

- Windows 10, Windows Server 2016 veya Windows Server 2012 R2. RTVS Ayrıca gerektirir
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) veya üzeri

## <a name="install-an-ssl-certificate"></a>Bir SSL sertifikası yükleme

RTVS, sunucuda bir SSL sertifikası gerektiren, uzak bir sunucu ile tüm iletişimlerin HTTP üzerinden gerçekleşmesini gerektirir. Güvenilen bir sertifika yetkilisi tarafından imzalanmış bir sertifika (önerilen) veya otomatik olarak imzalanan bir sertifika kullanabilirsiniz. (Otomatik olarak imzalanan bir sertifika, bağlandığında, RTVS uyarıları oluşturulmasına neden olur.) Bunlardan biri ile bilgisayara yüklemeniz ve özel anahtarına erişime izin vermeniz gerekir.

### <a name="obtain-a-trusted-certificate"></a>Güvenilen sertifika alma

Güvenilen bir sertifika, bir sertifika yetkilisi tarafından verilir (bkz. arka plan için [Vikipde sertifika yetkilileri](https://en.wikipedia.org/wiki/Certificate_authority) ). Kamu kimlik kartı alma gibi, güvenilen bir sertifika vermek daha fazla işlem ve olası ücretler içerir, ancak isteğin ve istek sahibinin orijinalliğini doğrular.

Sertifikada olması gereken anahtar alanı, R Server bilgisayarınızın tam etki alanı adıdır. Sertifika yetkilisi, sunucunuzun ait olduğu etki alanı için yeni bir sunucu oluşturma yetkinizin sağlamasını gerektirir.

Daha fazla arka plan için bkz. Vikipde [ortak anahtar sertifikaları](https://en.wikipedia.org/wiki/Public_key_certificate) .

## <a name="install-an-ssl-certificate-on-windows"></a>Windows 'a SSL sertifikası yükler

SSL sertifikası Windows 'a el ile yüklenmelidir. SSL sertifikası yüklemek için aşağıdaki yönergeleri izleyin.

### <a name="obtain-a-self-signed-certificate-windows"></a>Otomatik olarak imzalanan sertifika edinme (Windows)

Güvenilen sertifikanız varsa, bu bölümü atlayın. Güvenilen bir yetkiliyle karşılaştırıldığında, otomatik olarak imzalanan bir sertifika, kendiniz için bir kimlik kartı oluşturmaya benzer. Bu işlem, güvenilen bir yetkiliyle çalışmaktan çok daha basittir, ancak bir saldırgan, imzasız sertifika için kendi sertifikasını değiştirebilir ve istemci ile bu arasındaki tüm trafiği yakalayabilir. Server. Bu nedenle, *otomatik olarak imzalanan sertifika yalnızca sınama senaryolarında, güvenilen bir ağda ve hiçbir koşulda üretimde kullanılmalıdır.*

Bu nedenle, RTVS, otomatik olarak imzalanan bir sertifikayla sunucuya bağlanırken her zaman aşağıdaki uyarıyı yayınlar:

![Otomatik olarak imzalanan sertifika uyarısı iletişim kutusu](media/workspaces-remote-self-signed-certificate-warning.png)

Otomatik olarak imzalanan bir sertifika vermek için:

1. Bir yönetici hesabı kullanarak R Server bilgisayarında oturum açın.
1. Yeni bir yönetici PowerShell komut istemi açın ve aşağıdaki komutu vererek `"remote-machine-name"` sunucu bilgisayarınızın tam etki alanı adıyla değiştirin.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. R Server bilgisayarından önce PowerShell 'i hiç çalıştırmadıysanız, komutları açıkça çalıştırmayı etkinleştirmek için aşağıdaki komutu çalıştırın:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Arka plan için bkz. Vikipte [otomatik olarak imzalanan sertifikalar](https://en.wikipedia.org/wiki/Self-signed_certificate) .

### <a name="install-the-certificate"></a>Sertifikayı yükleme

Sertifikayı uzak bilgisayara yüklemek için bir komut isteminden *Certlm. msc* (Sertifika Yöneticisi) komutunu çalıştırın. **Kişisel** klasöre sağ tıklayın ve **Tüm görevler** > **içeri aktar** komutunu seçin:

![Sertifikayı içeri aktar komutu](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>SSL sertifikasının özel anahtarını okumak için izinler verme

Sertifika içeri aktarıldıktan sonra, aşağıdaki yönergelerde açıklandığı gibi özel anahtarı okumak için `NETWORK SERVICE` hesabına izin verin. `NETWORK_SERVICE`, sunucu bilgisayarına gelen SSL bağlantılarını sonlandıran hizmet olan R Services Broker 'ı çalıştırmak için kullanılan hesaptır.

1. Bir yönetici komut isteminden *Certlm. msc* (Sertifika Yöneticisi) komutunu çalıştırın.
1. **Kişisel** > **sertifikaları**' nı genişletin, sertifikaya sağ tıklayın ve **özel anahtarları Yönet** > **Tüm görevler** ' i seçin.
1. Sertifikaya sağ tıklayın ve **Tüm görevler**altında **özel anahtarları Yönet** komutunu seçin.
1. Görüntülenen iletişim kutusunda **Ekle** ' yi seçin ve hesap adı olarak `NETWORK SERVICE` girin:

    ![Özel anahtarları Yönet iletişim kutusu, NETWORK_SERVICE ekleme](media/workspaces-remote-manage-private-key-dialog.png)

1. İletişim kutularını kapatmak ve değişikliklerinizi uygulamak için iki kez **Tamam ' ı** seçin.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Ubuntu 'da SSL sertifikası kurma

`rtvs-daemon` paketi, yüklemenin bir parçası olarak varsayılan olarak otomatik olarak imzalanan bir sertifika yükler.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Otomatik olarak imzalanan sertifika edinme (Ubuntu)

Otomatik olarak imzalanan sertifika kullanmanın avantajları ve riskleri için bkz. Windows açıklaması. `rtvs-daemon` paketi, yükleme sırasında otomatik olarak imzalanan sertifikayı oluşturur ve yapılandırır. Bunu yalnızca otomatik olarak oluşturulan otomatik olarak imzalanan sertifikayı değiştirmek istediğinizde yapmanız gerekecektir.

Otomatik olarak imzalanan bir sertifika vermek için:

1. Linux makinenizde SSH veya oturum açın.
2. `ssl-cert` paketi 'ni yükler:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Varsayılan otomatik olarak imzalanan SSL sertifikasını oluşturmak için `make-ssl-cert` çalıştırın:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Oluşturulan anahtarı ve ped dosyalarını PFX 'e dönüştürün. Oluşturulan PFX, giriş klasörünüzde olmalıdır:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>RTVS Daemon 'ı yapılandırma

SSL sertifika dosyası yolu (PFX dosyasının yolu) */etc/rtvs/rtvsd.config.JSON*içinde ayarlanmalıdır. `X509CertificateFile` ve `X509CertificatePassword` sırasıyla dosya yolu ve parolayla güncelleştirin.

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

Dosyayı kaydedin ve arka plan programını yeniden başlatın `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Windows 'a R Services 'ı yükler

R kodunu çalıştırmak için, uzak bilgisayarda aşağıdaki gibi bir R yorumlayıcısı yüklü olmalıdır:

1. Aşağıdakilerden birini indirin ve yükleyin:

   - [Microsoft R açık](https://mran.microsoft.com/open/)
   - [Windows için CRAN R](https://cran.r-project.org/bin/windows/base/)

     Her ikisi de aynı işlevselliğe sahiptir, ancak [Intel Math Çekirdek Kitaplığı](https://software.intel.com/intel-mkl)'nın sağladığı ek donanım hızlandırmalı doğrusal algeköşeli kütüphanelerinin Microsoft R açık avantajları.

2. [R Services yükleyicisini](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) çalıştırın ve istendiğinde yeniden başlatın. Yükleyici şunları yapar:

    - *%ProgramFiles%\r araçları 'Nda Visual Studio\1.0\\için* bir klasör oluşturun ve tüm gerekli ikilileri kopyalayın.
    - `RHostBrokerService` ve `RUserProfileService` yükleyip otomatik olarak başlayacak şekilde yapılandırın.
    - `seclogon` hizmetini otomatik olarak başlayacak şekilde yapılandırın.
    - Varsayılan bağlantı noktası 5444 ' deki güvenlik duvarı gelen kurallarına *Microsoft. R. Host. exe* ve *Microsoft. R. Host. Broker. exe* ' yi ekleyin.

R Services, bilgisayar yeniden başlatıldığında otomatik olarak başlatılır:

- **R konak Aracısı hizmeti** , Visual Studio ile r kodunun bilgisayarda çalıştığı işlem ARASıNDAKI tüm HTTPS trafiğini işler.
- **R Kullanıcı profili hizmeti** , Windows Kullanıcı profili oluşturmayı işleyen ayrıcalıklı bir bileşendir. Hizmet, yeni bir Kullanıcı R Server bilgisayarında ilk kez oturum açtığında çağrılır.

Bu hizmetleri hizmetler yönetim konsolunda (*compmgmt. msc*) görebilirsiniz.

## <a name="install-r-services-on-linux"></a>Linux 'ta R Services 'ı yükler

R kodunu çalıştırmak için, uzak bilgisayarda aşağıdaki gibi bir R yorumlayıcısı yüklü olmalıdır:

1. Aşağıdakilerden birini indirin ve yükleyin:

   - [Microsoft R açık](https://mran.microsoft.com/open/)
   - [Windows için CRAN R](https://cran.r-project.org/bin/linux/ubuntu/)

     Her ikisi de aynı işlevselliğe sahiptir, ancak [Intel Math Çekirdek Kitaplığı](https://software.intel.com/intel-mkl)'nın sağladığı ek donanım hızlandırmalı doğrusal algeköşeli kütüphanelerinin Microsoft R açık avantajları.

2. Fiziksel Ubuntu bilgisayarlarını, Azure Ubuntu VM 'Leri, Linux için Windows alt sistemi (WSL) ve Docker Kapsayıcıları ile Azure Container Repository üzerinde çalışan bunlar dahil olmak üzere, [Linux Için uzak R hizmeti](setting-up-remote-r-service-on-linux.md)yönergelerini izleyin.

## <a name="configure-r-services"></a>R hizmetlerini yapılandırma

Uzak bilgisayarda çalışan R Services ile Kullanıcı hesapları oluşturmanız, güvenlik duvarı kuralları ayarlamanız, Azure ağ yapılandırmanız ve SSL sertifikasını yapılandırmanız gerekir.

1. Kullanıcı hesapları: uzak bilgisayara erişen her kullanıcı için hesap oluşturun. Standart (ayrıcalıksız) yerel kullanıcı hesapları oluşturabilir veya R Server bilgisayarınızı etki alanınıza katabilir ve `Users` güvenlik grubuna uygun güvenlik gruplarını ekleyebilirsiniz.

1. Güvenlik duvarı kuralları: `R Host Broker`, varsayılan olarak 5444 numaralı TCP bağlantı noktasını dinler. Bu nedenle, hem gelen hem de giden trafik için etkinleştirilmiş Windows Güvenlik Duvarı kurallarının bulunduğundan emin olun (paket ve benzer senaryolar yüklemek için giden).  R Services yükleyicisi, yerleşik Windows Güvenlik Duvarı için bu kuralları otomatik olarak ayarlar. Bununla birlikte, üçüncü taraf bir güvenlik duvarı kullanıyorsanız, `R Host Broker` için 5444 numaralı bağlantı noktasını el ile açın.

1. Azure yapılandırması: uzak Bilgisayarınız Azure 'da bir sanal makine ise, Windows güvenlik duvarından bağımsız olan Azure ağ iletişimi içindeki gelen trafik için 5444 numaralı bağlantı noktasını açın. Ayrıntılar için bkz. Azure belgelerindeki ağ [güvenlik grubu ile ağ trafiğini filtreleme](/azure/virtual-network/virtual-networks-nsg) .

1. R ana bilgisayar aracısına hangi SSL sertifikasının yükleneceğini söyleyin: sertifikayı bir Intranet sunucusuna yüklüyorsanız, sunucunuzun tam etki alanı adı NetBIOS adıyla aynı olabilir. Bu durumda, varsayılan sertifika yüklü olduğundan yapmanız gereken bir şey yoktur.

    Ancak, sertifikanızı Internet 'e yönelik bir sunucuya (örneğin, bir Azure VM) yüklüyorsanız, Internet 'e yönelik bir sunucunun FQDN 'SI, NetBIOS adı ile hiçbir şekilde aynı olmadığından sunucunuzun tam etki alanı adını (FQDN) kullanın.

    FQDN 'yi kullanmak için, R Services 'ın yüklü olduğu yere gidin (varsayılan olarak,*Visual Studio\1.0 için% program FILES%\R uzak hizmeti* ), bir metin düzenleyicisinde *Microsoft. R. Host. Broker. config. JSON* dosyasını açın ve içeriğini AŞAĞıDAKI ile değiştirerek sunucunuzun FQDN 'sine, ÖRNEĞIN `foo.westus.cloudapp.azure.com`gibi, CN 'yi atayarak:

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

**S. R Server bilgisayarı yanıt vermiyor, ne yapmam gerekir?**

Uzak bilgisayara komut satırından ping işlemi yapmayı deneyin: `ping remote-machine-name`. Ping başarısız olursa, bilgisayarın çalıştığından emin olun.

**S. R etkileşimli penceresi uzak bilgisayarın açık olduğunu, ancak hizmetin neden çalışmadığını belirtir.**

Üç olası neden vardır:

- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) veya üzeri, bilgisayarda yüklü değil.
- `Microsoft.R.Host.Broker` ve `Microsoft.R.Host` güvenlik duvarı kuralları 5444 numaralı bağlantı noktasında hem gelen hem de giden bağlantılar için etkin değildir.
- `CN=<remote-machine-name>` olan bir SSL sertifikası yüklenmedi.

Yukarıdaki değişikliklerden herhangi birini yaptıktan sonra bilgisayarı yeniden başlatın. `RHostBrokerService` ve `RUserProfileService`, Görev Yöneticisi (Hizmetler sekmesi) veya *Services. msc*aracılığıyla çalıştığından emin olun.

**S. r Server 'a bağlanırken neden R etkileşimli penceresi "401 Erişim engellendi" deyin?**

Olası iki neden vardır:

- `NETWORK SERVICE` hesabının, SSL sertifikasının özel anahtarına erişimi olmayabilir. `NETWORK SERVICE` özel anahtara erişim vermek için önceki yönergeleri izleyin.
- `seclogon` hizmetinin çalıştığından emin olun. `seclogon` otomatik olarak başlayacak şekilde yapılandırmak için *Services. msc* kullanın.

**S. r Server 'a bağlanırken R etkileşimli penceresi neden "404 bulunamadı" deyin?**

Bu hata, büyük olasılıkla eksik olan C++ yeniden dağıtılabilir kitaplıklarla kaynaklanıyor. Eksik kitaplık (DLL) ile ilgili bir ileti olup olmadığını görmek için R etkileşimli penceresini denetleyin. Sonra VS 2015 Redistributable 'ın yüklü olduğundan ve R 'nin yüklü olduğundan emin olun.

**S. R etkileşimli penceresinden internet/kaynağa erişemiyorum, ne yapmalıyım?**

`Microsoft.R.Host.Broker` ve `Microsoft.R.Host` Güvenlik Duvarı kurallarının 5444 numaralı bağlantı noktasında giden erişime izin verildiğinden emin olun. Değişiklikleri uyguladıktan sonra bilgisayarı yeniden başlatın.

**Soru-cevap, bu çözümleri gerçekleştirmeye çalıştım ve hala çalışmıyor. Şimdi ne?**

*C:\windows\serviceprofiles\networkservice\appdata\local\temp*konumundaki günlük dosyalarına bakın. Bu klasör, çalıştırılan R Broker hizmetinin her bir örneği için ayrı günlük dosyaları içerir. Hizmet her yeniden başlatıldığında yeni bir günlük dosyası oluşturulur. Neyin yanlış gittiğini öğrenmek için en son günlük dosyasını denetleyin.
