---
title: Visual Studio özellik turu için Blend
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2b9f38d83befcf49ecd3de8da3a2cd26ff3ab46
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301673"
---
# <a name="blend-for-visual-studio-overview"></a>Visual Studio için Blend genel bakış

Visual Studio için Blend, XAML tabanlı Windows ve Web uygulamaları tasarlamanıza yardımcı olur. Visual Studio ile aynı temel XAML tasarım deneyimini sağlar ve animasyonlar ve davranışlar gibi gelişmiş görevler için görsel tasarımcılar ekler. Blend ve Visual Studio arasında bir karşılaştırma için, [Visual Studio Tasarım XAML ve Visual Studio için Blend](../xaml-tools/designing-xaml-in-visual-studio.md)bakın.

Visual Studio için Blend Visual Studio bir bileşenidir. Blend'i yüklemek için **Visual Studio Installer'da** **Evrensel Windows Platformu geliştirmeyi** veya **.NET masaüstü geliştirme** iş yükünü seçin. Bu iş yüklerinin her ikisi de Visual Studio için Karışım bileşenini içerir.

![UWP iş yükü bileşenleri](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET masaüstü geliştirme iş yükü bileşenleri](media/installer-dotnet-desktop.png)

Visual Studio için Blend'te yeniyseniz, çalışma alanının benzersiz özelliklerini tanımak için bir dakikanızı ayırın. Bu konu hızlı bir tur götürür.

## <a name="tools-panel"></a>Araçlar paneli

Uygulamanızdaki nesneleri oluşturmak ve değiştirmek için Visual Studio için **Karışım'daki Araçlar** panelini kullanabilirsiniz. *.xaml* dosyanız açıkolduğunda **Araçlar** paneli XAML tasarımcısının sol tarafında görünür.

Bir araç seçerek ve fare ile artboard üzerinde çizim nesneleri oluşturun.

![Visual Studio için Blend araçlar paneli](media/blend-tools-panel.png)

> [!TIP]
> **Araçlar** panelindeki bazı araçlarda varyasyonlar vardır, örneğin, dikdörtgen yerine bir elips veya çizgi seçebilirsiniz. Bu varyasyonlara erişmek için, sağ tıklatın veya tıklatın ve aracı basılı tutun.
>
> ![Visual Studio için Blend'teki şekil aracı varyasyonları](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Seçim araçları

Nesneleri ve yolları seçin. İç içe nesneler ve yol segmentleri seçmek için **Doğrudan Seçim** aracını kullanın.

### <a name="view-tools"></a>Araçları görüntüleme

Kaydırma ve yakınlaştırma gibi artboard'un görünümünü ayarlayın.

### <a name="brush-tools"></a>Fırça araçları

Fırçayı dönüştürme veya degrade uygulama gibi bir nesnenin görsel öznitelikleriyle çalışın.

### <a name="object-tools"></a>Nesne araçları

Yollar, şekiller, düzen panelleri, metin ve denetimler gibi en yaygın nesneleri resim tahtasına çizin.

### <a name="asset-tools"></a>Varlık araçları

Varlıklar penceresine erişin ve kitaplıktan en son kullanılan varlığı gösterin.

## <a name="assets-window"></a>Varlıklar penceresi

**Varlıklar** penceresi tüm kullanılabilir denetimleri içerir ve Visual Studio'daki **Araç Kutusu'na** benzer. Denetimlere ek olarak, stiller, ortam, davranışlar ve efektler de dahil olmak üzere **Varlıklar** penceresinde resim panonuza ekleyebileceğiniz her şeyi bulacaksınız. **Varlıklar** penceresini açmak için**Varlıklar Penceresini** **Görüntüle'yi** > seçin veya **Ctrl**+**Alt**+**X**tuşuna basın.

![Visual Studio için Blend Varlıklar penceresi](media/blend-assets-window.png)

- Varlıklar listesini filtrelemek için **Arama Varlıkları** kutusuna metin girin.
- Sağ üstteki düğmeleri kullanarak Varlıkların Grid modu ve Liste modu görünümü arasında geçiş yapın.

## <a name="objects-and-timeline-window"></a>Nesneler ve Zaman Çizelgesi penceresi

Resim tahtanızdaki nesneleri düzenlemek ve isterseniz onları canlandırmak için bu pencereyi kullanın. **Nesneler ve Zaman Çizelgesi** penceresini açmak için Belge**Anahattını** **Görüntüle'yi** > seçin. Visual Studio'daki Belge [Anahat penceresinde](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) sağlanan işlevsellik lere ek olarak, Visual Studio için Karışım'daki Nesneler ve Zaman Çizelgesi penceresinde sağda bir zaman çizelgesi kompozisyon alanı vardır. Animasyonlar oluştururken ve düzenlerken zaman çizelgesini kullanın.

![Animasyon modunda Nesne ve Zaman Çizelgesi penceresi](media/storyboard-timeline.png)

Film şeridiyle ilgili düğmeleri kullanma ![Visual Studio için Blend'te storyboard düğmeleri](media/storyboard-buttons.png) bir film şeridi oluşturmak, silmek, kapatmak veya seçmek için. Zaman çizelgesini görüntülemek ve anahtar kareleri taşımak için sağdaki Zaman Çizelgesi kompozisyonu alanını kullanın.

Kullanılabilir işlevsellik hakkında daha fazla bilgi edinmek için penceredeki her düğmenin üzerine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere animasyon ekleme](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Şekiller ve yollar çizin](../xaml-tools/draw-shapes-and-paths.md)
- [Visual Studio ve Visual Studio İçin Blend Uygulamalarında XAML Tasarlama](../xaml-tools/designing-xaml-in-visual-studio.md)
