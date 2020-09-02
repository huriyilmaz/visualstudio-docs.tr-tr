---
title: "Nasıl yapılır: GetGlobalService 'i kullanma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948188"
---
# <a name="how-to-use-getglobalservice"></a>Nasıl yapılır: GetGlobalService kullanma
Bazen bir araç penceresi veya denetim kapsayıcısından bir hizmet almanız ya da başka bir hizmet sağlayıcı ile istediğiniz hizmet hakkında bilgi sahibi olmaması gerekebilir. Örneğin, bir denetim içinden etkinlik günlüğüne yazmak isteyebilirsiniz. Bu ve diğer senaryolar hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri sorun giderme](../extensibility/how-to-troubleshoot-services.md).  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Statik yöntemi çağırarak çoğu hizmeti edinebilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> , ' den türetilen herhangi bir VSPackage ilk kez başlatılan önbelleğe alınmış bir hizmet sağlayıcısına dayanır <xref:Microsoft.VisualStudio.Shell.Package> . Bu koşulun karşılandığından emin olmanız gerekir, aksi takdirde boş bir hizmet için hazır olun.  
  
 Neyse ki, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> çoğu zaman doğru bir şekilde çalışmaktadır.  
  
- Bir VSPackage yalnızca başka bir VSPackage için bilinen bir hizmet sağlıyorsa, hizmeti sağlayan VSPackage, hizmeti sağlayan VSPackage yüklenmeden önce oluşur.  
  
- Bir VSPackage tarafından bir araç penceresi oluşturulduysa, aracı penceresi oluşturulmadan önce VSPackage oluşur.  
  
- Bir denetim kapsayıcısı VSPackage tarafından oluşturulan bir araç penceresi tarafından barındırılıyorsa, Denetim kapsayıcısı oluşturulmadan önce VSPackage kullanılır.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Bir araç penceresi veya Denetim kapsayıcısı içinden bir hizmet almak için  
  
- Oluşturucuya, araç penceresine veya denetim kapsayıcısına bu kodu ekleyin:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Bu kod, bir SVsActivityLog hizmeti alır ve bunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> etkinlik günlüğüne yazmak için kullanılabilecek bir arabirime yayınlar. Bir örnek için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: hizmetler sorunlarını giderme](../extensibility/how-to-troubleshoot-services.md)   
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)