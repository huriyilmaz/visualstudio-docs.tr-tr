---
title: Visual Studio Aramasını kullanma
description: Ayarları, menüleri ve kodu bulmak için Visual Studio arama 'yı kullanmayı öğrenin.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 101875b3a600a71c832498d05073187d2cf0b774
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873911"
---
# <a name="use-visual-studio-search"></a>Visual Studio aramasını kullanma

Visual Studio tümleşik geliştirme ortamı (IDE), anımsanması zor olabilecek birçok menü, seçenek ve özelliğe sahiptir. Visual Studio arama özelliği, geliştiricilerin IDE menülerini ve seçeneklerini bulmasına yardımcı olan tek bir arama kutusudur ve ayrıca kodunuzda arama yapın. Visual Studio veya deneyimli bir geliştirici için yeni bir özelliktir, bu özellik IDE özellikleri ve kodunuz arasında arama yapmanın hızlı bir yolunu sunar.

 + Arama kutusuna erişmek için CTRL **Q** klavye kısayolunu kullanın veya varsayılan olarak menü çubuğunun yanında bulunan Visual Studio arama giriş kutusuna tıklayın:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Visual Studio arama kutusu" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Visual Studio Search tarafından yürütülen komut, `Window.QuickLaunch` Bu özelliğin hızlı arama veya hızlı başlatma olarak adlandırılmasından de karşılaşabilirsiniz.

Dosyalarda bul veya arama Çözüm Gezgini gibi diğer arama özelliklerinden farklı olarak, Visual Studio 'da arama yapın IDE özellikleri, menü seçenekleri, dosya adları ve daha fazlasını içerir. Aşağıdaki bölümler, Visual Studio aramasının bulabileceği farklı sonuç türlerini tartışır.

## <a name="search-menus-options-and-windows"></a>Menülerde, seçeneklerde ve Windows 'ta arama yapın

Ayarları, seçenekleri ve benzer yapılandırma öğelerini bulmak için Visual Studio arama kutusunu kullanabilirsiniz. Örneğin, aşağıdaki ekran görüntüsünde gösterildiği gibi Visual Studio Color temasını değiştirmenize olanak sağlayan iletişim kutusunu hızla bulup açmak için *değişiklik temasını* arayın:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Visual Studio ayarları ve seçeneklerinde ara":::

> [!TIP]
> Çoğu durumda, Visual Studio Search, sonuçlarda her öğenin menü, kısayol tuşu ve konumunu da hatırlatacaktır.

Menü öğelerini ve komutları bulmak için Visual Studio arama kutusunu kullanabilirsiniz. Örneğin, Clean Solution komutunu hızlıca bulup yürütmek için *Clean Nuevo* araması yapın. Arama sonuçları Ayrıca, aşağıdaki ekran görüntüsünde gösterildiği gibi menülerde bu komutun nerede bulunacağı hakkında bir anımsatıcı sunar:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Visual Studio menü öğeleri ve komutları ara":::

Son olarak, yanlışlıkla kapattığınız Windows veya panellerde arama yapabilirsiniz. Örneğin, test Gezgini penceresini bulmak ve açmak için *Test* araması yapın:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Visual Studio Windows ve panellerinde ara":::

## <a name="search-files-and-code"></a>Dosya ve kod ara

Visual Studio Search, çözüm öğelerinizi dosya adı, kod, yöntem ve diğer eşleşmeler için de arar. Aşağıdaki ekran görüntüsünde, *markaşağı* araması MarkdownMetaExtractor.cs dosyasını, `MarkdownMetaExtractor` sınıfını ve çözüm içinde iki yöntemi buldu:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Visual Studio Search ile dosyaları arama":::

"Camel Case" araması da yapabilirsiniz. Aşağıdaki ekran görüntüsünde, *FSS* araması bir **F** daha eski **s****canner** dosyası, sınıfı ve yöntemi buldu:

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Visual Studio Search ile Camel Hump arama":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](reference/visual-studio-commands.md)