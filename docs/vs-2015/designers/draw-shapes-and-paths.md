---
title: Şekil ve yollar çizme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8eb2d4f5b025be6f68860c18d1c14da017aaf3fe
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294318"
---
# <a name="draw-shapes-and-paths"></a>Şekiller ve yollar çizin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML Tasarımcısı, bir *Şekil* tam olarak beklediğiniz şeydir. Örneğin: dikdörtgen, daire veya elips. *Yol* , bir şeklin daha esnek bir sürümüdür. Bunları yeniden şekillendirme veya yeni şekiller oluşturmak için birlikte birleştirme gibi işlemler yapabilirsiniz.

 Şekiller ve yollar, vektör grafiklerini kullanarak yüksek çözünürlüklü ekranların ölçeğini de ölçeklendirirler. Vektör grafikleri hakkında daha fazla bilgi edinmek istiyorsanız bkz. [vektör grafikleri](https://www.youtube.com/watch?v=MoCSwF0n-io) veya [vektör grafikleri](https://www.webopedia.com/TERM/V/vector_graphics.html).

 **Bu konuda:**

- [Şekil çiz](#Shape)

- [Yol çiz](#Path)

- [Şekli yola dönüştürme](#Convert)

- [Yolları Birleştir](#Combine)

- [Bileşik yol oluşturma](#Compound)

- [Kırpma yolu oluşturma](#Clipping)

## <a name="Shape"></a>Şekil çiz
 Şekilleri **varlıklar** panelinde bulabilirsiniz.

 ![Varlıklar panelindeki şekiller kategorisi](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")

 İstediğiniz herhangi bir şekli çalışma yüzeyine sürükleyin. Ardından, şekli ölçeklendirmek, döndürmek, taşımak veya eğmek için şekildeki tutamaçları kullanabilirsiniz.

 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")

## <a name="Path"></a>Yol çiz
 Yol, bağlantılı çizgiler ve eğrilerden oluşan bir serisidir. **Varlıklar** panelinde kullanılamayan ilginç şekiller oluşturmak için bir yol kullanın.

 Bir çizgi, kalem veya kurşun kalem kullanarak bir yol çizebilirsiniz. Bu araçları **Araçlar** panelinde bulabilirsiniz.

 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")

### <a name="draw-a-straight-line"></a>Düz çizgi çizme
 **Kalem** aracını ![ ](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54")veya **çizgi** aracını ![ ](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")kullanın.

 **Kalem aracını kullanma**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54")

 Çalışma yüzeyinde, başlangıç noktasını tanımlamak için bir kez tıklayın ve sonra satırın sonunu tanımlamak için tekrar ' ye tıklayın.

 **Çizgi aracını kullanma**![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")

 Çalışma yüzeyinde, çizginin başlamasını istediğiniz yere sürükleyin ve sonra çizginin bitmesini istediğiniz noktada serbest bırakın.

### <a name="draw-a-curve"></a>Eğri çizme
 **Kalem** aracını ![ ](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54")kullanın.

 Çalışma yüzeyinde bir satırın başlangıç noktasını tanımlamak için bir kez tıklayın ve sonra istediğiniz eğriyi oluşturmak için işaretçinizi tıklatın ve sürükleyin.

 Yolu kapatmak istiyorsanız satırdaki ilk noktaya tıklayın.

### <a name="change-the-shape-of-a-curve"></a>Eğrinin şeklini değiştirme
 **Doğrudan seçim** aracını ![ ](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-C116-451D-8dd2-1f88b8406362")kullanın.

 Şekle tıklayın ve sonra eğri şekillerini değiştirmek için şeklin herhangi bir noktasını sürükleyin.

### <a name="draw-a-free-form-path"></a>Serbest form yolu çizme
 **Kurşun kalem** aracını ![ ](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-B012-987ee63450cd")kullanın.

 Çalışma yüzeyinde, tıpkı gerçek bir kurşun kalem kullanarak yaptığınız gibi serbest biçimli bir yol çizin.

### <a name="remove-part-of-a-path"></a>Yolun bir bölümünü kaldır
 **Doğrudan seçim** aracını ![ ](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-C116-451D-8dd2-1f88b8406362")kullanın.

 Silmek istediğiniz segmenti içeren yolu seçin ve **Sil** düğmesine tıklayın.

### <a name="remove-a-point-in-a-path"></a>Yoldaki bir noktayı kaldırma
 **Seçim** aracını ![ ](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-A0F7-af20851e4daa")ve **kalem** aracını ![ ](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54")kullanın.

 Yolu seçmek için seçim ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-A0F7-af20851e4daa") aracını kullanın. Ardından, kaldırmak istediğiniz noktaya tıklayarak ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54") Kalem aracını kullanın.

### <a name="add-a-point-to-a-path"></a>Yola bir işaret ekleyin
 **Seçim** aracını ![ ](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-A0F7-af20851e4daa")ve **kalem** aracını ![ ](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54")kullanın.

 Yolu seçmek için seçim ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-A0F7-af20851e4daa") aracını kullanın. Noktayı eklemek istediğiniz yolda ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54") herhangi bir yere tıklayarak Kalem aracını kullanın.

## <a name="Convert"></a>Şekli yola dönüştürme
 Bir şekli bir yolu değiştirdiğiniz şekilde değiştirmek için şekli bir yola dönüştürün.

 **Kısa bir video izleyin:** yollarla çalışan ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [: bir şekli yola dönüştürme](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

## <a name="Combine"></a>Yolları Birleştir
 Yolları ve şekilleri tek bir yolda birleştirebilirsiniz.

 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-a338-4ef4-96c5-dae51cc1ca8a")

|||||
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|Birleştirme öncesi iki şekil|![](../designers/media/b1-4.png "B1_4")|Kesiştir|
|![](../designers/media/b1-2.png "B1_2")|Birleştir|![](../designers/media/b1-5.png "B1_5")|Örtüşmeyi Dışla|
|![](../designers/media/b1-3.png "B1_3")|Sayısına|![](../designers/media/b1-6.png "B1_6")|Çıkarma|

 **Kısa bir video izleyin:** yollarla çalışan ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [: yolları birleştirin](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="Compound"></a>Bileşik yol oluşturma
 Bileşik yol oluşturduğunuzda, yolların herhangi bir kesişen bölümleri sonuçtan çıkartılır ve sonuçlanan yol en alt yolun görsel özelliklerini kabul eder.

 Bir bileşik yolu, oluşturduktan sonra istediğiniz zaman bölebilir.

 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")

 **Kısa bir video izleyin:** yollarla çalışan ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [: bileşik yol oluşturma](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="Clipping"></a>Kırpma yolu oluşturma
 Bir kırpma yolu, kırpma yolu dışına düşen maskelenmiş nesnenin kısımlarını saklayarak, diğer nesneye uygulanan bir yol veya şekildir.

 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")

 **Kısa bir video izleyin:** yollarla çalışan ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [: kırpma yolu oluşturma](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
