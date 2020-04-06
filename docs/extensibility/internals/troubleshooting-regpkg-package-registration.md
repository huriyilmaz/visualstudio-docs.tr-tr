---
title: Sorun Giderme RegPkg Paket Kaydı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704325"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg Paket Kaydı Sorunlarını Giderme
> [!NOTE]
> Visual Studio'da paketleri kaydetmenin tercih edilen yolu .pkgdef dosyalarını kullanmaktır. Bu, sistem kayıt defterine erişmek zorunda kalmadan uzatma dağıtımına olanak tanır. Pkgdef dosyaları [CreatePkgDef Yardımcı Programı](../../extensibility/internals/createpkgdef-utility.md)kullanılarak oluşturulur.

 RegPkg kullanarak bir paketi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kaydetmek için, paketiniz için uygun olan RegPkg sürümünü kullanmanız gerekir.

## <a name="regpkg-versions-related-to-package-versions"></a>Paket Sürümlere İlişkin RegPkg Versiyonları
 RegPkg'ın iki versiyonu vardır. Bir sürüm ' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de yer alan . Aşağıdaki derlemelerden birini kullanarak oluşturulmuş paketleri kaydetmek için bu sürümü kullanın:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Önceki Microsoft.VisualStudio.Shell.dll derlemesi kullanılarak oluşturulmuş paketleri kaydedemez.

   RegPkg'ın önceki sürümü, Microsoft.VisualStudio.Shell.dll derlemesi kullanılarak oluşturulmuş paketleri kaydedebilir. Ancak, bu derlemenin sonraki sürümlerini kullanarak oluşturulmuş paketleri kaydedemez.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)
