---
title: 'Nasıl yapılsın: Sorunları Giderme Hizmetleri | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710743"
---
# <a name="how-to-troubleshoot-services"></a>Nasıl yapilir: Hizmetleri sorun giderme
Bir hizmet almaya çalıştığınızda oluşabilecek birkaç yaygın sorun vardır:

- Hizmet kayıtlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]değil.

- Hizmet, hizmet türüne göre değil, arabirim türüne göre istenir.

- Hizmeti isteyen VSPackage sitede kullanılmadı.

- Yanlış servis sağlayıcı kullanılır.

  İstenen hizmet alınamıyorsa, çağrı <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> geçersiz olur. Bir hizmet istedikten sonra her zaman null için test etmeniz gerekir:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Bir hizmeti sorun giderme

1. Hizmetin doğru kaydedilip kaydedilmediğini görmek için sistem kayıt defterini inceleyin. Daha fazla bilgi için [bkz: Bir hizmet sağlayın.](../extensibility/how-to-provide-a-service.md)

    Aşağıdaki *.reg* dosyası parçası, SVsTextManager hizmetinin nasıl kaydedilebileceğini gösterir:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Yukarıdaki örnekte, sürüm numarası [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 12.0 veya 14.0 gibi sürümü, anahtar {F5E7E71D-1401-11d1-883B-0000F87579D2} hizmet tanımlayıcısı (SID) olduğunu, SVsTextManager ve varsayılan değer {F5E7E720-1401-11d1-883B-0000F87579D2} hizmet sağlayan metin yöneticisi VSPackage paketi GUID olduğunu.

2. GetService'i aradiğinizde arabirim türünü değil, hizmet türünü kullanın. Bir hizmet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]isteğinde, <xref:Microsoft.VisualStudio.Shell.Package> GUID türünden ayıklar. Aşağıdaki koşullar varsa bir hizmet bulunamaz:

   1. Hizmet türü yerine GetService'e bir arabirim türü geçirilir.

   2. Arabirime açıkça guid atanmamış. Bu nedenle, sistem gerektiği gibi bir nesne için varsayılan bir GUID oluşturur.

3. Hizmeti isteyen VSPackage'ın siteye eklendiğini unutmayın. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]siteleri bir VSPackage inşa ettikten <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>sonra ve aramadan önce .

    Bir hizmete ihtiyaç olan bir VSPackage oluşturucunuzda `Initialize` kod varsa, yönteme taşıyın.

4. Doğru servis sağlayıcısını kullandığınızdan emin olun.

    Tüm hizmet sağlayıcılar birbirine benzemez. Bir araç [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] penceresine geçen servis sağlayıcısı, vspackage'a geçtiğinden farklıdır. Araç penceresi servis sağlayıcısı, ancak hakkında <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>bilmiyor . Bir araç <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> penceresi içinden bir VSPackage servis sağlayıcısı almak için arayabilirsiniz.

    Bir araç penceresi bir kullanıcı denetimi veya başka bir denetim kapsayıcısı barındırıyorsa, kapsayıcı Windows [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bileşen modeli tarafından siteye dizilecek ve herhangi bir hizmete erişimi olmaz. Bir kontrol <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> konteyneri içinden bir VSPackage servis sağlayıcısı almak için arayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanılabilir hizmetlerin listesi](../extensibility/internals/list-of-available-services.md)
- [Kullanım ve hizmet sağlama](../extensibility/using-and-providing-services.md)
- [Hizmet esasları](../extensibility/internals/service-essentials.md)
