---
title: Yapılandırma ve Selecteditıtem nesneleri için Otomasyon | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157251"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Yapılandırma ve SelectedItem Nesneleri için Otomasyon
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İçindeki derleme ve seçili öğe işlemlerini otomatikleştirebilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Derlemeler için Otomasyon  
 Derleme veya yapılandırmanın, uyguladığınızda sağlanmış bir otomasyon modeli vardır <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../../ide/understanding-build-configurations.md).  
  
 Bir VSPackage oluşturup yapılandırma seçeneklerini denetlemek istiyorsanız otomasyon modelini kullanmanız gerekir.  
  
## <a name="automation-for-selecteditem"></a>Selecteditıtem Otomasyonu  
 `SelectedItem`Visual Studio standart bir uygulama içerdiğinden nesne için bir uygulama sağlamanız gerekmez. Ancak, `SelectedItem` isterseniz nesneyi uygulayabilirsiniz. Arabirimini içeren bir nesne uygulamanız `SelectedItem` ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSITEMıD olarak ayarlanan yönteme bir çağrıya yanıt döndürmelidir <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Otomasyon modeline katkıda bulunma](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Derleme yapılandırmasını anlama](../../ide/understanding-build-configurations.md)
