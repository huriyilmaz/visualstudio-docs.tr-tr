---
title: 'Nasıl: 3D Modelin Pivot Noktasını Değiştirme'
description: Döndürme ve ölçeklendirme için nesnenin merkezini tanımlayan nokta olan 3B modelin pivot noktasını değiştirmek için Model Düzenleyicisi'ni kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 17c02f56d29fbda871cbe74cf156deffbb1908e1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133568"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Nasıl yapılır: 3B modelin pivot noktasını değiştirme

Bu makalede, 3D modelin pivot noktasını değiştirmek için *Model Düzenleyicisi'nin* nasıl kullanılası gösterildi. Pivot noktası, döndürme ve ölçeklendirme için nesnenin matematiksel merkezini tanımlayan boşluk noktasıdır.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>3B modelin pivot noktasını değiştirme

Bir 3D modelin kaynağını yeniden tanımlamak için pivot noktasını değiştirebilirsiniz.

Özellikler penceresinin **ve Araç** Kutusunun **görüntülendiğinden** emin olun.

1. Nasıl 3D modeli oluşturma konusunda açıklanan gibi mevcut [bir 3D modelle başlar.](../designers/how-to-create-a-basic-3-d-model.md)

2. Özet modu girin. Model Düzenleyicisi **Modu araç çubuğunda,** özet **modunu etkinleştirmek için** Özet Modu düğmesini seçin. Model Düzenleyicisi'nin **artık pivot modunda** olduğunu belirtmek için Özet Modu düğmesinin etrafında bir kutu görüntülenir. Özet modunda çeviri gibi işlemler, dünya boşluğundaki nesnenin yapısı yerine nesnenin özet noktasını etkiler.

3. Nesnenin özet noktasını değiştirme. Seçim **modu'nda** nesneyi seçin ve ardından Model **Görüntüleyicisi** araç çubuğunda Çevir **aracını** seçin. Tasarım yüzeyinde pivot noktasını temsil eden bir kutu görünür. Nesnenin pivot noktasını değiştirmek için kutuyu hareket ettirin.

     Kutuyu hareket ettirerek özet noktasını üç boyutta da hareket ettirebilirsiniz. Bir eksende pivot noktasını çevirmek için bu eksene karşılık gelen oku hareket ettirin. Kutu ve oklar, çeviriden etkilenen ekseni göstermek için sarı renge döner.

     Özet noktasını Özellikler penceresindeki Özet Çeviri **özelliğini** kullanarak da **belirtebilirsiniz.**

    > [!TIP]
    > Nesneyi döndürerek yeni pivot noktasının etkisini görüntüebilirsiniz. Döndürmek için Döndür aracını **kullanın** veya **Rotation özelliğini değiştirme.**

Değiştirilmiş bir pivot noktası olan bir model şu şekildedir:

![Değiştirilmiş bir pivot noktası olan bir ev modeli](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)
- [Model düzenleyicisi](../designers/model-editor.md)
