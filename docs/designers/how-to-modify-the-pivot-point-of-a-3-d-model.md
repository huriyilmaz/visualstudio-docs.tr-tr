---
title: 'Nasıl yapilir: 3B Modelin Pivot Noktasını Değiştirme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 114beda700359eb5cdbfd4db12c18e442b8894f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589948"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Nasıl yapılır: 3B modelin pivot noktasını değiştirme

Bu makalede, model in pivot *noktasını* değiştirmek için Model Düzenleyicisi'nin nasıl kullanılacağı gösterin. Pivot noktası döndürme ve ölçekleme için nesnenin matematiksel merkezini tanımlayan boşluk noktasıdır.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>3B modelin pivot noktasını değiştirme

Bir 3B modelin kaynağını, pivot noktasını değiştirerek yeniden tanımlayabilirsiniz.

**Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

1. Nasıl açıklanmıştır gibi varolan bir 3B model ile [başlayın: Temel bir 3B model oluşturun.](../designers/how-to-create-a-basic-3-d-model.md)

2. Pivot moduna girin. Model **Düzenleyici Modu** araç çubuğunda, pivot modunu etkinleştirmek için **Pivot Modu** düğmesini seçin. Model Düzenleyicisi'nin artık pivot modunda olduğunu belirtmek için **Pivot Mode** düğmesinin etrafında bir kutu görüntülenir. Pivot modunda, çeviri gibi işlemler nesnenin dünya-uzaydaki yapısı yerine nesnenin pivot noktasını etkiler.

3. Nesnenin pivot noktasını değiştirin. **Select** modunda nesneyi seçin ve ardından **Model Görüntüleyici** araç çubuğunda **Çevir** aracını seçin. Tasarım yüzeyinde pivot noktasını temsil eden bir kutu görünür. Nesnenin pivot noktasını değiştirmek için kutuyu taşıyın.

     Kutuyu hareket ettirerek, pivot noktasını her üç boyutta da taşıyabilirsiniz. Pivot noktasını bir eksen boyunca çevirmek için, bu eksene karşılık gelen oku taşıyın. Kutu ve oklar, çeviriden etkilenen ekseni belirtmek için sarı renge dönüşür.

     **Özellikler** penceresinde ki **Pivot Çeviri** özelliğini kullanarak pivot noktasını da belirtebilirsiniz.

    > [!TIP]
    > Nesneyi döndürerek yeni pivot noktasının etkisini görüntüleyebilirsiniz. Döndürmek için **Döndürme** aracını kullanın veya **Döndürme** özelliğini değiştirin.

Değiştirilmiş bir özet noktası olan bir model aşağıda veda edilmiştir:

![Değiştirilmiş bir pivot noktası olan bir evin modeli](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)
- [Model düzenleyici](../designers/model-editor.md)
