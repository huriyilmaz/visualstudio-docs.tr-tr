---
title: Visual Studio için Blend özellik turu
titleSuffix: ''
description: XAML tabanlı Windows ve Web uygulamaları tasarlamaya yönelik bir bileşen olan Visual Studio için Blend çalışma alanı kullanıcı arabirimi ve özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: 5d658ac48d2481f414fdef07906275f25b35479c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092026"
---
# <a name="blend-for-visual-studio-overview"></a>Visual Studio için Blend genel bakış

Visual Studio için Blend XAML tabanlı Windows ve Web uygulamaları tasarlamanıza yardımcı olur. Visual Studio ile aynı temel XAML tasarım deneyimini sağlar ve animasyonlar ve davranışlar gibi gelişmiş görevler için görsel tasarımcılar ekler. Blend ve Visual Studio arasında bir karşılaştırma için, bkz. [Visual Studio ve Visual Studio için Blend XAML tasarımı](../xaml-tools/designing-xaml-in-visual-studio.md).

Visual Studio için Blend, Visual Studio bir bileşenidir. Blend 'yi yüklemek için **Visual Studio Yükleyicisi** **Evrensel Windows Platformu geliştirme** veya **.net masaüstü geliştirme** iş yükünü seçin. bu iş yüklerinin her ikisi de Visual Studio için Blend bileşeni içerir.

![UWP iş yükü bileşenleri](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET masaüstü geliştirme iş yükü bileşenleri](media/installer-dotnet-desktop.png)

Visual Studio için Blend yeni başladıysanız, çalışma alanının benzersiz özellikleri hakkında bilgi sahibi olmak için biraz zaman ayırın. Bu konu, sizi hızlı bir tura götürür.

## <a name="tools-panel"></a>Araçlar paneli

uygulamanızdaki nesneleri oluşturmak ve değiştirmek için Visual Studio için Blend **araçlar** panelini kullanabilirsiniz. **Araçlar** paneli, bir *. xaml* dosyanız açık olduğunda xaml tasarımcısının sol tarafında görünür.

Nesneleri bir araç seçip çalışma yüzeyinde farenizle çizerek bir araç seçerek oluşturursunuz.

![Visual Studio için Blend araçlar paneli](media/blend-tools-panel.png)

> [!TIP]
> **Araçlar** panelindeki araçlardan bazılarının çeşitleri vardır. Örneğin, dikdörtgen yerine bir elips veya çizgi seçebilirsiniz. Bu farklılıklara erişmek için, araç üzerinde sağ tıklayın veya tıklayın ve basılı tutun.
>
> ![Visual Studio için Blend çeşitlemeleri Şekil aracı](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Seçim araçları

Nesneleri ve yolları seçin. İç içe geçmiş nesneler ve yol kesimleri seçmek için **doğrudan seçim** aracını kullanın.

### <a name="view-tools"></a>Araçları görüntüle

Kaydırma ve yakınlaştırma gibi çalışma yüzeyi görünümünü ayarlayın.

### <a name="brush-tools"></a>Fırça araçları

Bir nesnenin görsel öznitelikleriyle (örneğin, fırçayı dönüştürme veya gradyan uygulama) çalışın.

### <a name="object-tools"></a>Nesne araçları

Çalışma yüzeyinde, yollar, şekiller, düzen bölmeleri, metin ve denetimler gibi en yaygın nesneleri çizin.

### <a name="asset-tools"></a>Varlık araçları

Varlıklar penceresine erişin ve kütüphanedeki en son kullanılan varlığı görüntüleyin.

## <a name="assets-window"></a>Varlıklar penceresi

**Varlıklar** penceresi, tüm kullanılabilir denetimleri içerir ve Visual Studio **araç kutusuna** benzerdir. Denetimlere ek olarak, **varlıklar** penceresinde stiller, medya, davranışlar ve efektler dahil olmak üzere çalışma yüzeyinizi ekleyebileceğiniz her şeyi bulabilirsiniz. **Varlıklar** penceresini açmak için varlıklar penceresini **görüntüle**' yi seçin  >   veya **CTRL** + **alt** + **X** tuşuna basın.

![Visual Studio için Blend varlıklar penceresi](media/blend-assets-window.png)

- Varlık listesini filtrelemek için **varlıkları ara** kutusuna metin girin.
- Sağ üstteki düğmeleri kullanarak, varlıkların kılavuz modu ve liste modu görünümü görünümü arasında geçiş yapın.

## <a name="objects-and-timeline-window"></a>Nesneler ve Zaman Çizelgesi penceresi

Çalışma yüzeyinizdeki nesneleri düzenlemek ve isterseniz bunlara animasyon uygulamak için bu pencereyi kullanın. **Nesneler ve zaman çizelgesi** penceresini açmak için   >  **belge anahattını** görüntüle ' yi seçin. Visual Studio 'daki [belge anahattı penceresinde](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) sunulan işlevlere ek olarak, Visual Studio için Blend Nesneler ve Zaman Çizelgesi penceresinin sağ tarafta bir zaman çizelgesi bileşim alanı vardır. Animasyonları oluştururken ve düzenlediğinizde zaman çizelgesini kullanın.

![Animasyon modundaki nesne ve zaman çizelgesi penceresi](media/storyboard-timeline.png)

Görsel taslağa ilişkili düğmeleri kullanma ![Visual Studio için Blend film şeridi düğmeleri](media/storyboard-buttons.png) Film şeridi oluşturmak, silmek, kapatmak veya seçmek için. Zaman çizelgesini görüntülemek ve ana kareleri taşımak için sağdaki zaman çizelgesi bileşim alanını kullanın.

Kullanılabilir işlevsellik hakkında daha fazla bilgi edinmek için penceredeki her bir düğmenin üzerine gelin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere animasyon ekleme](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Şekiller ve yollar çizin](../xaml-tools/draw-shapes-and-paths.md)
- [Visual Studio ve Visual Studio İçin Blend Uygulamalarında XAML Tasarlama](../xaml-tools/designing-xaml-in-visual-studio.md)
