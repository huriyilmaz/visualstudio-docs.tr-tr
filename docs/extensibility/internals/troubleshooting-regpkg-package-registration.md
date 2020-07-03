---
title: RegPkg paket kaydı sorunlarını giderme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65acd78ef2591a84a1f48bd6a694996f48078d68
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905129"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg Paket Kaydı Sorunlarını Giderme
> [!NOTE]
> Visual Studio 'da paketleri kaydetmek için tercih edilen yol. pkgdef dosyalarını kullanmaktır. Bu, sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına izin verir. Pkgdef dosyaları [CreatePkgDef yardımcı programı](../../extensibility/internals/createpkgdef-utility.md)kullanılarak oluşturulur.

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
