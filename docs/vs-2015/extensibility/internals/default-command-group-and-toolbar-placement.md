---
title: Varsayılan komut, Grup ve araç çubuğu yerleşimi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7fc877332f7db7b27c4a30c23f1ac395a4fc22e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196891"
---
# <a name="default-command-group-and-toolbar-placement"></a>Varsayılan Komut, Grup ve Araç Çubuğu Yerleşimi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ürün ve kararlılık için, Kullanıcı arabirimi belirli komut gruplarını varsayılan olarak görüntüler ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Komutlar ve komut grupları için tanımlar sağlar. VSPackages, standart komutları ve komut gruplarını da kullanabilir.  
  
 Varsayılan komut grupları üç kategoriye ayrılır: IDE komutları, ürün komutları ve düzenleyici komutları.  
  
## <a name="default-ide-commands"></a>Varsayılan IDE komutları  
 Varsayılan IDE araç çubuğu, içinde bulunan tüm ürünler tarafından paylaşılan komutları içerir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bunlar, **Kaydet** komutu ve **öğe Ekle** komutu gibi genel proje işlemleriyle ilgili komutları içerir. VSPackages, tek bir özel durumla birlikte bu araç çubuğuna eklemez veya çıkarmamalıdır: ürün veya VSPackage yeni bir araç penceresi eklerse, pencere **Görünüm** menüsünde kullanılabilir araç pencereleri listesine eklenmelidir. Yeni ürünler veya VSPackages kendi araç çubuklarını ekleyebilir.  
  
## <a name="default-product-commands"></a>Varsayılan ürün komutları  
 Her ürün, IDE 'yi önemli ve sık kullanılan komutları içeren kendi varsayılan araç çubuğuyla sağlayabilir. Bununla birlikte, mümkün olan her durumda var olan menüleri ve araç çubuklarını kullanmak ve gerektiğinde diğer görevlere özgü araç çubuklarıyla birlikte kullanmak en iyisidir.  
  
 Bir araç çubuğunun öncelik alanı, satır yerleşimini belirler. Sıfır öncelik araç çubuğunu, menü çubuğunun (satır 1) ve **Standart** araç çubuğunun (satır 2) altındaki üçüncü satıra (satır 3) koyar. Bu nedenle, diğer araç çubukları satırda görünür (öncelik + 3). Sonraki araç çubukları, oda varsa aynı satıra yerleştirilir; Aksi takdirde, otomatik olarak bir sonraki satıra taşınır.  
  
## <a name="default-editor-commands"></a>Varsayılan düzenleyici komutları  
 Özel bir düzenleyici sağlayan VSPackage, Bu düzenleyicide en önemli ve sık kullanılan komutları içeren varsayılan bir araç çubuğu sağlamalıdır. Düzenleyici etkin olduğunda Düzenleyici araç çubuğu görünmelidir ve düzenleyici etkin olmadığında gizli olmalıdır. Bu görünürlük, `VisibilityConstraints Element` . vsct dosyasının içinde denetlenir.  
  
 Düzenleyici araç çubukları IDE ve ürün araç çubuklarının altına yerleştirilmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
