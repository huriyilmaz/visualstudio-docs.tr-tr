---
title: Hizmetler kaydediliyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 64f2afa6e853978e919e466f91475bed1e8d698c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62971296"
---
# <a name="registering-services"></a>Hizmetler kaydediliyor
İsteğe bağlı yüklemeyi desteklemek için, bir hizmet sağlayıcının ile küresel hizmetlerini kaydetmesi gerekir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Geliştirme sırasında yönetilen hizmet sağlayıcıları, paketler için kaynak koda öznitelikler ekleyerek ve ardından IDE 'de paketleri oluşturarak Hizmetleri ve hizmet geçersiz kılmalarını kaydeder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bu, paketi kaydederek ve dağıtım için hazırlandığından elde edilen derlemede RegPkg.exe yardımcı programını çalıştırır. Daha fazla bilgi için bkz. [nasıl yapılır: hizmet kaydetme](../misc/how-to-register-a-service.md).  
  
 Yönetilmeyen hizmet sağlayıcılarının [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hizmetleri bölümünde veya sistem kayıt defteri 'nin hizmet geçersiz kılmaları bölümünde sağladıkları Hizmetleri kaydetmesi gerekir. Aşağıdaki. reg dosya parçasında, SVsTextManager hizmetinin nasıl kaydedileceği gösterilmektedir:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 Yukarıdaki örnekte, sürüm numarası 7,1 veya 8,0 gibi bir sürümüdür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , {F5E7E71D-1401-11D1-883B-0000F87579D2} anahtarı hizmetin hizmet tanımlayıcısıdır (SID), SVsTextManager ve varsayılan değer olan {F5E7E720-1401-11D1-883B-0000F87579D2}, hizmet sağlayan VSPackage 'ın paket GUID 'sidir.  
  
## <a name="remote-services-and-background-threads"></a>Uzak hizmetler ve arka plan Iş parçacıkları  
 Sağladığınız hizmetler otomatik olarak uzaktan veya arka plan iş parçacıkları için kullanılamaz. Bunları kullanılabilir hale getirmek için, bir tür kitaplığı oluşturmanız ve kaydetmeniz gerekir.  
  
 Visual Studio kitaplığı (VSL) kullanan yönetilmeyen koddan, tür kitaplığınızı şu şekilde kaydedebilirsiniz:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Yönetilen koddan şu şekilde bir oluşturma sonrası adımı ekleyebilirsiniz:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)