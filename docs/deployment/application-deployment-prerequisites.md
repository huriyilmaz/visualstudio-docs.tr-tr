---
title: Uygulama Dağıtımı Önkoşulları | Microsoft Docs
description: Önkoşullar İletişim Kutusu ve önyükleyici paketlerini kullanma dahil olmak üzere uygulamalarınız için dağıtım önkoşulları hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 09/23/2021
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: ca078ac6051e4550cd4ec102ccb4a8067675e3fb
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427122"
---
# <a name="application-deployment-prerequisites-windows-desktop"></a>Uygulama dağıtımı önkoşulları (Windows masaüstü)

Masaüstü uygulamanıza Windows ve başarıyla çalıştırmak için, önce uygulamanın hedef bilgisayara bağımlı olduğu tüm bileşenleri yükleyin. Örneğin, kullanılarak oluşturulan uygulamaların [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çoğu, uygulamanın .NET Framework. Bu durumda, uygulama yüklenmeden önce ortak dil çalışma zamanının doğru sürümü hedef bilgisayarda mevcut olmalıdır.

Bu önkoşulları  Önkoşullar İletişim Kutusu'.NET Framework yüklemenizin bir parçası olarak .NET Framework ve diğer yeniden dağıtılabilir seçenekleri yükleyebilirsiniz. Bu uygulama *önyüklemesi olarak bilinir.* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], önyükleyici olarak Windows *adlıSetup.exe* bir yürütülebilir program *üretir.* Önkoşullar, uygulama çalıştırılamadan önce önkoşulları yüklemekten sorumludur. Bu önkoşulları seçme hakkında daha fazla bilgi için bkz. [Önkoşullar iletişim kutusu.](../ide/reference/prerequisites-dialog-box.md)

Her önkoşul bir önyükleyici paketidir. Önyükleyici paketi, önkoşulların nasıl yük olduğunu açıklayan bildirim dosyalarını içeren bir dizin ve dosya grubudur. Uygulama önkoşulları Önkoşul İletişim Kutusunda listelenmiyorsa, özel önyükleyici paketleri oluşturabilir ve bunları Visual Studio. Ardından Önkoşullar İletişim Kutusunda **önkoşulları belirleyebilirsiniz.** Daha fazla bilgi için [bkz. Önyükleyici paketleri oluşturma.](../deployment/creating-bootstrapper-packages.md)

Varsayılan olarak, önyükleme hem Windows Yükleyicisi dağıtımı (Visual Studio'da Kurulum projeleri kullanılarak) hem de ClickOnce etkinleştirilir. Windows Yükleyicisi dağıtımı için oluşturulan önyükleyici imzalanmaz, ancak ClickOnce önyükleyici imzalanmıştır. Bir bileşen için önyüklemeyi devre dışı abilirsiniz, ancak yalnızca bileşenin doğru sürümünün tüm hedef bilgisayarlara zaten yüklü olduğundan eminsanız bunu gerekir.

## <a name="bootstrapping-and-clickonce-deployment"></a>Önyükleme ve ClickOnce başlatma
 Bir uygulamayı bir istemci bilgisayara yüklemeden önce, uygulama bildiriminde belirtilen gereksinimlere sahip olduğundan emin olmak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için istemciyi inceler. Bunlar aşağıdaki gereksinimleri içerir:

- Uygulama bildiriminde derleme bağımlılığı olarak belirtilen ortak dil çalışma zamanının gereken en düşük sürümü.

- öğesi kullanılarak uygulama bildiriminde Windows için gereken en düşük işletim sistemi `<osVersionInfo>` sürümü. [ \<dependency> (Bkz. öğesi](../deployment/dependency-element-clickonce-application.md).)

- Derleme bildiriminde derleme bağımlılık bildirimleri tarafından belirtilen şekilde, genel derleme önbelleğine (GAC) önceden yüklenmiş olması gereken tüm derlemelerin en düşük sürümü.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eksik önkoşulları algılanabilir ve önkoşulları bir önyükleyici kullanarak yükleyebilirsiniz. Daha fazla bilgi için, [bkz. How to: Install prerequisites with a ClickOnce .](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)

> [!NOTE]
> veMageUI.exegibi araçlar tarafından oluşturulan bildirimlerde yer alan değerleri değiştirmek için, uygulama bildirimini bir metin düzenleyicisinde düzenlemeniz ve ardından hem uygulama hem de dağıtım bildirimlerini yeniden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] imzalamanız gerekir. ** Daha fazla bilgi için, [bkz. How to: Re-sign application and deployment manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Uygulamanızı dağıtmak Visual Studio ClickOnce önyükleyici paketlerini kullanırsanız, varsayılan olarak seçilen önyükleyici paketleri çözümde .NET Framework sürümüne bağlıdır. Ancak, hedef sürümü değiştirir .NET Framework Önkoşullar İletişim Kutusundaki seçenekleri **el ile güncelleştirmeniz** gerekir.

|Hedef .NET Framework|Seçili Önyükleyici Paketleri|
|---------------------------|------------------------------------|
|.NET Framework 4 İstemci Profili|.NET Framework 4 İstemci Profili<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 Dağıtımda,Publish.htmSihirbazı tarafından oluşturulan sayfa yalnızca uygulamayı yüklayan bir bağlantıya veya hem uygulamayı hem de önyüklenen bileşenleri yüklayan bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bağlantıya  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] başvurur.

 ClickOnce Yayımlama Sihirbazı'nı veya Visual Studio'da Yayımla Sihirbazı'nı kullanarak önyükleyiciyi *Setup.exe* otomatik olarak imzalarsınız. Öte yandan önyükleyiciyi imzalamak için müşterinizin sertifikasını kullanmak için dosyayı daha sonra imzaabilirsiniz.

## <a name="bootstrapping-and-msbuild"></a>Önyükleme ve MSBuild
 kullanmazsanız, uygulamalarınızı komut satırına derlemek yerine, bir Microsoft Build Engine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] (MSBuild) görevi kullanarak önyükleme uygulamasını oluşturabilirsiniz. Daha fazla bilgi için [bkz. GenerateBootstrapper görevi.](../msbuild/generatebootstrapper-task.md)

 Önyüklemeye alternatif olarak, Microsoft Systems Management Server (SMS) gibi bir elektronik yazılım dağıtım sistemi kullanarak bileşenleri önceden dağıtabilirsiniz.

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Önyükleyici (Setup.exe) komut satırı bağımsız değişkenleri
 tarafından *Setup.exe* komut satırı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] MSBuild aşağıdaki komut satırı bağımsız değişkenlerini destekler. Diğer bağımsız değişkenler uygulama yükleyiciye iletildi.

 Herhangi bir önyükleyici seçeneği değiştirirsanız, imzalanmamış önyükleyiciyi değiştirmeli ve ardından önyükleyici dosyasını imzalamanız gerekir.

| Komut satırı bağımsız değişkeni | Description |
| - | - |
| **-?, -h, -help** | Bir Yardım iletişim kutusu görüntüler. |
| **-url, -componentsurl** | Bu ayar için depolanan URL'yi ve bileşenler URL'sini gösterir. |
| **-url=** `location` | Url'yi *Setup.exe* için aramanın nerede olduğunu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ayarlar. |
| **-componentsurl=** `location` | Url'yi *ayarlarSetup.exe* gibi bağımlılıkları .NET Framework. |
| **-homesite=** `true` **&#124;** `false` | olduğunda, `true` bağımlılıkları satıcının sitesinde tercih edilen konumdan indirir. Bu ayar **-componentsurl ayarını geçersiz** kılar. olduğunda `false` , **-componentsurl** tarafından belirtilen URL'den bağımlılıkları indirir. |

## <a name="operating-system-support"></a>İşletim sistemi desteği
 Visual Studio önyükleyicisi, Windows Server 2008 Sunucu Çekirdeği veya Windows Server 2008 R2 Sunucu Çekirdeği üzerinde desteklanmaz çünkü sınırlı işlevsellikle düşük bakımlı bir sunucu ortamı sağlar. Örneğin, Sunucu Çekirdeği yükleme seçeneği yalnızca .NET Framework 3.5 Sunucu Çekirdeği profilini destekler ve bu profil tam sunucu Visual Studio özellikleri .NET Framework.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)