---
title: Varsayılan komut, Grup ve araç çubuğu yerleşimi | Microsoft Docs
description: Visual Studio kullanıcı arabiriminin varsayılan olarak görüntüleyeceği ıde komutları, ürün komutları ve düzenleyici komutları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e431441d4a0ea8a447554b96bc9bf9d5f290110a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063466"
---
# <a name="default-command-group-and-toolbar-placement"></a>Varsayılan komut, Grup ve araç çubuğu yerleşimi
Ürün ve kararlılık için, Kullanıcı arabirimi belirli komut gruplarını varsayılan olarak görüntüler ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komutlar ve komut grupları için tanımlar sağlar. VSPackages, standart komutları ve komut gruplarını da kullanabilir.

 Varsayılan komut grupları üç kategoriye ayrılır: IDE komutları, ürün komutları ve düzenleyici komutları.

## <a name="default-ide-commands"></a>Varsayılan IDE komutları
 Varsayılan IDE araç çubuğu, içinde bulunan tüm ürünler tarafından paylaşılan komutları içerir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bunlar, **Kaydet** komutu ve **öğe Ekle** komutu gibi genel proje işlemleriyle ilgili komutları içerir. VSPackages, tek bir özel durumla birlikte bu araç çubuğuna eklemez veya çıkarmamalıdır: ürün veya VSPackage yeni bir araç penceresi eklerse, pencere **Görünüm** menüsünde kullanılabilir araç pencereleri listesine eklenmelidir. Yeni ürünler veya VSPackages kendi araç çubuklarını ekleyebilir.

## <a name="default-product-commands"></a>Varsayılan ürün komutları
 Her ürün, IDE 'yi önemli ve sık kullanılan komutları içeren kendi varsayılan araç çubuğuyla sağlayabilir. Bununla birlikte, mümkün olan her durumda var olan menüleri ve araç çubuklarını kullanmak ve gerektiğinde diğer görevlere özgü araç çubuklarıyla birlikte kullanmak en iyisidir.

 Bir araç çubuğunun öncelik alanı, satır yerleşimini belirler. Sıfır öncelik araç çubuğunu, menü çubuğunun (satır 1) ve **Standart** araç çubuğunun (satır 2) altındaki üçüncü satıra (satır 3) koyar. Bu nedenle, diğer araç çubukları satırda görünür (öncelik + 3). Sonraki araç çubukları, oda varsa aynı satıra yerleştirilir; Aksi takdirde, otomatik olarak bir sonraki satıra taşınır.

## <a name="default-editor-commands"></a>Varsayılan düzenleyici komutları
 Özel bir düzenleyici sağlayan VSPackage, Bu düzenleyicide en önemli ve sık kullanılan komutları içeren varsayılan bir araç çubuğu sağlamalıdır. Düzenleyici etkin olduğunda Düzenleyici araç çubuğu görünmelidir ve düzenleyici etkin olmadığında gizli olmalıdır. Bu görünürlük, `VisibilityConstraints` *. vsct* dosyasının öğesinde denetlenir.

 Düzenleyici araç çubukları IDE ve ürün araç çubuklarının altına yerleştirilmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
