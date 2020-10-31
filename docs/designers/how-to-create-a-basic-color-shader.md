---
title: 'Nasıl Yapılır: Temel Renk Gölgelendiricisi Oluşturma'
description: Gölgelendirici tasarımcısını ve yönlendirilen grafik gölgelendirici dilini kullanarak, son rengi sabit bir RGB renk değerine ayarlayan düz renk gölgelendirici oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d966a8fdc565eae5254d21dba4ab9dfaa440de94
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134112"
---
# <a name="how-to-create-a-basic-color-shader"></a>Nasıl yapılır: temel renk gölgelendiricisi oluşturma

Bu makalede, bir düz renk gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş Graf gölgelendirici dilinin (DGSL) nasıl kullanılacağı gösterilmektedir. Bu gölgelendirici, son rengi sabit bir RGB renk değerine ayarlar.

## <a name="create-a-flat-color-shader"></a>Düz renk gölgelendiricisi oluşturma

Bir RGB renk sabitinin Color değerini son çıkış rengine yazarak düz bir renk gölgelendiricisi uygulayabilirsiniz.

Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

1. Birlikte çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Nokta rengi** düğümünü silin. **Nokta rengi** düğümünü seçmek için **Seç** aracını kullanın ve ardından menü çubuğunda Sil **Düzenle** ' yi seçin  >  **Delete** .

3. Grafiğe **renkli sabit** bir düğüm ekleyin. **Araç kutusunda** **sabitler** altında **renk sabiti** ' ni seçin ve tasarım yüzeyine taşıyın.

4. **Renk sabiti** düğümü için bir renk değeri belirtin. **Renk sabiti** düğümünü seçmek için **seçim** aracını kullanın ve ardından **Özellikler** penceresinde, **Çıkış** özelliği ' nde bir renk değeri belirtin. Turuncu için bir değer (1,0, 0,5, 0,2, 1,0) belirtin.

5. Renkli sabiti son renge bağlayın. Bağlantıları oluşturmak için, **renk sabiti** düğümünün **RGB** terminalini **son renk** düğümünün **RGB** terminaline taşıyın ve ardından renk sabiti düğümünün **Alfa** terminalini **son renk** düğümünün **Alfa** **terminaline** taşıyın. Bu bağlantılar, son rengi önceki adımda tanımlanan renk sabitine ayarlar.

Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir küpe uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Çizimde, gölgelendirici efektini daha iyi göstermek için turuncu bir renk belirtildi.

![Gölgelendirici Grafiği ve bunun sonucu 3&#45;D modeli](../designers/media/digit-flat-color-effect.png)

Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı](../designers/shader-designer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
