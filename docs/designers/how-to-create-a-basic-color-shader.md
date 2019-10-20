---
title: 'Nasıl Yapılır: Temel Renk Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db97199518d4f7f023696b085d0f66dc81394511
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72636403"
---
# <a name="how-to-create-a-basic-color-shader"></a>Nasıl yapılır: temel renk gölgelendiricisi oluşturma

Bu makalede, bir düz renk gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş Graf gölgelendirici dilinin (DGSL) nasıl kullanılacağı gösterilmektedir. Bu gölgelendirici, son rengi sabit bir RGB renk değerine ayarlar.

## <a name="create-a-flat-color-shader"></a>Düz renk gölgelendiricisi oluşturma

Bir RGB renk sabitinin Color değerini son çıkış rengine yazarak düz bir renk gölgelendiricisi uygulayabilirsiniz.

Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

1. Birlikte çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Nokta rengi** düğümünü silin. **Nokta rengi** düğümünü seçmek için **Seç** aracını kullanın ve ardından menü çubuğunda **Düzenle**  > **Sil**' i seçin.

3. Grafiğe **renkli sabit** bir düğüm ekleyin. **Araç kutusunda** **sabitler**altında **renk sabiti** ' ni seçin ve tasarım yüzeyine taşıyın.

4. **Renk sabiti** düğümü için bir renk değeri belirtin. **Renk sabiti** düğümünü seçmek için **seçim** aracını kullanın ve ardından **Özellikler** penceresinde, **Çıkış** özelliği ' nde bir renk değeri belirtin. Turuncu için bir değer (1,0, 0,5, 0,2, 1,0) belirtin.

5. Renkli sabiti son renge bağlayın. Bağlantıları oluşturmak için, renk sabiti düğümünün **RGB** terminalini **son renk** düğümünün **RGB** **terminaline** taşıyın ve ardından **renk sabiti** düğümünün **Alfa** terminalini **Alpha** 'a taşıyın **son renk** düğümünün terminali. Bu bağlantılar, son rengi önceki adımda tanımlanan renk sabitine ayarlar.

Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir küpe uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Çizimde, gölgelendirici efektini daha iyi göstermek için turuncu bir renk belirtildi.

![Gölgelendirici Grafiği ve bunun sonucu 3&#45;D modelde](../designers/media/digit-flat-color-effect.png)

Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı](../designers/shader-designer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: Gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)