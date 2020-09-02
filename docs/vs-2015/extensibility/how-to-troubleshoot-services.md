---
title: 'Nasıl yapılır: hizmetler sorunlarını giderme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5311aa3ff390611942aa91cb1f2a53ca5a76258d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204063"
---
# <a name="how-to-troubleshoot-services"></a>Nasıl Yapılır: Hizmetlerde Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir hizmeti almaya çalıştığınızda oluşabilecek bazı yaygın sorunlar vardır:  
  
- Hizmet hizmetine kayıtlı değil [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Hizmet, hizmet türüne göre değil arabirim türü tarafından istenir.  
  
- Hizmeti isteyen VSPackage yok.  
  
- Yanlış hizmet sağlayıcısı kullanılıyor.  
  
  İstenen hizmet alınamadığından, çağrısı <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> null değerini döndürür. Hizmeti isteyerek her zaman null için test etmelisiniz:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Bir hizmette sorun gidermek için  
  
1. Hizmetin doğru şekilde kaydedilip kaydedilmediğini görmek için sistem kayıt defterini inceleyin. Daha fazla bilgi için bkz. [Hizmetleri kaydetme](../misc/registering-services.md).  
  
     Aşağıdaki. reg dosya parçasında SVsTextManager hizmetinin nasıl kaydedildiği gösterilmektedir:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     Yukarıdaki örnekte, sürüm numarası 12,0 veya 14,0 gibi bir sürümüdür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , {F5E7E71D-1401-11D1-883B-0000F87579D2} anahtarı hizmetin hizmet tanımlayıcısıdır (SID), SVsTextManager ve varsayılan değer olan {F5E7E720-1401-11D1-883B-0000F87579D2}, hizmet sağlayan VSPackage 'ın paket GUID 'sidir.  
  
2. GetService 'i çağırdığınızda arabirim türünü değil hizmet türünü kullanın. İçinden bir hizmet istendiğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , <xref:Microsoft.VisualStudio.Shell.Package> GUID 'yi türden ayıklar. Aşağıdaki koşullar mevcutsa bir hizmet bulunamayacak:  
  
    1. Bir arabirim türü, hizmet türü yerine GetService 'e geçirilir.  
  
    2. Arabirime açıkça bir GUID atanmaz. Bu nedenle, sistem gerektiğinde bir nesne için varsayılan bir GUID oluşturur.  
  
3. Hizmeti isteyen VSPackage 'ın kaldırılmış olduğundan emin olun. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] siteleri oluşturduktan sonra ve çağrılmadan önce bir VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
     Bir hizmet gerektiren VSPackage oluşturucusunda kodunuz varsa Initialize yöntemine taşıyın.  
  
4. Doğru hizmet sağlayıcısını kullandığınızdan emin olun.  
  
     Hizmet sağlayıcılarının hepsi benzer değildir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bir araç penceresine geçen hizmet sağlayıcısı, VSPackage 'a geçen olandan farklıdır. Araç penceresi hizmet sağlayıcısı hakkında bilir <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> , ancak hakkında bilgi vermez <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Bir <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> araç penceresi Içinden VSPackage hizmeti sağlayıcısı almak için çağırabilirsiniz.  
  
     Bir araç penceresi bir kullanıcı denetimi veya başka bir denetim kapsayıcısı barındırıyorsa, kapsayıcı Windows bileşen modeli tarafından kaldırılır ve hiçbir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hizmete erişemez. <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>Bir denetim kapsayıcısının Içinden VSPackage hizmeti sağlayıcısı almak için çağırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanılabilir Hizmetler listesi](../extensibility/internals/list-of-available-services.md)   
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Hizmet Temel Bileşenleri](../extensibility/internals/service-essentials.md)
