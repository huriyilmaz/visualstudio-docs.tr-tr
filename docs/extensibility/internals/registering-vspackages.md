---
title: VSPackages Kayıt | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705740"
---
# <a name="registering-vspackages"></a>VSPackage’ları Kaydetme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]vspackage tanımlamak ve bulmak için .pkgdef dosyalarına güvenir. Bir .pkgdef dosyası, aksi takdirde sistem kayıt defterine eklenecek tüm kayıt bilgilerini içerir. Yönetilen VSPackages kaynak koduna öznitelikleri ekleyerek ve sonra bir .pkgdef dosyası oluşturmak için ortaya çıkan montaj [üzerinde CreatePkgDef Yardımcı Programı](../../extensibility/internals/createpkgdef-utility.md) çalıştırarak kaydedilir.

## <a name="in-this-section"></a>Bu Bölümde
- [VS Kabuğuna VSPackage Dosya Konumunu Belirtme](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 VSPackages için yükleme yolunu açıklar.

- [VSPackage Kaydetme ve Kaydını Kaldırma](../../extensibility/registering-and-unregistering-vspackages.md)

 VSPackage'ın nasıl kaydedilebildiğini açıklar.
