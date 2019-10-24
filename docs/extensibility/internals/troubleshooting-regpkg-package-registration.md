---
title: RegPkg paket kaydı sorunlarını giderme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 386a1a17c036207d122e4b3c7cb142a628dcfe38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722273"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg Paket Kaydı Sorunlarını Giderme
> [!NOTE]
> Visual Studio 'da paketleri kaydetmek için tercih edilen yol. pkgdef dosyalarını kullanmaktır. Bu, sistem kayıt defterine erişmek zorunda kalmadan uzantı dağıtımına izin verir. Pkgdef dosyaları [CreatePkgDef yardımcı programı](../../extensibility/internals/createpkgdef-utility.md)kullanılarak oluşturulur.

 @No__t_0 'de RegPkg kullanarak bir paketi kaydetmek için, paketinize uygun olan RegPkg sürümünü kullanmanız gerekir.

## <a name="regpkg-versions-related-to-package-versions"></a>Paket sürümleriyle Ilgili RegPkg sürümleri
 İki RegPkg sürümü vardır. @No__t_0 bir sürüm bulunmaktadır. Aşağıdaki derlemelerden biri kullanılarak oluşturulmuş paketleri kaydetmek için bu sürümü kullanın:

1. Microsoft. VisualStudioShell. 9.0. dll

2. Microsoft. VisualStudioShell. 10.0. dll

3. Microsoft. VisualStudioShell. 11.0. dll

   Daha önceki Microsoft. VisualStudio. Shell. dll derlemesi kullanılarak oluşturulmuş paketleri kaydedemez.

   RegPkg 'in önceki sürümü, Microsoft. VisualStudio. Shell. dll derlemesi kullanılarak oluşturulmuş paketleri kaydedebilir. Ancak, bu derlemenin sonraki sürümleri kullanılarak oluşturulan paketleri kaydedemez.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)