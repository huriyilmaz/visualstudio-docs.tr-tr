---
title: 'Nasıl: Hizmet Sorunlarını | Microsoft Docs'
description: Visual Studio SDK'sı'sinde bir hizmet almaya çalışabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d84e178f8dd3c7006dd3213fdb60eea9b96dac24
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124860"
---
# <a name="how-to-troubleshoot-services"></a>Nasıl yapılanlar: Hizmet sorunlarını giderme
Hizmet almaya çalışabilirsiniz bazı yaygın sorunlar vardır:

- Hizmet ile kayıtlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] değil.

- Hizmet, hizmet türüne göre değil arabirim türüne göre istenmektedir.

- Hizmeti talep alan VSPackage sited değil.

- Yanlış hizmet sağlayıcısı kullanılıyor.

  İstenen hizmet alınamazsa çağrısı <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> null döndürür. Hizmet isteği verdikten sonra her zaman null değerini test etmek gerekir:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Hizmet sorunlarını gidermek için

1. Hizmetin doğru şekilde kaydedilmiş olup olmadığını görmek için sistem kayıt defterini inceleme. Daha fazla bilgi için, [bkz. How to: Provide a service](../extensibility/how-to-provide-a-service.md).

    Aşağıdaki *.reg dosya* parçası, SVsTextManager hizmetinin nasıl kaydedil olabileceğini gösterir:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Yukarıdaki örnekte sürüm numarası sürümüdür; [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] örneğin, 12.0 veya 14.0, {F5E7E71D-1401-11d1-883B-0000F87579D2} anahtarı hizmetin hizmet tanımlayıcısıdır (SID), SVsTextManager ve varsayılan değer {F5E7E720-1401-11d1-883B-0000F87579D2} metin yöneticisi VSPackage'ın hizmet sağlayan paket GUID'idir.

2. GetService çağrısında arabirim türünü değil hizmet türünü kullanın. 'den bir hizmet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] isteğite <xref:Microsoft.VisualStudio.Shell.Package> bulundurarak TÜRÜNDEn GUID'i ayıklar. Aşağıdaki koşullar varsa bir hizmet bulunmayacak:

   1. Arabirim türü, hizmet türü yerine GetService'e geçirildi.

   2. Arabirime açıkça bir GUID atanmamış. Bu nedenle, sistem gerektiğinde bir nesne için varsayılan bir GUID oluşturur.

3. Hizmeti talep alan VSPackage'ın siteli olduğundan emin olun. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , bir VSPackage'ı oluşturmadan ve çağırmadan önce sitelerine <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yerleştirmektedir.

    VSPackage oluşturucus unda bir hizmete ihtiyaç olan kodunuz varsa, bunu yöntemine `Initialize` taşımanız gerekir.

4. Doğru hizmet sağlayıcısını kullanırkenn emin olun.

    Tüm hizmet sağlayıcıları aynı değildir. Araç [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] penceresine geçen hizmet sağlayıcısı, VSPackage'a geçtiğinden farklıdır. Araç penceresi hizmet sağlayıcısı, <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> hakkında bilgi edindi ancak hakkında bilgisi <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> yok. <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>VsPackage hizmet sağlayıcısını bir araç penceresinden almak için çağrısı alabilirsiniz.

    Bir araç penceresi bir kullanıcı denetimi veya başka bir denetim kapsayıcısı barındırırsa, kapsayıcı, Windows bileşen modeli tarafından sitelir ve hiçbir hizmet erişimine sahip [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olmaz. <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>VsPackage hizmet sağlayıcısını bir denetim kapsayıcısı içinde almak için çağrısı alabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanılabilir hizmetlerin listesi](../extensibility/internals/list-of-available-services.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
- [Hizmet temelleri](../extensibility/internals/service-essentials.md)
- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)