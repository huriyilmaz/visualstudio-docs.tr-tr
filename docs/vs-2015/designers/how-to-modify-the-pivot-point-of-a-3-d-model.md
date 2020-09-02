---
title: 'Nasıl yapılır: 3B modelin pivot noktasını değiştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: baeae2af825edc6a0032445288de7311b1ab1ae1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664399"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Nasıl Yapılır: 3B Modelin Pivot Noktasını Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede, 3B modelin *pivot noktasını* değiştirmek Için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilir. Özet noktası, döndürme ve ölçekleme için nesnenin matematik merkezini tanımlayan yer alan noktasıdır.

 Bu belgede bu etkinlik gösterilmektedir:

- Bir nesnenin Özet noktasını değiştirme

## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>3B modelin pivot noktasını değiştirme
 Özet noktasını değiştirerek 3B modelin kaynağını yeniden tanımlayabilirsiniz.

 **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>3B modelin pivot noktasını değiştirmek için

1. [Nasıl yapılır: temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)bölümünde açıklananlar gibi var olan bir 3-b modeliyle başlayın.

2. Özet moduna girin. **Model Düzenleyicisi Modu** araç çubuğunda Özet modunu etkinleştirmek Için **Pivot modu** düğmesini seçin. Model düzenleyicisinin şimdi Pivot modunda olduğunu göstermek için **Pivot modu** düğmesinin etrafında bir kutu belirir. Özet modunda, çeviri gibi işlemler, nesnenin, dünya alanındaki yapısı yerine Özet noktasını etkiler.

3. Nesnenin pivot noktasını değiştirin. **Seç** modunda, nesneyi seçin ve ardından **Model Görüntüleyicisi** araç çubuğunda **çevir** aracını seçin. Tasarım yüzeyinde Özet noktasını temsil eden bir kutu görüntülenir. Nesnenin Özet noktasını değiştirmek için kutuyu taşıyın.

    Kutuyu taşıyarak Özet noktasını üç boyutun tümünde taşıyabilirsiniz. Özet noktasını bir eksen üzerinde çevirmek için, bu eksene karşılık gelen oku taşıyın. Kutu ve oklar, çevirinin etkilediği ekseni göstermek için sarı renge değişir.

    Ayrıca, **Özellikler** penceresindeki **Pivot çevirisi** özelliğini kullanarak da Özet noktası belirtebilirsiniz.

   > [!TIP]
   > Nesneyi döndürerek yeni Özet noktasının etkisini görüntüleyebilirsiniz. Döndürmek için, **döndürme** aracını kullanın veya **döndürme** özelliğini değiştirin.

   Değiştirilmiş bir Özet noktası olan bir model aşağıda verilmiştir:

   ![Değiştirilmiş bir Özet noktası olan bir evin modeli](../designers/media/digit-modified-model.png "Basamak-değiştirme modeli")

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: temel 3B model](../designers/how-to-create-a-basic-3-d-model.md) [Model Düzenleyicisi](../designers/model-editor.md) oluşturma
