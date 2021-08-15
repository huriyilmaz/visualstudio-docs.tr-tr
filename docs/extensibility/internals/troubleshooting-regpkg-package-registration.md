---
title: RegPkg paket kaydı sorunlarını giderme | Microsoft Docs
description: Visual Studio 'de RegPkg paket kaydı sorunlarını gidermek için bu bilgileri kullanın. Paketinize uygun olan RegPkg sürümünü kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fbefcdd5bbb0193339fab1b91335e16fcc0e820afd97ad35a7d39ee71582ff06
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431766"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg Paket Kaydı Sorunlarını Giderme
> [!NOTE]
> Visual Studio paketleri kaydetmek için tercih edilen yol. pkgdef dosyalarını kullanmaktır. Bu, sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına izin verir. Pkgdef dosyaları [CreatePkgDef yardımcı programı](../../extensibility/internals/createpkgdef-utility.md)kullanılarak oluşturulur.

 İçinde RegPkg kullanarak bir paketi kaydetmek için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , paketinize uygun olan RegPkg sürümünü kullanmanız gerekir.

## <a name="regpkg-versions-related-to-package-versions"></a>Paket sürümleriyle Ilgili RegPkg sürümleri
 İki RegPkg sürümü vardır. Sürümüne bir sürüm dahildir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Aşağıdaki derlemelerden biri kullanılarak oluşturulmuş paketleri kaydetmek için bu sürümü kullanın:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Daha önceki Microsoft.VisualStudio.Shell.dll derlemesi kullanılarak oluşturulmuş paketleri kaydedemez.

   RegPkg 'in önceki sürümü, Microsoft.VisualStudio.Shell.dll derlemesi kullanılarak oluşturulmuş paketleri kaydedebilir. Ancak, bu derlemenin sonraki sürümleri kullanılarak oluşturulan paketleri kaydedemez.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
