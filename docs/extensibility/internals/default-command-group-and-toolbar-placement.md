---
title: Varsayılan Komut, Grup ve Araç Çubuğu Yerleştirme | Microsoft Dokümanlar
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708884"
---
# <a name="default-command-group-and-toolbar-placement"></a>Varsayılan komut, grup ve araç çubuğu yerleşimi
Ürün tekdüzeliği ve kararlılık için, Kullanıcı Arabirimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] varsayılan olarak belirli komut gruplarını görüntüler ve komutlar ve komut grupları için tanımlar sağlar. VSPackages standart komutları ve komut gruplarını da kullanabilir.

 Varsayılan komut grupları üç kategoriye ayrılır: IDE komutları, ürün komutları ve düzenleyici komutları.

## <a name="default-ide-commands"></a>Varsayılan IDE komutları
 Varsayılan IDE araç çubuğu, 'de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]yer alan tüm ürünler tarafından paylaşılan komutları içerir. Bunlar, **Kaydet** komutu ve **Madde Ekle** komutu gibi genel proje işlemleriyle ilgili komutları içerir. VSPackages bir istisna dışında bu araç çubuğuna eklememeli veya çıkarmamalıdır: Ürün veya VSPackage yeni bir araç penceresi ekliyorsa, pencere **Görünüm** menüsündeki kullanılabilir araç pencereleri listesine eklenmelidir. Yeni ürünler veya VSPackages kendi araç çubuğu ekleyebilirsiniz.

## <a name="default-product-commands"></a>Varsayılan ürün komutları
 Her ürün, IDE'ye önemli ve sık kullanılan komutları içeren kendi varsayılan araç çubuğunu sağlayabilir. Ancak, varolan menüleri ve araç çubuklarını mümkün olduğunca kullanmak ve gerektiğinde diğer göreve özel araç çubuklarıyla tamamlamak en iyisidir.

 Araç çubuğunun öncelik alanı, satır yerleşimini belirler. Sıfır önceliği araç çubuğunu üçüncü satıra (satır 3), menü çubuğunun (satır 1) ve **Standart** araç çubuğunun (satır 2) altına yerleştirir. Bu nedenle, satırda diğer araç çubukları görünür (öncelik + 3). Sonraki araç çubukları aynı satıra yerleştirilir, eğer yer varsa; aksi takdirde, otomatik olarak bir sonraki satıra taşınır.

## <a name="default-editor-commands"></a>Varsayılan düzenleyici komutları
 Özel bir düzenleyici sağlayan bir VSPackage, bu düzenleyicide en önemli ve sık kullanılan komutları içeren varsayılan bir araç çubuğu sağlamalıdır. Düzenleyici etkinolduğunda düzenleyici araç çubuğu görünmeli ve düzenleyici etkin olmadığında gizlenmelidir. Bu görünürlük `VisibilityConstraints` *.vsct* dosyasının öğesinde denetlenir.

 Düzenleyici araç çubukları IDE ve ürün araç çubuklarının altına yerleştirilmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
