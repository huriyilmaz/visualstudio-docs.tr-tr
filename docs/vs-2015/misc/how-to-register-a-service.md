---
title: 'Nasıl yapılır: hizmet kaydetme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: f41578f2522487f746a469933a2269a621390f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784864"
---
# <a name="how-to-register-a-service"></a>Nasıl yapılır: bir hizmeti kaydetme
Yönetilen paket çerçevesi (MPF), yönetilen hizmetlerin kaydını denetlemek için öznitelikler sağlar. RegPkg yardımcı programı, hizmetini ile kaydetmek için bu öznitelikleri kullanır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, [VSSDK örneklerinden](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>Smyıglobalservice hizmetini ile kaydeder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Ve hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> bkz. [VSPackages kaydetme ve kaydını silme](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Aynı ada sahip başka bir hizmetin yerini alan bir hizmeti kaydetmek için <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> yerine kullanın <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Hizmet istemcisini değiştirmeden bir hizmet sağlayıcısını yeniden derlemeyi kolaylaştırmak için veya bunun tersini yapmak için, hizmeti ve arabirimlerini ayrı bir derleme modülünde tanımlayabilirsiniz. Aşağıdaki kod, Reference. Services (C#) örneğindeki IMyGlobalService.cs dosyasından.  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>Arabirimin yönetilmeyen koddan alınması gerekir.  
  
> [!NOTE]
> Hem hizmet hem de arabirim için aynı türü veya GUID 'ı kullanabilseniz de, bir hizmet farklı arabirimler sergilebileceğinden ikisini de ayırmanızı öneririz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages 'yi kaydetme](../extensibility/internals/registering-vspackages.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)