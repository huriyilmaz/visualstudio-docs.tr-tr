---
title: Service Essentials | Microsoft Docs
description: Başka bir VSPackage'ın tüketmesi için arabirim olan hizmetler hakkında bilgi öğrenin. VSPackage'daki hizmetler yerleşik veya diğer hizmetleri geçersiz kılmış olabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 66b5689c2212104608361ccc07a799051e4627eb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627333"
---
# <a name="service-essentials"></a>Hizmet Temel Bileşenleri
Hizmet, iki VSPackage arasındaki bir sözleşmedir. Bir VSPackage, başka bir VSPackage'ın tüketmesi için belirli bir arabirim kümesi sağlar. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , diğer VSPackage'lara hizmet sağlayan bir VSPackage koleksiyonudur.

 Örneğin, etkinlik günlüğüne yazmak için kullanabileceğiniz bir IVsActivityLog arabirimi elde etmek için SVsActivityLog hizmetini kullanabilirsiniz. Daha fazla bilgi için, [bkz. How to: Use the Activity Log](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayrıca kayıtlı olmayan bazı yerleşik hizmetler de sağlar. VSPackage'lar bir hizmet geçersiz kılma sağlayarak yerleşik veya diğer hizmetleri değiştirebilir. Herhangi bir hizmet için yalnızca bir hizmet geçersiz kılmaya izin verilir.

 Hizmetlerin keşfedebilirliği yoktur. Bu nedenle, tüketmek istediğiniz hizmetin hizmet tanımlayıcısını (SID) ve hangi arabirimleri sağladığını biliyor gerekir. Hizmetin başvuru belgeleri bu bilgileri sağlar.

- Hizmet sağlayan VSPackage'lar hizmet sağlayıcısı olarak adlandırılan bir hizmet sağlayıcısıdır.

- Diğer VSPackage'lara sağlanan hizmetlere genel hizmetler denir.

- Yalnızca bunları uygulayan VSPackage'da veya oluşturduğu herhangi bir nesnede kullanılabilen hizmetlere yerel hizmetler denir.

- Diğer paketler tarafından sağlanan yerleşik hizmetlerin veya hizmetlerin yerini alan hizmetlere hizmet geçersiz kılma adı verilmektedir.

- Hizmetler veya hizmet geçersiz kılmaları isteğe bağlı olarak yüklenir; diğer bir ifadeyle hizmet sağlayıcısı, sağladığı hizmet başka bir VSPackage tarafından istenmiş olduğunda yüklenir.

- Bir hizmet sağlayıcısı, isteğe bağlı yüklemeyi desteklemek için genel hizmetlerini hizmetine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaydettirmektedir. Daha fazla bilgi için, [bkz. How to: Provide a Service](../../extensibility/how-to-provide-a-service.md).

- Bir hizmet edindikten sonra, istenen arabirimi almak için [QueryInterface](/cpp/atl/queryinterface) (yönetilemeyen kod) veya atama (yönetilen kod) kullanın, örneğin:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Yönetilen kod, türüne göre bir hizmete, yönetilemeyen kod ise GUID'si ile hizmete başvurur.

- Bir VSPackage yüklerken, VSPackage'a genel hizmetlere erişim vermek için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir hizmet sağlayıcısını VSPackage'a iletir. Bu, VSPackage'da "siting" olarak adlandırılır.

- VSPackage'lar, oluşturdukları nesneler için hizmet sağlayıcıları olabilir. Örneğin, bir form bir renk hizmeti için çerçeveye istek gönderebilir ve bu da isteği 'ye [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iletir.

- İç içe geçmiş veya hiç siteden yerleştirmediğimiz yönetilen nesneler, genel <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> hizmetlere doğrudan erişim için çağrıda olabilir.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>GetGlobalService kullanma

Bazen, bir araç penceresinden veya sited 2019'da yer almayan veya istediğiniz hizmeti bilmiyor bir hizmet sağlayıcısıyla siteli olan kapsayıcıyı denetlemeniz gerekebilir. Örneğin, bir denetimden etkinlik günlüğüne yazmak istiyor olabilir. Bu ve diğer senaryolar hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: HizmetLerde Sorun Giderme.](../../extensibility/how-to-troubleshoot-services.md)

Statik yöntemi çağırarak Visual Studio hizmetlerinden çoğunu <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> eldeabilirsiniz.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> , Paketten türetilen herhangi bir VSPackage ilk kez siteli olarak başlatılan önbelleğe alınmış bir hizmet sağlayıcısını kullanır. Bu koşulun karşılanır veya null hizmet için hazırlanır.

Neyse ki <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> çoğu zaman doğru şekilde çalışıyor.

- VsPackage yalnızca başka bir VSPackage için bilinen bir hizmet sağlıyorsa, hizmeti talep alan VSPackage hizmeti yüklenmeden önce SITED'ye yüklenir.

- VsPackage tarafından bir araç penceresi oluşturulursa VSPackage, araç penceresi oluşturulmadan önce siteden oluşturulur.

- Bir denetim kapsayıcısı VSPackage tarafından oluşturulan bir araç penceresi tarafından barındırıldısa, vsPackage denetim kapsayıcısı oluşturulmadan önce siteden oluşturulur.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Araç penceresinden veya denetim kapsayıcısı içinde bir hizmet almak için

- Oluşturucu, araç penceresi veya denetim kapsayıcısı içine şu kodu girin:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Bu kod bir SVsActivityLog hizmeti edinir ve bunu etkinlik günlüğüne yazmak için kullanılan bir IVsActivityLog arabirimine yazar. Bir örnek için, [bkz. Nasıl: Etkinlik Günlüğünü Kullanma.](../../extensibility/how-to-use-the-activity-log.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanılabilir Hizmetlerin Listesi](../../extensibility/internals/list-of-available-services.md)
- [Hizmetleri Kullanma ve Sağlama](../../extensibility/using-and-providing-services.md)
- [Atama ve Tür Dönüşümleri](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Atama](/cpp/cpp/casting)
