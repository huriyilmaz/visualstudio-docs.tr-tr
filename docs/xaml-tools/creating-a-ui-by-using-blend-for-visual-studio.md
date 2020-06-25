---
title: Visual Studio için Blend Özellik turu
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8348ba38849b76a745a56f941850d6b61a8f433f
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332089"
---
# <a name="blend-for-visual-studio-overview"></a>Visual Studio için Blend genel bakış

Visual Studio için Blend XAML tabanlı Windows ve Web uygulamaları tasarlamanıza yardımcı olur. Visual Studio ile aynı temel XAML tasarım deneyimini sağlar ve animasyonlar ve davranışlar gibi gelişmiş görevler için görsel tasarımcılar ekler. Blend ve Visual Studio arasında bir karşılaştırma için bkz. [Visual Studio 'DA xaml tasarlama ve Visual Studio için Blend](../xaml-tools/designing-xaml-in-visual-studio.md).

Visual Studio için Blend, Visual Studio 'nun bir bileşenidir. Blend 'yi yüklemek için **Visual Studio Yükleyicisi** **Evrensel Windows platformu geliştirme** veya **.net masaüstü geliştirme** iş yükünü seçin. Bu iş yüklerinin her ikisi de Visual Studio için Blend bileşeni içerir.

![UWP iş yükü bileşenleri](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET masaüstü geliştirme iş yükü bileşenleri](media/installer-dotnet-desktop.png)

Visual Studio için Blend yeni başladıysanız, çalışma alanının benzersiz özellikleri hakkında bilgi sahibi olmak için biraz zaman ayırın. Bu konu, sizi hızlı bir tura götürür.

## <a name="tools-panel"></a>Araçlar paneli

Uygulamanızdaki nesneleri oluşturmak ve değiştirmek için Visual Studio için Blend **Araçlar** panelini kullanabilirsiniz. **Araçlar** paneli, bir *. xaml* dosyanız açık olduğunda xaml tasarımcısının sol tarafında görünür.

Nesneleri bir araç seçip çalışma yüzeyinde farenizle çizerek bir araç seçerek oluşturursunuz.

![Visual Studio için Blend Araçlar paneli](media/blend-tools-panel.png)

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

**Varlıklar** penceresi, tüm kullanılabilir denetimleri Içerir ve Visual Studio 'Daki **araç kutusuna** benzerdir. Denetimlere ek olarak, **varlıklar** penceresinde stiller, medya, davranışlar ve efektler dahil olmak üzere çalışma yüzeyinizi ekleyebileceğiniz her şeyi bulabilirsiniz. **Varlıklar** penceresini açmak için varlıklar penceresini **görüntüle**' yi seçin  >  **Assets Window** veya **CTRL** + **alt** + **X**tuşuna basın.

![Visual Studio için Blend varlıklar penceresi](media/blend-assets-window.png)

- Varlık listesini filtrelemek için **varlıkları ara** kutusuna metin girin.
- Sağ üstteki düğmeleri kullanarak, varlıkların kılavuz modu ve liste modu görünümü görünümü arasında geçiş yapın.

## <a name="objects-and-timeline-window"></a>Nesneler ve Zaman Çizelgesi penceresi

Çalışma yüzeyinizdeki nesneleri düzenlemek ve isterseniz bunlara animasyon uygulamak için bu pencereyi kullanın. **Nesneler ve zaman çizelgesi** penceresini açmak için **View**  >  **belge anahattını**görüntüle ' yi seçin. Visual Studio 'daki [Belge Anahattı penceresinde](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) sunulan işlevlere ek olarak, Visual Studio için Blend nesneler ve zaman çizelgesi pencerenin sağ tarafta bir zaman çizelgesi bileşim alanı vardır. Animasyonları oluştururken ve düzenlediğinizde zaman çizelgesini kullanın.

![Animasyon modundaki nesne ve zaman çizelgesi penceresi](media/storyboard-timeline.png)

Görsel taslağa ilişkili düğmeleri kullanma ![Visual Studio için Blend film şeridi düğmeleri](media/storyboard-buttons.png) Film şeridi oluşturmak, silmek, kapatmak veya seçmek için. Zaman çizelgesini görüntülemek ve ana kareleri taşımak için sağdaki zaman çizelgesi bileşim alanını kullanın.

Kullanılabilir işlevsellik hakkında daha fazla bilgi edinmek için penceredeki her bir düğmenin üzerine gelin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere animasyon ekleme](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Şekiller ve yollar çizin](../xaml-tools/draw-shapes-and-paths.md)
- [Visual Studio ve Visual Studio İçin Blend Uygulamalarında XAML Tasarlama](../xaml-tools/designing-xaml-in-visual-studio.md)
