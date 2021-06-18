---
title: Ağ veya ara sunucu hatalarını giderme
description: Bir güvenlik duvarı veya ara sunucu arkasında ağ veya ara sunucu yükleme veya kullanma sırasında karşılaşabilirsiniz Visual Studio ağ veya ara sunucu ile ilgili hataların çözümlerini bulun.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5e7d54b4e7777b3569031e96760699e7c075245f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306832"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Ağ ile ilgili sorunları, Visual Studio'i yükleme veya kullanma sırasında Visual Studio

Bir güvenlik duvarı veya ara sunucu arkasında yükleme veya kullanma sırasında karşılaş olabileceğiniz en tipik ağ veya ara sunucu Visual Studio hatalarına yönelik çözümlerimiz var.

## <a name="error-proxy-authorization-required"></a>Hata: "Ara sunucu yetkilendirmesi gerekiyor"

Bu hata genellikle kullanıcılar bir ara sunucu üzerinden İnternet'e bağlandığında ve ara sunucu bazı ağ kaynaklarına Visual Studio çağrıları engellerken oluşur.

### <a name="to-fix-this-proxy-error"></a>Bu ara sunucu hatasını düzeltmek için

- Visual Studio’yu yeniden başlatın. Ara sunucu kimlik doğrulaması iletişim kutusu görüntü gerekir. İletişim kutusuna istendiğinde kimlik bilgilerinizi girin.

- Yeniden başlatma Visual Studio sorunu çözene kadar ara sunucunuz http:&#47;&#47;go.microsoft.com adresleri için kimlik bilgileri isteminde A2.visualStudio.microsoft.com olabilir. Bu sunucular için, bir izin verme listesine aşağıdaki URL'leri ekleyerek aşağıdaki sunucularda tüm oturum açma senaryolarının engelini Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- Aksi takdirde http:&#47;&#47;go.microsoft.com adresini izin verme listesinden kaldırabilirsiniz; böylece ara sunucu kimlik doğrulaması iletişim kutusu, yeniden başlatıldığında hem http:&#47;&#47;go.microsoft.com adresi hem de sunucu uç Visual Studio görünür.

  -VEYA-

- Proxy'niz ile varsayılan kimlik bilgilerinizi kullanmak için aşağıdaki eylemleri gerçekleştirin:

::: moniker range="vs-2017"

  1. Şu **devenv.exe.config** (devenv.exe yapılandırma dosyası) bulun: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** veya **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Yapılandırma dosyasında bloğu bulun `<system.net>` ve şu kodu ekleyin:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      içinde ağınız için doğru ara sunucu adresini `proxyaddress="<http://<yourproxy:port#>` ekleyebilirsiniz.

     > [!NOTE]
     > Daha fazla bilgi için [ &lt; defaultProxy &gt; Öğesi (Ağ Ayarları) ve](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) proxy Öğesi [ &lt; &gt; (Ağ Ayarları) sayfalarına](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) bakın.

::: moniker-end

::: moniker range=">=vs-2019"

  1. Şu **devenv.exe.config** (devenv.exe yapılandırma dosyası) bulun: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** veya **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. Yapılandırma dosyasında bloğu bulun `<system.net>` ve şu kodu ekleyin:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      içinde ağınız için doğru ara sunucu adresini `proxyaddress="<http://<yourproxy:port#>` ekleyebilirsiniz.

     > [!NOTE]
     > Daha fazla bilgi için [ &lt; defaultProxy &gt; Öğesi (Ağ Ayarları) ve](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) proxy Öğesi [ &lt; &gt; (Ağ Ayarları) sayfalarına](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) bakın.

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Hata: Sorun bildirmeye Visual Studio "Bağlantı kesildi"

Bu hata genellikle bir kullanıcı bir ara sunucu üzerinden İnternet'e bağlandığında ve ara sunucu bazı ağ kaynaklarına Visual Studio çağrıları engellerken oluşur.

### <a name="to-fix-this-proxy-error"></a>Bu ara sunucu hatasını düzeltmek için

1. Şu **feedback.exe.config** (feedback.exe yapılandırma dosyası) bulun: **%ProgramFiles(x86)%\Microsoft Visual Studio\Installer** veya **%ProgramFiles%\Microsoft Visual Studio\Installer**.

2. Yapılandırma dosyasında aşağıdaki kodun mevcut olup olmadığını kontrol edin; Kod yoksa, son satırdan önce `</configuration>` ekleyin.

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

## <a name="error-the-underlying-connection-was-closed"></a>Hata: "Temel alınan bağlantı kapatıldı"

Güvenlik duvarı olan Visual Studio ağ kullanıyorsanız, Visual Studio ağ kaynaklarına bağlanamayabilirsiniz. Bu kaynaklar oturum Azure DevOps Services lisanslama, NuGet ve Azure hizmetleri için kullanılabilir. Bu Visual Studio bağlantı kuramazsanız aşağıdaki hata iletisini alabilirsiniz:

  **Temel alınan bağlantı kapatıldı: Gönderme sırasında beklenmeyen bir hata oluştu**

Visual Studio kaynaklarına bağlanmak için Aktarım Katmanı Güvenliği (TLS) 1.2 protokolünü kullanır. Bazı özel ağlarda güvenlik gereçleri TLS 1.2 Visual Studio bazı sunucu bağlantılarını engellemektedir.

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

- cdn.vsassets.io (içerik teslim ağına veya CDN içeriğine sahip)

- &#42;.gallerycdn.vsassets.io (konaklar Azure DevOps Services uzantıları)

- static2.sharepointonline.com (Office UI Visual Studio setini kullanan yazı tipleri gibi kaynakları barındırarak)

- &#42;.nuget.org (NuGet bağlantıları için)

  > [!NOTE]
  > Özel olarak sahip olunan NuGet sunucu URL'leri bu listeye dahil edem olabilir. %APPData%\Nuget\NuGet.Config içinde kullanmakta olan NuGet sunucularını \Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Hata: "Üst işlemden kimlik ayrıştırılamadı"

Ağ sürücüsü üzerinde bir önyükleyici ve Visual Studio bir response.jsbu hata iletisiyle karşılaşabilirsiniz. Hatanın kaynağı, Windows'da Kullanıcı Hesabı Denetimi 'dir (UAC).

Bu hatanın nedeni şu olabilir: Eşlenmiş bir ağ sürücüsü veya [UNC](/dotnet/standard/io/file-path-formats#unc-paths) paylaşımı kullanıcının erişim belirteclerine bağlıdır. UAC etkinleştirildiğinde iki kullanıcı [erişim belirteci](/windows/win32/secauthz/access-tokens) oluşturulur: Biri yönetici erişimi olan, biri yönetici  *erişimi* olmayan. Bir ağ sürücüsü veya paylaşım oluşturulduğunda, kullanıcının geçerli erişim belirteci buna bağlıdır. Önyükleyicinin yönetici olarak çalışması gerek olduğundan, sürücü veya paylaşım yönetici erişimine sahip bir kullanıcı erişim belirteci ile bağlantılı değilse ağ sürücüsüne veya paylaşıma erişemiyor olabilir.

### <a name="to-fix-this-error"></a>Bu hatayı düzeltmek için

komutunu kullanabilir `net use` veya UAC komut satırı grup ilkesi değiştirebilirsiniz. Bu geçici çözümler ve bunların nasıl uygulanarak ilgili daha fazla bilgi için aşağıdaki Microsoft destek makalelerine bakın:

* [Windows'da UAC "Kimlik bilgilerini sor" olarak yapılandırıldığında, eşlenen sürücüler yükseltilmiş bir istemden kullanılamaz](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Windows işletim sistemlerinde Kullanıcı Hesabı Denetimi'ne başladıktan sonra programlar bazı ağ konumlarına erişemiyor olabilir](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu bir güvenlik duvarı veya ara sunucusunun arkasına yükleme ve burada kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio'yu yükleme](install-visual-studio.md)
