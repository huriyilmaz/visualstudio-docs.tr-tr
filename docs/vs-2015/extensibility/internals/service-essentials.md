---
title: Hizmet temelleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696076"
---
# <a name="service-essentials"></a>Hizmet Temel Bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hizmet iki VSPackages arasında bir sözleşmedir. Bir VSPackage, başka bir VSPackage kullanması için belirli bir arabirim kümesi sağlar. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , diğer VSPackages 'e hizmet sağlayan VSPackages koleksiyonudur.  
  
 Örneğin, SVsActivityLog hizmetini kullanarak, etkinlik günlüğüne yazmak için kullanabileceğiniz bir ıtransactedtivitylog arabirimi elde edebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , kayıtlı olmayan bazı yerleşik hizmetler de sağlar. VSPackages, hizmet geçersiz kılma sağlayarak yerleşik veya diğer Hizmetleri değiştirebilir. Her hizmet için yalnızca bir hizmete geçersiz kılmaya izin verilir.  
  
 Hizmetlerin bulunabilirliği yok. Bu nedenle, kullanmak istediğiniz bir hizmetin hizmet tanımlayıcısını (SID) bilmeniz ve hangi arabirimlerin sağladığını bilmeniz gerekir. Hizmet için başvuru belgeleri bu bilgileri sağlar.  
  
- Hizmetler sağlayan VSPackages, hizmet sağlayıcıları olarak adlandırılır.  
  
- Diğer VSPackages 'e sunulan hizmetlere küresel hizmetler denir.  
  
- Yalnızca bunları uygulayan VSPackage veya oluşturduğu herhangi bir nesne için kullanılabilen hizmetler yerel hizmetler olarak adlandırılır.  
  
- Diğer paketler tarafından sunulan yerleşik hizmetleri veya hizmetleri değiştiren hizmetler, hizmet geçersiz kılma olarak adlandırılır.  
  
- Hizmetler veya hizmet geçersiz kılmaları, isteğe bağlı olarak yüklenir, diğer bir deyişle, hizmet sağlayıcısı, sağladığı hizmet başka bir VSPackage tarafından istendiğinde yüklenir.  
  
- İsteğe bağlı yüklemeyi desteklemek için bir hizmet sağlayıcı, genel hizmetlerini ile kaydeder [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [Hizmetleri kaydetme](../../misc/registering-services.md).  
  
- Bir hizmeti elde ettikten sonra, istenen arabirimi almak için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (yönetilmeyen kod) veya atama (yönetilen kod) kullanın, örneğin:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- Yönetilen kod, türüne göre bir hizmete başvurur, yönetilmeyen kod ise bir hizmete GUID tarafından başvurur.  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Bir VSPackage yüklediğinde, genel hizmetlere VSPackage erişimi sağlamak için bir hizmet sağlayıcısını VSPackage 'a geçirir. Bu, VSPackage olarak adlandırılır.  
  
- VSPackages, oluşturdukları nesneler için hizmet sağlayıcıları olabilir. Örneğin, bir form bir renk hizmeti için bir istek gönderebilir ve bu, isteği öğesine geçirebilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Derin iç içe geçmiş veya hiç yerleştirilmemiş yönetilen nesneler, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> küresel hizmetlere doğrudan erişim için çağrı gösterebilir. Daha fazla bilgi için bkz. [nasıl yapılır: GetGlobalService kullanma](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanılabilir Hizmetler listesi](../../extensibility/internals/list-of-available-services.md)   
 [Hizmetleri kullanma ve sağlama](../../extensibility/using-and-providing-services.md)   
 [Atama ve tür dönüşümleri](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Atama](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
