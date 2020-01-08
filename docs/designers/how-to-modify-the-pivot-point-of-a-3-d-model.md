---
title: 'Nasıl yapılır: 3B modelin pivot noktasını değiştirme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 114beda700359eb5cdbfd4db12c18e442b8894f2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589948"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Nasıl yapılır: 3B modelin pivot noktasını değiştirme

Bu makalede, bir 3B modelin *pivot noktasını* değiştirmek Için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilir. Özet noktası, döndürme ve ölçekleme için nesnenin matematik merkezini tanımlayan yer alan noktasıdır.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>3B modelin pivot noktasını değiştirme

Bir 3B modelin kaynağını, Özet noktasını değiştirerek yeniden tanımlayabilirsiniz.

**Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

1. [Nasıl yapılır: temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)bölümünde açıklananlar gibi mevcut bir 3B modeliyle başlayın.

2. Özet moduna girin. **Model Düzenleyicisi Modu** araç çubuğunda Özet modunu etkinleştirmek Için **Pivot modu** düğmesini seçin. Model düzenleyicisinin şimdi Pivot modunda olduğunu göstermek için **Pivot modu** düğmesinin etrafında bir kutu belirir. Özet modunda, çeviri gibi işlemler, nesnenin, dünya alanındaki yapısı yerine Özet noktasını etkiler.

3. Nesnenin pivot noktasını değiştirin. **Seç** modunda, nesneyi seçin ve ardından **Model Görüntüleyicisi** araç çubuğunda **çevir** aracını seçin. Tasarım yüzeyinde Özet noktasını temsil eden bir kutu görüntülenir. Nesnenin Özet noktasını değiştirmek için kutuyu taşıyın.

     Kutuyu taşıyarak Özet noktasını üç boyutun tümünde taşıyabilirsiniz. Özet noktasını bir eksen üzerinde çevirmek için, bu eksene karşılık gelen oku taşıyın. Kutu ve oklar, çevirinin etkilediği ekseni göstermek için sarı renge değişir.

     Ayrıca, **Özellikler** penceresindeki **Pivot çevirisi** özelliğini kullanarak da Özet noktası belirtebilirsiniz.

    > [!TIP]
    > Nesneyi döndürerek yeni Özet noktasının etkisini görüntüleyebilirsiniz. Döndürmek için, **döndürme** aracını kullanın veya **döndürme** özelliğini değiştirin.

Değiştirilmiş bir Özet noktası olan bir model aşağıda verilmiştir:

![Değiştirilmiş bir Özet noktası olan bir evin modeli](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)
- [Model düzenleyicisi](../designers/model-editor.md)
