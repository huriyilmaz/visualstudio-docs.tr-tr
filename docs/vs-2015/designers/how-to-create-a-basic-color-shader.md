---
title: 'Nasıl yapılır: temel renk gölgelendiricisi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90f27e2359954e56a5b3d86bfc31883d4f29c44d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664581"
---
# <a name="how-to-create-a-basic-color-shader"></a>Nasıl Yapılır: Temel Renk Gölgelendiricisi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, bir düz renk gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş grafik gölgelendirici dilinin (DGSL) nasıl kullanılacağını gösterir. Bu gölgelendirici, son rengi sabit bir RGB renk değerine ayarlar.

 Bu belge Şu etkinlikleri gösterir:

- Grafikten düğümleri kaldırma

- Grafiğe düğüm ekleme

- Düğüm özelliklerini ayarlama

- Düğümleri bağlama

## <a name="creating-a-flat-color-shader"></a>Düz renk gölgelendiricisi oluşturma
 Bir RGB renk sabitinin Color değerini son çıkış rengine yazarak düz bir renk gölgelendiricisi uygulayabilirsiniz.

 Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

#### <a name="to-create-a-flat-color-shader"></a>Düz renk gölgelendiricisi oluşturmak için

1. Birlikte çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Nokta rengi** düğümünü silin. **Nokta rengi** düğümünü seçmek için **Seç** aracını kullanın ve ardından menü çubuğunda **Düzenle**, **Sil**' i seçin.

3. Grafiğe **renkli sabit** bir düğüm ekleyin. **Araç kutusunda** **sabitler**altında **renk sabiti** ' ni seçin ve tasarım yüzeyine taşıyın.

4. **Renk sabiti** düğümü için bir renk değeri belirtin. **Renk sabiti** düğümünü seçmek için **seçim** aracını kullanın ve ardından **Özellikler** penceresinde, **Çıkış** özelliği ' nde bir renk değeri belirtin. Turuncu için bir değer (1,0, 0,5, 0,2, 1,0) belirtin.

5. Renkli sabiti son renge bağlayın. Bağlantıları oluşturmak için, **renk sabiti** düğümünün **RGB** terminalini **son renk** düğümünün **RGB** terminaline taşıyın ve ardından renk sabiti düğümünün **Alfa** terminalini **son renk** düğümünün **Alfa** **terminaline** taşıyın. Bu bağlantılar, son rengi önceki adımda tanımlanan renk sabitine ayarlar.

   Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir küpe uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Çizimde, gölgelendirici efektini daha iyi göstermek için turuncu bir renk belirtildi.

 ![Gölgelendirici Grafiği ve bunun sonucu 3&#45;D modeli](../designers/media/digit-flat-color-effect.png "Basamak-düz renkli efekt")

 Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı](../designers/shader-designer.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [nasıl yapılır: gölgelendirici](../designers/how-to-export-a-shader.md) [Gölgelendirici Tasarımcısı](../designers/shader-designer.md) [Gölgelendirici Tasarımcısı düğümlerini](../designers/shader-designer-nodes.md) dışarı aktarma
