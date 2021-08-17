---
title: Visual Studio Aramasını kullanma
description: ayarları, menüleri ve kodu bulmak için Visual Studio aramasını kullanmayı öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 1299810fa015f9e54d418209e13d366ff47bfb33
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048394"
---
# <a name="use-visual-studio-search"></a>Visual Studio arama kullan

Visual Studio tümleşik geliştirme ortamı (ıde), anımsanması zor olabilecek birçok menü, seçenek ve özelliğe sahiptir. Visual Studio arama özelliği, geliştiricilerin ıde menülerini ve seçeneklerini bulmasına yardımcı olan tek bir arama kutusudur ve ayrıca kodunuzda arama yapmanıza yardımcı olur. Visual Studio veya deneyimli bir geliştirici için yeni bir özelliktir, bu özellik ıde özellikleri ve kodunuz arasında arama yapmanın hızlı bir yolunu sunar.

 + arama kutusuna erişmek için Ctrl **Q** klavye kısayolunu kullanın veya varsayılan olarak menü çubuğunun yanında bulunan Visual Studio arama giriş kutusuna tıklayın:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Visual Studio arama kutusu" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> Visual Studio arama tarafından yürütülen komut, `Window.QuickLaunch` bu özelliğin hızlı arama veya hızlı başlatma olarak adlandırılmasından daha fazla bilgi alabilirsiniz.

dosyalarda bul veya arama Çözüm Gezgini gibi diğer arama özelliklerinden farklı olarak, Visual Studio sonuçlarında arama yapın ıde özellikleri, menü seçenekleri, dosya adları ve daha fazlasını içerir. aşağıdaki bölümler, Visual Studio aramanın bulabileceği farklı sonuç türlerini tartışır.

## <a name="search-menus-options-and-windows"></a>Menülerde, seçeneklerde ve Windows 'ta arama yapın

ayarları, seçenekleri ve benzer yapılandırma öğelerini bulmak için Visual Studio arama kutusunu kullanabilirsiniz. örneğin, aşağıdaki ekran görüntüsünde gösterildiği gibi Visual Studio color temasını değiştirmenize olanak sağlayan iletişim kutusunu hızlıca bulup açmak için *değişiklik temasını* arayın:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="arama Visual Studio ayarları ve seçenekleri":::

> [!TIP]
> çoğu durumda Visual Studio arama, sonuçlarda her öğenin menü, kısayol tuşu ve konumunu da hatırlatacaktır.

menü öğelerini ve komutları bulmak için Visual Studio arama kutusunu kullanabilirsiniz. Örneğin, Clean Solution komutunu hızlıca bulup yürütmek için *Clean Nuevo* araması yapın. Arama sonuçları Ayrıca, aşağıdaki ekran görüntüsünde gösterildiği gibi menülerde bu komutun nerede bulunacağı hakkında bir anımsatıcı sunar:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Visual Studio menü öğelerini ve komutları arayın":::

Son olarak, yanlışlıkla kapattığınız Windows veya panellerde arama yapabilirsiniz. Örneğin, test Gezgini penceresini bulmak ve açmak için *Test* araması yapın:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Visual Studio pencereleri ve panelleri arayın":::

## <a name="search-files-and-code"></a>Dosya ve kod ara

Visual Studio arama, çözüm öğelerinizi dosya adı, kod, yöntem ve diğer eşleşmeler için de arar. Aşağıdaki ekran görüntüsünde *markaşağı* araması, MarkdownMetaExtractor. cs dosyasını, `MarkdownMetaExtractor` sınıfını ve çözüm içinde iki yöntemi buldu:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Visual Studio aramayla dosya ara":::

"Camel Case" araması da yapabilirsiniz. Aşağıdaki ekran görüntüsünde, *FSS* araması bir **F** daha eski **s****canner** dosyası, sınıfı ve yöntemi buldu:

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Visual Studio arama ile camel hump araması":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](reference/visual-studio-commands.md)