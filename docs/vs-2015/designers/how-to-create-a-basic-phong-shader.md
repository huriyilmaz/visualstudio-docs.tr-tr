---
title: 'Nasıl yapılır: temel bir Phong gölgelendiricisi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 17ba5d143a5f4534b09b2aaff718af7ce99f2773
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664543"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Nasıl Yapılır: Temel Phong Gölgelendiricisi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, klasik Phong aydınlatma modelini uygulayan bir aydınlatma gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş grafik gölgelendirici dilinin (DGSL) nasıl kullanılacağını gösterir.

 Bu belge Şu etkinlikleri gösterir:

- Gölgelendirici grafiğine düğüm ekleme

- Düğümlerin bağlantısı kesiliyor

- Düğümleri bağlama

## <a name="the-phong-lighting-model"></a>Phong aydınlatma modeli
 Phong aydınlatma modeli, bir yüzey 'nin yansıtıcı özelliklerini taklit eden yansımalı vurgulama 'i içerecek şekilde lambda Yansımalı bileşen Lambert aydınlatma modelinde kullanılan aynı yönlü ışık kaynaklarından ek aydınlatma sağlar, ancak nihai renge olan katkı farklı şekilde işlenir. Yansımalı vurgulama, Görünüm yönü, hafif kaynakların yönü ve yüzey yönü arasındaki ilişkiye bağlı olarak sahnenin her yüzeyi farklı şekilde etkiler. Bu, yüzeysel renk, yüzeysel güç, yüzey yönü ve açık kaynakların rengi, yoğunluğu ve yönü hakkında bir üründür. Açık kaynağı doğrudan görüntüleyicide yansıtan yüzeyler, görüntüleyicideki ışık kaynağını yansıtan maksimum yansımalı katkı ve yüzeyleri, hiçbir katkı almaz. Phong aydınlatma modeli kapsamında, bir veya daha fazla yansımalı bileşen, nesne üzerindeki her bir nokta için yansımalı Vurgulamanın rengini ve yoğunluğunu belirleyip, ardından pikselin nihai rengini oluşturmak için Lambert aydınlatma modelinin sonucuna eklenir.

 Lambert aydınlatma modeli hakkında daha fazla bilgi için bkz. [nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md).

 Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

#### <a name="to-create-a-phong-shader"></a>Bir Phong gölgelendiricisi oluşturmak için

1. [Nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md)bölümünde açıklandığı gibi bir Lambert gölgelendiricisi oluşturun.

2. **Son renk** düğümünden **Lambert** düğümünün bağlantısını kesin. **Lambert** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kes**' i seçin. Bu, bir sonraki adımda eklenen düğüm için yer açar.

3. Grafiğe **ekleme** düğümü ekleyin. **Araç kutusunda**, **matematik**altında **Ekle** ' yi seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe **Yansımalı** bir düğüm ekleyin. **Araç kutusu**' nda, **yardımcı program**altında **Yansımalı** ' ı seçin ve tasarım yüzeyine taşıyın.

5. Yansımalı katkı ekleyin. **Yansımalı** düğümün **Çıkış** terminalini **Add** düğümünün **X** terminaline taşıyın ve ardından **Lambert** düğümünün **Çıkış** terminalini **Add** düğümünün **Y** terminaline taşıyın. Bu bağlantılar piksel için toplam dağıtma ve yansımalı renk katkıları birleştirir.

6. Hesaplanan renk değerini son renge bağlayın. **Add** düğümünün **çıktı** terminalini **son renk** düğümünün **RGB** terminaline taşıyın.

   Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir ekip modeline uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Bu çizimde gölgelendirici etkisini daha iyi göstermek için, gölgelendiricinin **Materialdağıt** parametresi kullanılarak turuncu bir renk belirtilmiştir ve **Materialspecsel** ve **Materialspeculargüç** parametreleri kullanılarak metalik görünümlü bir bitiş belirtilir. Malzeme parametreleri hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)gölgelendiricilerin önizlemesi bölümü.

 ![Gölgelendirici Grafiği ve efektinin önizlemesi](../designers/media/digit-lighting-graph.png "Basamak aydınlatma-grafik")

 Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiriciler önizlemesi hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md) gölgelendiricilerin önizlemesi bölümü

 Aşağıdaki çizimde, bu belgede 3-b modeline uygulanan gölgelendirici gösterilmektedir. **Materialspecsel** özelliği (1,00, 0,50, 0,20, 0,00) olarak ayarlanır ve **MaterialSpecularPower** özelliği 16 olarak ayarlanmıştır.

> [!NOTE]
> **Materialspecsel** özelliği, yüzey malzemelerinin görünen bitişini belirler. Cam veya plastik gibi yüksek parlak bir yüzey, parlak bir beyaz gölgeye sahip olan yansımalı bir renge sahiptir. Metalik bir yüzey, kendi dağıtma rengine yakın bir yansımalı renge sahip olacak şekilde eğilimi gösterir. Bir tam bitiş yüzeyi, koyu bir gri gölge olan yansımalı bir renge sahip olma eğilimi gösterir.
>
> **MaterialSpecularPower** özelliği, Yansımalı vurguların ne kadar kuvvetli olduğunu belirler. Yüksek yansımalı güçler, daha fazla yerelleştirilmiş vurguları taklit etmez. Çok düşük yansımalı güçler, tüm yüzeyin rengini açığa çıkaran ve gizlemek için yoğun ve keskin vurguları taklit edebilir.

 ![Bir modele uygulanan Phong aydınlatma](../designers/media/digit-lighting-model.png "Basamak aydınlatma modeli")

 3B modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir gölgelendiriciyi 3-b modele uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md) [nasıl yapılır: temel Lambert gölgelendirici](../designers/how-to-create-a-basic-lambert-shader.md) [Gölgelendirici Tasarımcısı](../designers/shader-designer.md) [gölgelendirici tasarımcı düğümleri](../designers/shader-designer-nodes.md) oluşturma
