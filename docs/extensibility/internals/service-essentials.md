---
title: Hizmet temelleri | Microsoft Docs
description: Başka bir VSPackage 'ın tüketmesi için arabirimler olan hizmetler hakkında bilgi edinin. VSPackage içindeki hizmetler, yerleşik veya diğer hizmetleri geçersiz kılabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 145097b9e012d8c09df1424747d04148df3cae8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911008"
---
# <a name="service-essentials"></a>Hizmet Temel Bileşenleri
Hizmet iki VSPackages arasında bir sözleşmedir. Bir VSPackage, başka bir VSPackage kullanması için belirli bir arabirim kümesi sağlar. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , diğer VSPackages 'e hizmet sağlayan VSPackages koleksiyonudur.

 Örneğin, SVsActivityLog hizmetini kullanarak, etkinlik günlüğüne yazmak için kullanabileceğiniz bir ıtransactedtivitylog arabirimi elde edebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , kayıtlı olmayan bazı yerleşik hizmetler de sağlar. VSPackages, hizmet geçersiz kılma sağlayarak yerleşik veya diğer Hizmetleri değiştirebilir. Her hizmet için yalnızca bir hizmete geçersiz kılmaya izin verilir.

 Hizmetlerin bulunabilirliği yok. Bu nedenle, kullanmak istediğiniz bir hizmetin hizmet tanımlayıcısını (SID) bilmeniz ve hangi arabirimlerin sağladığını bilmeniz gerekir. Hizmet için başvuru belgeleri bu bilgileri sağlar.

- Hizmetler sağlayan VSPackages, hizmet sağlayıcıları olarak adlandırılır.

- Diğer VSPackages 'e sunulan hizmetlere küresel hizmetler denir.

- Yalnızca bunları uygulayan VSPackage veya oluşturduğu herhangi bir nesne için kullanılabilen hizmetler yerel hizmetler olarak adlandırılır.

- Diğer paketler tarafından sunulan yerleşik hizmetleri veya hizmetleri değiştiren hizmetler, hizmet geçersiz kılma olarak adlandırılır.

- Hizmetler veya hizmet geçersiz kılmaları, isteğe bağlı olarak yüklenir, diğer bir deyişle, hizmet sağlayıcısı, sağladığı hizmet başka bir VSPackage tarafından istendiğinde yüklenir.

- İsteğe bağlı yüklemeyi desteklemek için bir hizmet sağlayıcı, genel hizmetlerini ile kaydeder [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Daha fazla bilgi için bkz. [nasıl yapılır: hizmet sağlama](../../extensibility/how-to-provide-a-service.md).

- Bir hizmeti elde ettikten sonra, istenen arabirimi almak için [QueryInterface](/cpp/atl/queryinterface) (yönetilmeyen kod) veya atama (yönetilen kod) kullanın, örneğin:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Yönetilen kod, türüne göre bir hizmete başvurur, yönetilmeyen kod ise bir hizmete GUID tarafından başvurur.

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Bir VSPackage yüklediğinde, genel hizmetlere VSPackage erişimi sağlamak için bir hizmet sağlayıcısını VSPackage 'a geçirir. Bu, VSPackage olarak adlandırılır.

- VSPackages, oluşturdukları nesneler için hizmet sağlayıcıları olabilir. Örneğin, bir form bir renk hizmeti için bir istek gönderebilir ve bu, isteği öğesine geçirebilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Derin iç içe geçmiş veya hiç yerleştirilmemiş yönetilen nesneler, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> küresel hizmetlere doğrudan erişim için çağrı gösterebilir.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>GetGlobalService kullanma

Bazen bir araç penceresi veya denetim kapsayıcısından bir hizmet almanız ya da başka bir hizmet sağlayıcı ile istediğiniz hizmet hakkında bilgi sahibi olmaması gerekebilir. Örneğin, bir denetim içinden etkinlik günlüğüne yazmak isteyebilirsiniz. Bu ve diğer senaryolar hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri sorun giderme](../../extensibility/how-to-troubleshoot-services.md).

Statik yöntemi çağırarak, çoğu Visual Studio hizmetini edinebilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> , paketten türetilen herhangi bir VSPackage ilk kez başlatılan önbelleğe alınmış bir hizmet sağlayıcısına dayanır. Bu koşulun karşılandığından emin olmanız gerekir, aksi takdirde boş bir hizmet için hazır olun.

Neyse ki, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> çoğu zaman doğru bir şekilde çalışmaktadır.

- Bir VSPackage yalnızca başka bir VSPackage için bilinen bir hizmet sağlıyorsa, hizmeti sağlayan VSPackage, hizmeti sağlayan VSPackage yüklenmeden önce oluşur.

- Bir VSPackage tarafından bir araç penceresi oluşturulduysa, aracı penceresi oluşturulmadan önce VSPackage oluşur.

- Bir denetim kapsayıcısı VSPackage tarafından oluşturulan bir araç penceresi tarafından barındırılıyorsa, Denetim kapsayıcısı oluşturulmadan önce VSPackage kullanılır.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Bir araç penceresi veya Denetim kapsayıcısı içinden bir hizmet almak için

- Oluşturucuya, araç penceresine veya denetim kapsayıcısına bu kodu ekleyin:

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

    Bu kod, bir SVsActivityLog hizmeti alır ve bunu etkinlik günlüğüne yazmak için kullanılabilecek bir ıtransactedtivitylog arabirimine yayınlar. Bir örnek için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanılabilir Hizmetlerin Listesi](../../extensibility/internals/list-of-available-services.md)
- [Hizmetleri Kullanma ve Sağlama](../../extensibility/using-and-providing-services.md)
- [Atama ve Tür Dönüşümleri](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Atama](/cpp/cpp/casting)
