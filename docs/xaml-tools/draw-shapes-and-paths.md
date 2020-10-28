---
title: Şekiller ve yollar çizin
description: Yollar ve şekiller çizmek, bunları değiştirmek ve bunları birleştirmek için Visual Studio için Blend XAML Tasarımcısı özelliklerini kullanın.
ms.custom: SEO-VS-2020
titleSuffix: Blend for Visual Studio
ms.date: 09/22/2020
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c29e2a4718a10193a4c86d1485549ded6ae2c0e
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796803"
---
# <a name="draw-shapes-and-paths"></a>Şekiller ve yollar çizin

XAML Tasarımcısı, bir *Şekil* tam olarak beklediğiniz şeydir. Örneğin: dikdörtgen, daire veya elips. *Yol* , bir şeklin daha esnek bir sürümüdür. Bunları yeniden şekillendirme veya yeni şekiller oluşturmak için birlikte birleştirme gibi işlemler yapabilirsiniz.

Şekiller ve yollar vektör grafikleri kullanır, bu nedenle yüksek çözünürlüklü ekranlarda da ölçeklenebilirler.

## <a name="draw-a-shape"></a>Şekil çiz

**Varlıklar** penceresinde şekilleri bulun.

:::image type="content" source="media/blend-shapes.png" alt-text="Visual Studio için Blend varlıklar penceresinin şekiller kategorisinin ekran görüntüsü":::

İstediğiniz herhangi bir şekli çalışma yüzeyine sürükleyin. Ardından, şekli ölçeklendirmek, döndürmek, taşımak veya eğmek için şekildeki tutamaçları kullanın.

![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>Yol çiz

Yol, bağlantılı çizgiler ve eğrilerden oluşan bir serisidir. **Varlıklar** penceresinde kullanılamayan ilginç şekiller oluşturmak için bir yol kullanın.

Bir çizgi, kalem veya kurşun kalem kullanarak bir yol çizebilirsiniz. Bu araçları **Araçlar** penceresinde bulabilirsiniz.

### <a name="draw-a-straight-line"></a>Düz çizgi çizme

**Kalem** aracını veya **çizgi** aracını kullanın.

**Kalem aracını kullanma**

Çalışma yüzeyinde, başlangıç noktasını tanımlamak için bir kez tıklayın ve sonra satırın sonunu tanımlamak için tekrar ' ye tıklayın.

**Çizgi aracını kullanma**

Çalışma yüzeyinde, çizginin başlamasını istediğiniz yere sürükleyin ve sonra çizginin bitmesini istediğiniz noktada serbest bırakın.

### <a name="draw-a-curve"></a>Eğri çizme

**Kalem** aracını kullanın.

Çalışma yüzeyinde bir satırın başlangıç noktasını tanımlamak için bir kez tıklayın ve sonra istediğiniz eğriyi oluşturmak için işaretçinizi tıklatın ve sürükleyin.

Yolu kapatmak istiyorsanız satırdaki ilk noktaya tıklayın.

### <a name="change-the-shape-of-a-curve"></a>Eğrinin şeklini değiştirme

**Doğrudan seçim** aracını kullanın.

Şekle tıklayın ve sonra eğri şekillerini değiştirmek için şeklin herhangi bir noktasını sürükleyin.

### <a name="draw-a-free-form-path"></a>Serbest form yolu çizme

**Kurşun kalem** aracını kullanın.

Çalışma yüzeyinde, tıpkı gerçek bir kurşun kalem kullanarak yaptığınız gibi serbest biçimli bir yol çizin.

### <a name="remove-part-of-a-path"></a>Yolun bir bölümünü kaldır

**Doğrudan seçim** aracını kullanın.

Silmek istediğiniz segmenti içeren yolu seçin ve **Sil** düğmesine tıklayın.

### <a name="remove-a-point-in-a-path"></a>Yoldaki bir noktayı kaldırma

Yolu seçmek için **seçim** aracını kullanın. Ardından, kaldırmak istediğiniz noktaya tıklayarak **kalem** aracını kullanın.

### <a name="add-a-point-to-a-path"></a>Yola bir işaret ekleyin

Yolu seçmek için **seçim** aracını kullanın. Noktayı eklemek istediğiniz yolda herhangi bir yere tıklayarak **kalem** aracını kullanın.

## <a name="convert-a-shape-to-a-path"></a>Şekli yola dönüştürme

Bir şekli bir yolu değiştirdiğiniz şekilde değiştirmek için şekli bir yola dönüştürün. Şekli seçin ve sonra **Biçim**  >  **yolu**  >  **yola Dönüştür** ' nu seçin.

**Kısa bir video izleyin:** ![ Yollarla çalışan yüklü özellikleri yapılandırma ](../designers/media/bldadminconsoleinitialconfigicon.png) [: bir şekli yola dönüştürme](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

> [!NOTE]
> **Yola Dönüştür** , en az 10.0.16299.0 veya ÜZERI olan UWP uygulamaları için şu anda kullanılamıyor `TargetPlatformVersion` .

## <a name="combine-paths"></a>Yolları Birleştir

Yolları ve şekilleri tek bir yolda birleştirebilirsiniz.

![Yolları Birleştir](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|Sayı|Eylem|
|-|-|
|![Birleştirme öncesi iki şekil](../designers/media/b1_1.png)|Birleştirme öncesi iki şekil|
|![Birleştir](../designers/media/b1_2.png)|Birleştir|
|![Böl](../designers/media/b1_3.png)|Böl|
|![Kesiştir](../designers/media/b1_4.png)|Kesiştir|
|![Örtüşmeyi Dışla](../designers/media/b1_5.png)|Örtüşmeyi Dışla|
|![Çıkar](../designers/media/b1_6.png)|Çıkar|

**Kısa bir video izleyin:** ![ Yollarla çalışan yüklü özellikleri yapılandırma ](../designers/media/bldadminconsoleinitialconfigicon.png) [: yolları birleştirin](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a>Bileşik yol oluşturma

Bileşik yol oluşturduğunuzda, yolların herhangi bir kesişen bölümleri sonuçtan çıkartılır ve sonuçlanan yol en alt yolun görsel özelliklerini kabul eder.

Bir bileşik yolu, oluşturduktan sonra istediğiniz zaman bölebilir.

![Bileşik yolu bölme](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**Kısa bir video izleyin:** ![ Yollarla çalışan yüklü özellikleri yapılandırma ](../designers/media/bldadminconsoleinitialconfigicon.png) [: bileşik bir yol oluşturun](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a>Kırpma yolu oluşturma

Bir kırpma yolu, kırpma yolu dışına düşen maskelenmiş nesnenin kısımlarını saklayarak, diğer nesneye uygulanan bir yol veya şekildir.

![Kırpma yolu](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**Kısa bir video izleyin:** ![ Yollarla çalışan yüklü özellikleri yapılandırma ](../designers/media/bldadminconsoleinitialconfigicon.png) [: kırpma yolu oluşturma](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).
