---
title: 'Nasıl yapılır: gri tonlamalı doku gölgelendiricisi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 554717d59a42bed15b37379d3bf7a5c4da727e95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664504"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Nasıl Yapılır: Gri Tonlamalı Doku Gölgelendiricisi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, bir gri tonlamalı doku gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş grafik gölgelendirici dilinin (DGSL) nasıl kullanılacağını gösterir. Bu gölgelendirici, doku örneğinin RGB renk değerini değiştirir ve ardından son rengi ayarlamak için onu değiştirilmemiş Alfa değeriyle birlikte kullanır.

## <a name="creating-a-grayscale-texture-shader"></a>Gri tonlamalı doku gölgelendiricisi oluşturma
 Son çıkış rengine yazmadan önce bir doku örneğinin renk değerini değiştirerek bir gri tonlamalı doku gölgelendiricisi uygulayabilirsiniz.

 Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

#### <a name="to-create-a-grayscale-texture-shader"></a>Gri tonlamalı doku gölgelendiricisi oluşturmak için

1. [Nasıl yapılır: temel doku gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-texture-shader.md)bölümünde açıklandığı gibi temel bir doku gölgelendiricisi oluşturun.

2. **Doku örneği** düğümünün **RGB** terminalinin, **son renk** düğümünün **RGB** terminalden bağlantısını kesin. **Seç** modunda, **doku örnek** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kes**' i seçin. Bu, bir sonraki adımda eklenen düğüm için yer açar.

3. Grafiğe gri **bir düğüm** ekleyin. **Araç kutusunda**, **Filtreler**altında **, doygunluğu Kaldır ' ı seçin ve** tasarım yüzeyine taşıyın.

4. Gri tonlamalı değeri **, doygunluğu Azalt düğümünü kullanarak** hesaplayın. **Seç** modunda, **doku örnek** düğümünün **RGB** terminalini **Gri olan düğümün** **RGB** terminaline taşıyın.

   > [!NOTE]
   > Varsayılan olarak **, doygunluğu Azalt düğümü,** giriş rengini tamamen kaldırır ve gri tona dönüştürme dönüştürmesi için standart ışıklılık ağırlıklarını kullanır. **Işıklılık** özelliğinin değerini değiştirerek veya giriş renginin yalnızca kısmen doygunluğu yaparak **, doygunluğu kaplama düğümünün nasıl** davranacağını değiştirebilirsiniz. Giriş renginin kısmen borçlandırçıkarılması için, [0, 1) aralığında **, doygunluğu Azalt düğümünün** **yüzde** terminaline bir skaler değer sağlayın.

5. Gri tonlamalı renk değerini son renge bağlayın. **Yarım gri** düğümün **Çıkış** terminalini **son renk** düğümünün **RGB** terminaline taşıyın.

   Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir küpe uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Bu çizimde, önizleme şekli olarak bir düzlem kullanılır ve gölgelendirici efektini daha iyi göstermek için bir doku belirtilmiştir.

 ![Gölgelendirici Grafiği ve efektinin önizlemesi](../designers/media/digit-grayscale-effect.png "Basamak-gri tonlamalı-efekt")

 Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [nasıl yapılır: gölgelendirici](../designers/how-to-export-a-shader.md) [Görüntü Düzenleyicisi](../designers/image-editor.md) [Gölgelendirici Tasarımcısı](../designers/shader-designer.md) [gölgelendirici tasarımcı düğümlerini](../designers/shader-designer-nodes.md) dışarı aktarma
