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
ms.openlocfilehash: 103e04bbfb32000e5e3a533988e6727f4323fcda
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124535"
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
