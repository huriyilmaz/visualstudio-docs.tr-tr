---
title: Hizmet Esasları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e2947cb4cd6a347d8e010340f8689eb1907a28a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705495"
---
# <a name="service-essentials"></a>Hizmet Temel Bileşenleri
Hizmet, iki VSPackages arasındaki bir sözleşmedir. Bir VSPackage, başka bir VSPackage'ın tüketilmesi için belirli bir arayüz kümesi sağlar. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kendisi diğer VSPackages hizmetleri sağlayan VSPackages bir koleksiyondur.

 Örneğin, Etkinlik günlüğüne yazmak için kullanabileceğiniz bir IVsActivityLog arabirimi elde etmek için SVsActivityLog hizmetini kullanabilirsiniz. Daha fazla bilgi için [bkz: Etkinlik Günlüğü'nün kullanımı.](../../extensibility/how-to-use-the-activity-log.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ayrıca kayıtlı olmayan bazı yerleşik hizmetler de sağlar. VSPackages bir hizmet geçersiz kılma sağlayarak yerleşik veya diğer hizmetlerin yerini alabilir. Herhangi bir hizmet için yalnızca bir hizmet geçersiz kılmaya izin verilir.

 Servislerin keşfedilebilirliği yoktur. Bu nedenle, tüketmek istediğiniz bir hizmetin hizmet tanımlayıcısını (SID) bilmeniz ve hangi arabirimleri sağladığını bilmeniz gerekir. Hizmet için başvuru belgeleri bu bilgileri sağlar.

- Hizmet sağlayan VSPackages'e hizmet sağlayıcılar denir.

- Diğer VSPackages'e sağlanan hizmetlere global hizmetler denir.

- Yalnızca bunları uygulayan VSPackage'da veya oluşturduğu herhangi bir nesneye kullanılabilen hizmetlere yerel hizmetler denir.

- Diğer paketler tarafından sağlanan yerleşik hizmetlerin veya hizmetlerin yerini alan hizmetlere hizmet geçersiz kılma denir.

- Hizmetler veya hizmet geçersiz kılar, isteğe bağlı olarak yüklenir, yani hizmet sağlayıcı, sağladığı hizmet başka bir VSPackage tarafından istendiğinde yüklenir.

- İsteğe bağlı yüklemeyi desteklemek için, bir hizmet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sağlayıcısı küresel hizmetlerini . Daha fazla bilgi için [bkz: Hizmet sağlayın.](../../extensibility/how-to-provide-a-service.md)

- Bir hizmet aldıktan sonra, örneğin istenen arabirimi elde etmek için [QueryInterface](/cpp/atl/queryinterface) (yönetilmeyen kod) veya döküm (yönetilen kod) kullanın:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Yönetilen kod türüne göre bir hizmete başvururken, yönetilmeyen kod GUID tarafından bir hizmete başvurur.

- VSPackage yüklendiğinde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'a küresel hizmetlere erişim sağlamak için bir servis sağlayıcısından VSPackage'a geçer. Bu VSPackage "siting" olarak adlandırılır.

- VSPackages oluşturdukları nesneler için hizmet sağlayıcılar olabilir. Örneğin, bir form, çerçevesine renk hizmeti için istek gönderebilir ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bu istek .

- Derin denli iç içe olan veya hiç sited olmayan <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yönetilen nesneler, genel hizmetlere doğrudan erişim için çağrıda bulunabilir.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>GetGlobalService'i kullanma

Bazen bir araç penceresinden veya sited edilmemiş bir denetim kapsayıcısından veya istediğiniz hizmet hakkında bilgi olmayan bir hizmet sağlayıcısıyla sited'den hizmet almanız gerekebilir. Örneğin, bir denetim içinden etkinlik günlüğüne yazmak isteyebilirsiniz. Bu ve diğer senaryolar hakkında daha fazla bilgi için [bkz.](../../extensibility/how-to-troubleshoot-services.md)

Statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yöntemi arayarak çoğu Visual Studio hizmeti alabilirsiniz.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>Paketten türetilen herhangi bir VSPackage ilk kez başlatılan önbelleğe alınmış bir hizmet sağlayıcısına güvenir. Bu koşulun yerine getirildiğini garanti etmeli veya başka bir hizmetiçin hazır olmalısınız.

Neyse <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ki, çoğu zaman doğru çalışır.

- Bir VSPackage yalnızca başka bir VSPackage tarafından bilinen bir hizmet sağlıyorsa, hizmeti isteyen VSPackage, hizmeti sağlayan VSPackage yüklenmeden önce sitede yerlenir.

- Bir araç penceresi BIR VSPackage tarafından oluşturulursa, araç penceresi oluşturulmadan önce VSPackage sited edilir.

- Bir kontrol kapsayıcısı VSPackage tarafından oluşturulan bir araç penceresi tarafından barındırılırsa, kontrol kapsayıcısı oluşturulmadan önce VSPackage sitelenir.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Bir araç penceresi veya kontrol kapsayıcısı içinden hizmet almak için

- Bu kodu oluşturucuya, araç penceresine veya denetim konteynerine ekleyin:

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

    Bu kod bir SVsActivityLog hizmeti alır ve etkinlik günlüğüne yazmak için kullanılabilecek bir IVsActivityLog arabirimine atar. Örneğin, [bkz.](../../extensibility/how-to-use-the-activity-log.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanılabilir Hizmetlerin Listesi](../../extensibility/internals/list-of-available-services.md)
- [Hizmetleri Kullanma ve Sağlama](../../extensibility/using-and-providing-services.md)
- [Atama ve Tür Dönüşümleri](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Atama](/cpp/cpp/casting)
