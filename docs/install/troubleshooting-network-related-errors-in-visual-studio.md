---
title: Ağ veya proxy hatalarında sorun giderme
description: Bir güvenlik duvarı veya proxy sunucusu arkasında Visual Studio 'Yu yüklediğinizde veya kullandığınızda karşılaşabileceğiniz ağ veya ara sunucu ile ilgili hatalara yönelik çözümler bulun.
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
ms.openlocfilehash: 0abe51b9f01d0c1f380c4762a7d0d4f457964aa7
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135137"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Visual Studio 'Yu yüklerken veya kullanırken ağla ilgili hatalarda sorun giderme

Visual Studio 'Yu bir güvenlik duvarı veya proxy sunucusu arkasında yüklerken veya kullandığınızda karşılaşabileceğiniz, en tipik ağ veya ara sunucu ile ilgili hatalara yönelik çözümler sunuyoruz.

## <a name="error-proxy-authorization-required"></a>Hata: "proxy yetkilendirmesi gerekiyor"

Bu hata genellikle, kullanıcılar bir ara sunucu üzerinden İnternet 'e bağlandığında oluşur ve proxy sunucusu, Visual Studio 'Nun bazı ağ kaynaklarına yaptığı çağrıları engeller.

### <a name="to-fix-this-proxy-error"></a>Bu proxy hatasını onarmak için

- Visual Studio’yu yeniden başlatın. Proxy kimlik doğrulaması iletişim kutusu görünmelidir. İletişim kutusunda istendiğinde kimlik bilgilerinizi girin.

- Visual Studio 'Yu yeniden başlatmak sorunu çözmezse, proxy sunucunuz http: &#47;&#47;go.microsoft.com adreslerinde kimlik bilgilerini istemez ancak &#42;. visualStudio.microsoft.com adresleri için bunu yapar. Bu sunucular için, Visual Studio 'daki tüm oturum açma senaryolarına engel olmak için aşağıdaki URL 'Leri izin verilenler listesine eklemeyi göz önünde bulundurun:

  - &#42;. windows.net

  - &#42;. microsoftonline.com

  - &#42;. visualstudio.microsoft.com

  - &#42;. microsoft.com

  - &#42;. live.com

- Aksi takdirde, http: &#47;&#47;go.microsoft.com adresini izin verilenler listesinden kaldırabilirsiniz. böylece, proxy kimlik doğrulama iletişim kutusu, Visual Studio yeniden başlatıldığında hem http: &#47;&#47;go.microsoft.com adresi hem de sunucu uç noktaları için görüntülenir.

  -VEYA-

- Proxy 'niz ile varsayılan kimlik bilgilerinizi kullanmak istiyorsanız, aşağıdaki işlemleri gerçekleştirebilirsiniz:

::: moniker range="vs-2017"

  1. İçinde **devenv.exe.config** (devenv.exe yapılandırma dosyası) bulun: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** veya **% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Yapılandırma dosyasında, `<system.net>` bloğu bulun ve şu kodu ekleyin:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Ağınız için doğru proxy adresini ' de eklemeniz gerekir `proxyaddress="<http://<yourproxy:port#>` .

     > [!NOTE]
     > Daha fazla bilgi için [ &lt; defaultProxy &gt; öğesi (ağ ayarları)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) ve [ &lt; proxy &gt; öğesi (ağ ayarları)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) sayfalarına bakın.

::: moniker-end

::: moniker range="vs-2019"

  1. İçinde **devenv.exe.config** (devenv.exe yapılandırma dosyası) bulun: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** veya **% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. Yapılandırma dosyasında, `<system.net>` bloğu bulun ve şu kodu ekleyin:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Ağınız için doğru proxy adresini ' de eklemeniz gerekir `proxyaddress="<http://<yourproxy:port#>` .

     > [!NOTE]
     > Daha fazla bilgi için [ &lt; defaultProxy &gt; öğesi (ağ ayarları)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) ve [ &lt; proxy &gt; öğesi (ağ ayarları)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) sayfalarına bakın.

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Hata: bir sorun raporlanmaya çalışılırken "Visual Studio bağlantısı kesildi"

Bu hata genellikle, bir Kullanıcı bir ara sunucu üzerinden İnternet 'e bağlandığında oluşur ve proxy sunucusu, Visual Studio 'Nun bazı ağ kaynaklarına yaptığı çağrıları engeller.

### <a name="to-fix-this-proxy-error"></a>Bu proxy hatasını onarmak için

1. İçinde **feedback.exe.config** (feedback.exe yapılandırma dosyası) bulun: **% ProgramFiles (x86)% \ Microsoft Visual Studio\ınstaller** veya **%ProgramFiles%\Microsoft Visual studio\ınstaller**.

2. Yapılandırma dosyasında aşağıdaki kodun mevcut olup olmadığını kontrol edin; kod yoksa, son satırdan önce ekleyin `</configuration>` .

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

## <a name="error-the-underlying-connection-was-closed"></a>Hata: "temeldeki bağlantı kapatıldı"

Visual Studio 'Yu güvenlik duvarı olan bir özel ağda kullanıyorsanız, Visual Studio bazı ağ kaynaklarına bağlanabilmeyebilir. Bu kaynaklar, oturum açma ve lisanslama, NuGet ve Azure hizmetleri için Azure DevOps Services içerebilir. Visual Studio bu kaynaklardan birine bağlanamıyorsa aşağıdaki hata iletisini görebilirsiniz:

  **Temel alınan bağlantı kapatıldı: gönderme sırasında beklenmeyen bir hata oluştu**

Visual Studio, ağ kaynaklarına bağlanmak için Aktarım Katmanı Güvenliği (TLS) 1,2 protokolünü kullanır. Bazı özel ağlardaki güvenlik gereçleri, Visual Studio TLS 1,2 kullandığında bazı sunucu bağlantılarını engeller.

### <a name="to-fix-this-connection-error"></a>Bu bağlantı hatasını onarmak için

Aşağıdaki URL 'Ler için bağlantıları etkinleştirin:

- https: &#47;&#47;management.core.windows.net

- https: &#47;&#47;app.vssps.visualstudio.com

- https: &#47;&#47;login.microsoftonline.com

- https: &#47;&#47;login.live.com

- https: &#47;&#47;go.microsoft.com

- https: &#47;&#47;graph.windows.net

- https: &#47;&#47;app.vsspsext.visualstudio.com

- &#42;. azurewebsites.net (Azure bağlantıları için)

- &#42;. visualstudio.microsoft.com

- cdn.vsassets.io (içerik teslim ağı veya CDN, içerik barındırır)

- &#42;. gallerycdn.vsassets.io (konaklar Azure DevOps Services uzantıları)

- static2.sharepointonline.com (Visual Studio 'Nun Office UI Fabric Kit 'te yazı tipleri gibi kullandığı kaynakları barındırır)

- &#42;. nuget.org (NuGet bağlantıları için)

  > [!NOTE]
  > Özel olarak sahip olan NuGet sunucusu URL 'Leri bu listeye dahil olmayabilir. % APPData% \Nuget\NuGet.Config içinde kullandığınız NuGet sunucularını kontrol edebilirsiniz.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Hata: "KIMLIĞI üst işlemden ayrıştırılamadı"

Bir Visual Studio önyükleyici ve bir ağ sürücüsündeki dosya response.jskullandığınızda bu hata iletisiyle karşılaşabilirsiniz. Hatanın kaynağı Windows 'daki Kullanıcı hesabı denetimidir (UAC).

Bu hata şu anda oluşabilir: eşlenen bir ağ sürücüsü veya [UNC](/dotnet/standard/io/file-path-formats#unc-paths) paylaşımının bir kullanıcının erişim belirtecine bağlı olması. UAC etkinleştirildiğinde, iki Kullanıcı [erişim belirteci](/windows/win32/secauthz/access-tokens) oluşturulur: biri yönetici erişimine *sahip* diğeri yönetici erişimi *olmayan* bir. Bir ağ sürücüsü veya paylaşma oluşturulduğunda, kullanıcının geçerli erişim belirteci buna bağlanır. Önyükleyicinin yönetici olarak çalıştırılması gerektiğinden, sürücü veya paylaşımın yönetici erişimi olan bir Kullanıcı erişim belirtecine bağlı olmaması durumunda ağ sürücüsüne veya paylaşıma erişemez.

### <a name="to-fix-this-error"></a>Bu hatayı düzeltmek için

`net use`Komutunu kullanabilirsiniz veya UAC Grup İlkesi ayarını değiştirebilirsiniz. Bu geçici çözümler ve bunların nasıl uygulanacağı hakkında daha fazla bilgi için, aşağıdaki Microsoft destek makalelerine bakın:

* [UAC, Windows 'ta "kimlik bilgilerini ıste" olarak yapılandırıldığında, eşlenen sürücüler yükseltilmiş bir istem içinden kullanılamaz](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Windows işletim sistemlerinde Kullanıcı hesabı denetimini etkinleştirdikten sonra programlar bazı ağ konumlarına erişemeyebilir](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu bir güvenlik duvarı veya ara sunucusunun arkasına yükleme ve burada kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio'yu yükleme](install-visual-studio.md)
