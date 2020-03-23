---
title: Sorun giderme ağı veya proxy hataları
description: Güvenlik duvarının veya proxy sunucusunun arkasına Visual Studio yüklediğinizde veya kullandığınızda karşılaşabileceğiniz ağ veya proxy ile ilgili hatalar için çözümler bulun.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0e127006976c484d1e4fc2fe011af979af7eb7a9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114993"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Visual Studio'yu yüklediğinizde veya kullandığınızda ağla ilgili hataları giderme

Visual Studio'yu bir güvenlik duvarının veya proxy sunucusunun arkasına yüklediğinizde veya kullandığınızda karşılaşabileceğiniz en tipik ağ veya proxy ile ilgili hatalar için çözümlerimiz vardır.

## <a name="error-proxy-authorization-required"></a>Hata: "Proxy yetkilendirmegerekli"

Bu hata genellikle kullanıcılar bir proxy sunucusu aracılığıyla internete bağlandığında oluşur ve proxy sunucusu Visual Studio'nun bazı ağ kaynaklarına yaptığı aramaları engeller.

### <a name="to-fix-this-proxy-error"></a>Bu proxy hatasını düzeltmek için

- Visual Studio'yu yeniden başlatın. Proxy kimlik doğrulama iletişim kutusu görünmelidir. İletişim kutusuna istendiğinde kimlik bilgilerinizi girin.

- Visual Studio'yu yeniden başlatmak sorunu çözmüyorsa, proxy sunucunuzun http:&#47;&#47;go.microsoft.com adresleri için kimlik bilgileri istenmemesi, ancak bunu &#42;.visualStudio.microsoft.com adresleri için yapıyor olması olabilir. Bu sunucular için, Visual Studio'daki tüm oturum açma senaryolarının engelini kaldırmak için izin listesine aşağıdaki URL'leri eklemeyi düşünün:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- Aksi takdirde, http:&#47;&#47;go.microsoft.com adresini izin listesinden kaldırabilirsiniz, böylece proxy kimlik doğrulama iletişim kutusu hem http:&#47;&#47;go.microsoft.com adresi hem de Visual Studio yeniden başlatıldığında sunucu bitiş noktaları için gösterir.

  -VEYA-

- Varsayılan kimlik bilgilerinizi proxy'nizle birlikte kullanmak istiyorsanız, aşağıdaki eylemleri gerçekleştirebilirsiniz:

::: moniker range="vs-2017"

  1. **devenv.exe.config** (devenv.exe configuration file) dosyasını bulabilirsiniz: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** veya **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Yapılandırma `<system.net>` dosyasında, bloğu bulun ve sonra bu kodu ekleyin:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Ağınız için doğru proxy adresini 'ye `proxyaddress="<http://<yourproxy:port#>`eklemelisiniz.

     > [!NOTE]
     > Daha fazla bilgi için [ &lt;varsayılan Proxy&gt; Öğesi (Ağ Ayarları)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) ve [ &lt;Proxy&gt; Öğesi (Ağ Ayarları)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) sayfalarına bakın.

::: moniker-end

::: moniker range="vs-2019"

  1. **devenv.exe.config** (devenv.exe configuration file) içinde bulun: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** veya **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. Yapılandırma `<system.net>` dosyasında, bloğu bulun ve sonra bu kodu ekleyin:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Ağınız için doğru proxy adresini 'ye `proxyaddress="<http://<yourproxy:port#>`eklemelisiniz.

     > [!NOTE]
     > Daha fazla bilgi için [ &lt;varsayılan Proxy&gt; Öğesi (Ağ Ayarları)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) ve [ &lt;Proxy&gt; Öğesi (Ağ Ayarları)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) sayfalarına bakın.

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Hata: "Temel bağlantı kapatıldı"

Güvenlik duvarı olan özel bir ağda Visual Studio kullanıyorsanız, Visual Studio bazı ağ kaynaklarına bağlanamayabilir. Bu kaynaklar oturum açma ve lisanslama için Azure DevOps Hizmetlerini, NuGet'i ve Azure hizmetlerini içerebilir. Visual Studio bu kaynaklardan birine bağlanamazsa, aşağıdaki hata iletisini görebilirsiniz:

  **Temel bağlantı kapatıldı: Gönderme'de beklenmeyen bir hata oluştu**

Visual Studio, ağ kaynaklarına bağlanmak için Transport Layer Security (TLS) 1.2 protokolünü kullanır. Bazı özel ağlardaki güvenlik cihazları, Visual Studio TLS 1.2 kullandığında bazı sunucu bağlantılarını engeller.

### <a name="to-fix-this-connection-error"></a>Bu bağlantı hatasını düzeltmek için

Aşağıdaki URL'ler için bağlantıları etkinleştirin:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (Azure bağlantıları için)

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (içerik dağıtım ağı veya CDN, içerik ana bilgisayar)

- &#42;.gallerycdn.vsassets.io (Azure DevOps Hizmetleri uzantılarını barındırıyor)

- static2.sharepointonline.com (Visual Studio'nun Office UI Kumaş kitinde kullandığı yazı tipleri gibi kaynakları barındırıyor)

- &#42;.nuget.org (NuGet bağlantıları için)

  > [!NOTE]
  > Özel sektöre ait NuGet sunucu URL'leri bu listeye dahil olmayabilir. %APPData%\Nuget\NuGet.Config'de kullandığınız NuGet sunucularını kontrol edebilirsiniz.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Hata: "Ana işlemden kimliği ayrıştırmak için başarısız oldu"

Bir Visual Studio bootstrapper ve bir ağ sürücüsü üzerinde bir yanıt.json dosyası kullandığınızda bu hata iletisi karşılaşabilirsiniz. Hatanın kaynağı Windows'daki Kullanıcı Hesabı Denetimi'dir (UAC).

Bu hatanın nedeni şudur: Eşlenmiş bir ağ sürücüsü veya [UNC](/dotnet/standard/io/file-path-formats#unc-paths) paylaşımı, kullanıcının erişim belirteciyle bağlantılıdır. UAC etkinleştirildiğinde, iki kullanıcı [erişim belirteçleri](/windows/win32/secauthz/access-tokens) oluşturulur: biri yönetici *erişimine sahip,* diğeri yönetici erişimi *olmayan.* Bir ağ sürücüsü veya paylaşım oluşturulduğunda, kullanıcının geçerli erişim belirteci ona bağlanır. Bootstrapper yönetici olarak çalıştırılması gerektiğinden, sürücü veya paylaşım yönetici erişimi olan bir kullanıcı erişim belirteci ile bağlantılı değilse ağ sürücüsüne erişemez veya paylaşamaz.

### <a name="to-fix-this-error"></a>Bu hatayı düzeltmek için

Komutu `net use` kullanabilir veya UAC Grup İlkesi ayarını değiştirebilirsiniz. Bu geçici servis ler ve bunların nasıl uygulanacağı hakkında daha fazla bilgi için aşağıdaki Microsoft destek makalelerine bakın:

* [UAC Windows'da "Kimlik bilgileri için komut istemi" olarak yapılandırıldığında, eşlenen sürücüler yükseltilmiş bir komut isteminden kullanılamaz](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Windows işletim sistemlerinde Kullanıcı Hesabı Denetimi'ni açtıktan sonra programlar bazı ağ konumlarına erişemeyebilir](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu bir güvenlik duvarı veya ara sunucusunun arkasına yükleme ve burada kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio yükleme](install-visual-studio.md)
