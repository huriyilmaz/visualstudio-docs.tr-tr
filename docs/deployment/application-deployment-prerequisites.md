---
title: Uygulama dağıtımı önkoşulları | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8206e199acc3ccb76cf89603d48bed0173129218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66746056"
---
# <a name="application-deployment-prerequisites"></a>Uygulama dağıtımının önkoşulları

Uygulamanızın başarıyla yüklenip çalışması için, önce uygulamanızın hedef bilgisayara bağlı olduğu tüm bileşenleri yüklemeniz gerekir. Örneğin, kullanılarak oluşturulan çoğu uygulamanın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework bağımlılığı vardır. Bu durumda, uygulama yüklenmeden önce, hedef bilgisayarda ortak dil çalışma zamanının doğru sürümünün mevcut olması gerekir.

 **Önkoşullar Iletişim kutusunda** bu önkoşulları seçebilir ve .NET Framework ve diğer yeniden dağıtılabilir ' ı yüklemenizin bir parçası olarak yükleyebilirsiniz. Bu uygulama *önyükleme*olarak bilinir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]*önyükleyici*olarak da bilinen *Setup.exe*adlı bir Windows yürütülebilir programı oluşturur. Önyükleyici, uygulamanız çalışmadan önce bu önkoşulları yüklemekten sorumludur. Bu önkoşulları seçme hakkında daha fazla bilgi için bkz. [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).

 Her önkoşul bir önyükleyici paketidir. Önyükleyici paketi, önkoşulların nasıl yükleneceğini tanımlayan bildirim dosyalarını içeren bir dizin ve dosya grubudur. Uygulama önkoşulları **Önkoşul Iletişim kutusunda**listelenmiyorsa, özel önyükleyici paketleri oluşturabilir ve bunları Visual Studio 'ya ekleyebilirsiniz. Ardından **Önkoşullar Iletişim kutusunda**önkoşulları seçebilirsiniz. Daha fazla bilgi için bkz. [önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md).

 Varsayılan olarak, önyükleme ClickOnce dağıtımı için etkinleştirilmiştir. ClickOnce dağıtımı için oluşturulan önyükleyici imzalanır. Bir bileşen için önyükleyiciyi devre dışı bırakabilirsiniz, ancak yalnızca bileşenin doğru sürümünün tüm hedef bilgisayarlarda zaten yüklü olduğundan eminseniz.

## <a name="bootstrapping-and-clickonce-deployment"></a>Önyükleme ve ClickOnce dağıtımı
 Bir uygulamayı istemci bilgisayara yüklemeden önce, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildiriminde belirtilen gereksinimlere sahip olduğundan emin olmak için istemciyi inceler. Bunlar aşağıdaki gereksinimleri içerir:

- Uygulama bildiriminde derleme bağımlılığı olarak belirtilen ortak dil çalışma zamanının gerekli en düşük sürümü.

- Uygulamayı kullanan uygulama bildiriminde belirtilen şekilde uygulamanın gerektirdiği Windows işletim sisteminin gerekli en düşük sürümü `<osVersionInfo>` . (Bkz. [ \<dependency> öğesi](../deployment/dependency-element-clickonce-application.md).)

- Derleme bildiriminde derleme bağımlılığı bildirimleri tarafından belirtildiği gibi, genel derleme önbelleğinde (GAC) önceden yüklenmiş olması gereken tüm derlemelerin en düşük sürümü.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eksik önkoşulları algılayabilir ve bir önyükleyici kullanarak önkoşulları yükleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulaması ile önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

> [!NOTE]
> VeMageUI.exegibi araçlar tarafından oluşturulan bildirimlerde değerleri değiştirmek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , uygulama bildirimini * *bir metin düzenleyicisinde düzenlemeniz ve ardından hem uygulama hem de dağıtım bildirimlerini yeniden imzalamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Uygulamanızı dağıtmak için Visual Studio ve ClickOnce kullanıyorsanız, varsayılan olarak seçilen önyükleyici paketleri çözümdeki .NET Framework sürümüne göre değişir. Ancak, hedef .NET Framework sürümünü değiştirirseniz, **Önkoşullar Iletişim kutusundaki** seçenekleri el ile güncelleştirmeniz gerekir.

|Hedef .NET Framework|Seçili önyükleyici paketleri|
|---------------------------|------------------------------------|
|.NET Framework 4 İstemci Profili|.NET Framework 4 İstemci Profili<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Dağıtım ile, Yayımlama Sihirbazı tarafından oluşturulan *Publish.htm* sayfası [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , yalnızca uygulamayı yükleyen bir bağlantıya ya da hem uygulamayı hem de önyüklendi bileşenlerini yükleyen bir bağlantıya işaret eder.

 Önyükleyici 'yi ClickOnce Yayımlama Sihirbazı 'Nı veya Visual Studio 'daki Yayımla sayfasını kullanarak oluşturursanız, *Setup.exe* otomatik olarak imzalanır. Ancak, önyükleyici imzalamak için müşterinizin sertifikasını kullanmak istiyorsanız, dosyayı daha sonra imzalayabilirsiniz.

## <a name="bootstrapping-and-msbuild"></a>Önyükleme ve MSBuild
 Kullanmıyorsanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve komut satırında uygulamalarınızı derlerseniz, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önyükleme uygulamasını bir Microsoft Build Engine (MSBuild) görevi kullanarak oluşturabilirsiniz. Daha fazla bilgi için bkz. [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md).

 Önyükleme için alternatif olarak, Microsoft Systems Management Server (SMS) gibi bir elektronik yazılım dağıtım sistemini kullanarak bileşenleri önceden dağıtabilirsiniz.

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Önyükleyici (Setup.exe) komut satırı bağımsız değişkenleri
 Ve MSBuild görevleri tarafından oluşturulan *Setup.exe* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aşağıdaki komut satırı bağımsız değişkenleri kümesini destekler. Diğer bağımsız değişkenler uygulama yükleyicisine iletilir.

 Herhangi bir önyükleyici seçeneğini değiştirirseniz, imzasız önyükleyici ' yi değiştirmeli ve ardından önyükleyici dosyasını daha sonra imzalamanız gerekir.

| Komut satırı bağımsız değişkeni | Açıklama |
| - | - |
| **-?,-h,-yardım** | Bir yardım iletişim kutusu görüntüler. |
| **-URL,-ComponentsUrl** | Bu kurulum için depolanan URL ve bileşen URL 'sini gösterir. |
| **-URL =**`location` | *Setup.exe* uygulama için BAKACAĞı URL 'yi ayarlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . |
| **-ComponentsUrl =**`location` | *Setup.exe* , .NET Framework gibi bağımlılıklara BAKACAĞı URL 'yi ayarlar. |
| **-HomeSite =** `true` **&#124;**`false` | Ne zaman `true` , bağımlılıkları satıcının sitesindeki tercih edilen konumdan indirir. Bu ayar **-ComponentsUrl** ayarını geçersiz kılar. Ne zaman `false` , bağımlılıklarını **-ComponentsUrl**tarafından belirtilen URL 'den indirir. |

## <a name="operating-system-support"></a>İşletim sistemi desteği
 Windows Server 2008 Server Core veya Windows Server 2008 R2 Server Core üzerinde, sınırlı işlevlere sahip düşük bakım sunucusu ortamı sağladıkları için Visual Studio önyükleyici desteklenmez. Örneğin, Sunucu Çekirdeği yükleme seçeneği yalnızca .NET Framework 3,5 sunucu çekirdeği profilini destekler ve bu, tam .NET Framework bağlı olan Visual Studio özelliklerini çalıştıraamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)