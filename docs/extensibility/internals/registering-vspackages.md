---
title: VSPackage'ları | Microsoft Docs
description: .pkgdef dosyası, aksi takdirde sistem kayıt defterine eklenecek bilgiler içerir. Bir VSPackage Visual Studio tanımlamak/bulmak için .pkgdef dosyalarını nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b8f4f56bd2f033501e8482fbd813aa72e1cb2bf9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062881"
---
# <a name="registering-vspackages"></a>VSPackage’ları Kaydetme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir VSPackage'ı tanımlamak ve bulmak için .pkgdef dosyalarını kullanır. .pkgdef dosyası, aksi takdirde sistem kayıt defterine eklenecek tüm kayıt bilgilerini içerir. Yönetilen VSPackage'lar, kaynak koda öznitelikler eklip ardından bir .pkgdef dosyası oluşturmak için sonuçta elde edilen derlemede [CreatePkgDef Yardımcı](../../extensibility/internals/createpkgdef-utility.md) Programı çalıştırarak kaydedilir.

## <a name="in-this-section"></a>Bu Bölümde
- [VS Kabuğuna VSPackage Dosya Konumunu Belirtme](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 VSPackage'lar için yükleme yolunu açıklar.

- [VSPackage Kaydetme ve Kaydını Kaldırma](../../extensibility/registering-and-unregistering-vspackages.md)

 VSPackage kaydetmeyi açıklar.
