---
title: RegPkg Paket Kaydı sorunlarını | Microsoft Docs
description: Bu bilgileri kullanarak Visual Studio'de RegPkg paket kaydıyla ilgili sorunları Visual Studio. Paketiniz için uygun RegPkg sürümünü kullanın.
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
> Paketleri uygulama içinde kaydetmenin tercih Visual Studio .pkgdef dosyalarını kullanmaktır. Bu, sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına olanak sağlar. Pkgdef dosyaları, [CreatePkgDef Yardımcı Programı kullanılarak oluşturulur.](../../extensibility/internals/createpkgdef-utility.md)

 içinde RegPkg kullanarak bir paketi kaydetmek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için paketinize uygun RegPkg sürümünü kullanacaksınız.

## <a name="regpkg-versions-related-to-package-versions"></a>Paket Sürümleriyle İlgili RegPkg Sürümleri
 RegPkg'nin iki sürümü vardır. Bir sürüm içinde yer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] almaktadır. Aşağıdaki derlemelerden biri kullanılarak yapılmış paketleri kaydetmek için bu sürümü kullanın:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Önceki derleme derlemesi kullanılarak Microsoft.VisualStudio.Shell.dll kaydedemektedir.

   RegPkg'nin önceki sürümü, Microsoft.VisualStudio.Shell.dll derlemesi kullanılarak Microsoft.VisualStudio.Shell.dll olabilir. Ancak, bu derlemenin sonraki sürümleri kullanılarak yapılan paketleri kaydedamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
