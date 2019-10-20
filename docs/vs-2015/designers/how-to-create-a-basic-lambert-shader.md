---
title: 'Nasıl yapılır: temel Lambert gölgelendiricisi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 038b3e7db7f1e3b79ee3e41b6e256216a39b91bd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664564"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Nasıl Yapılır: Temel Lambert Gölgelendiricisi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, klasik Lambert aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş grafik gölgelendirici dilinin (DGSL) nasıl kullanılacağını gösterir.

 Bu belge Şu etkinlikleri gösterir:

- Gölgelendirici grafiğine düğüm ekleme

- Düğümlerin bağlantısı kesiliyor

- Düğümleri bağlama

## <a name="the-lambert-lighting-model"></a>Lambert aydınlatma modeli
 Lambert aydınlatma modeli, 3-b sahnede nesneleri gölgelendirmek için çevresel ve yönlü aydınlatma özelliklerini içerir. Çevresel bileşenler, 3-b sahnede temel bir aydınlatma düzeyi sağlar. Yönlü bileşenler, yönlü (en uzakta) ışık kaynaklarından daha fazla aydınlatma sağlar. Çevresel aydınlatma, kendi yönüne bakılmaksızın sahnenin tüm yüzeylerini eşit olarak etkiler. Belirli bir yüzey için, yüzeyde ortam renginin bir ürünüdür ve sahneye ait çevresel aydınlatma renk ve yoğunluğu vardır. Yönlü aydınlatma, yüzdeki her yüzeyi, ışık kaynağının yönlerine göre yüzey yönüne göre farklı şekilde etkiler. Bu, yüzeyi dağıtma renginin ve yönlerinin yanı sıra ışık kaynaklarının rengi, yoğunluğu ve yönlerinin bir ürünüdür. Işık kaynağına doğrudan ulaşan yüzeyler, doğrudan katkı almamak için en yüksek katkı ve yüzeyleri alır. Lambert aydınlatma modeli altında, ortam bileşeni ve bir veya daha fazla yönlü bileşen, nesne üzerindeki her bir nokta için toplam dağıtma rengi katkısını belirlemede birleştirilir.

 Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

#### <a name="to-create-a-lambert-shader"></a>Lambert gölgelendiricisi oluşturmak için

1. Birlikte çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Son renk** düğümündeki **nokta rengi** düğümünün bağlantısını kesin. **Nokta rengi** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kes**' i seçin. **Alfa** terminalini bağlı bırakın.

3. Grafiğe **Lambert** düğümü ekleyin. **Araç kutusu**' nda, **yardımcı program**altında **Lambert** ' yi seçin ve tasarım yüzeyine taşıyın. Lambert düğümü, çevresel ve Dağıtılmış aydınlatma parametrelerine göre pikselin toplam dağıtma rengi katkısını hesaplar.

4. **Nokta rengi** düğümünü **Lambert** düğümüne bağlayın. **Seç** modunda, **nokta rengi** düğümünün **RGB** terminalini **Lambert** düğümünün **dağıtma rengi** terminaline taşıyın. Bu bağlantı, pikselin ara değerli dağıtma rengi ile Lambert düğümünü sağlar.

5. Hesaplanan renk değerini son renge bağlayın. **Lambert** düğümünün **Çıkış** terminalini **son renk** düğümünün **RGB** terminaline taşıyın.

   Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir ekip modeline uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Bu çizimde gölgelendirici etkisini daha iyi göstermek için, gölgelendiricinin **Materialdağıt** parametresi kullanılarak turuncu bir renk belirtilmiştir. Bir oyun veya uygulama, her bir nesne için benzersiz bir renk değeri sağlamak üzere bu parametreyi kullanabilir. Malzeme parametreleri hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)gölgelendiricilerin önizlemesi bölümü.

 ![Gölgelendirici Grafiği ve efektinin önizlemesi.](../designers/media/digit-lambert-effect-graph.png "Basamak-Lambert-efekt-grafik")

 Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için, [gölgelendirici tasarımcısında](../designers/shader-designer.md)gölgelendiricilerin önizlemesi bölümüne bakın.

 Aşağıdaki çizimde, bu belgede 3-b modeline uygulanan gölgelendirici gösterilmektedir.

 ![Bir modele uygulanan Lambert aydınlatma.](../designers/media/digit-lambert-effect-result.png "Digit-Lambert-efekt-sonuç")

 3B modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir gölgelendiriciyi 3-b modele uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md) nasıl [yapılır: temel bir Phong gölgelendirici](../designers/how-to-create-a-basic-phong-shader.md) [Gölgelendirici Tasarımcısı](../designers/shader-designer.md) [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md) oluşturma
