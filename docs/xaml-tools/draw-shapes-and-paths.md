---
title: Şekiller ve yollar çizin
description: Yol ve şekil çizmek XAML Tasarımcısı, Visual Studio için Blend ve birleştirmek için XAML Tasarımcısı'nin özelliklerini kullanın.
ms.custom: SEO-VS-2020
titleSuffix: Blend for Visual Studio
ms.date: 09/22/2020
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: f534d1917e6533c7a03e313f29f3a792dd545aee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136579"
---
# <a name="draw-shapes-and-paths"></a>Şekiller ve yollar çizin

Bu XAML Tasarımcısı tam *olarak* beklediğiniz şekildir. Örneğin: dikdörtgen, daire veya üç nokta. *Yol,* şeklin daha esnek bir sürümüdür. Bunları yeniden şekillendirme veya birleştirarak yeni şekiller oluşturma gibi şeyler de ebilirsiniz.

Şekiller ve yollar vektör grafiklerini kullanır, bu nedenle yüksek çözünürlüklü görüntüler için iyi ölçeklendirilenler.

## <a name="draw-a-shape"></a>Şekil çizme

Varlıklar penceresinde **şekilleri** bulun.

:::image type="content" source="media/blend-shapes.png" alt-text="Visual Studio için Blend'da Varlıklar penceresinin Şekiller kategorisinin ekran Visual Studio için Blend":::

Çalışma panosuna istediğiniz herhangi bir şekli sürükleyin. Ardından, şekli ölçeklendirmek, döndürmek, taşımak veya çarpıtk için şekil tutamaçlarını kullanın.

![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>Yol çizme

Yol, bir dizi bağlantılı çizgi ve eğridir. Varlıklar penceresinde mevcut olmayan ilginç şekiller oluşturmak için bir **yol** kullanın.

Bir çizgi, kalem veya kalem kullanarak yol çizebilirsiniz. Bu araçları Araçlar penceresinde **bulabilirsiniz.**

### <a name="draw-a-straight-line"></a>Düz çizgi çizme

Kalem **aracını veya** Çizgi **aracını** kullanın.

**Kalem aracını kullanma**

Çalışma panosunda, başlangıç noktasını tanımlamak için bir kez tıklayın ve sonra satırın sonunu tanımlamak için yeniden tıklayın.

**Çizgi aracını kullanma**

Çalışma panosunda, satırın başlamalarını istediğiniz yerden sürükleyin ve sonra satırın bitmelerini istediğiniz noktada bırakın.

### <a name="draw-a-curve"></a>Eğri çizme

Kalem **aracını** kullanın.

Çalışma panosunda, bir çizginin başlangıç noktasını tanımlamak için bir kez tıklayın ve ardından istenen eğriyi oluşturmak için işaretçinize tıklayın ve sürükleyin.

Yolu kapatmak için satırda ilk noktaya tıklayın.

### <a name="change-the-shape-of-a-curve"></a>Eğrinin şeklini değiştirme

Doğrudan **seçim aracını** kullanın.

Şekle tıklayın ve ardından eğri şekillerini değiştirmek için şeklin herhangi bir noktasını sürükleyin.

### <a name="draw-a-free-form-path"></a>Serbest form yolu çizme

Kalem **aracını** kullanın.

Çalışma panosunda, tıpkı gerçek bir kalem kullanarak olduğu gibi serbest biçimli bir yol çizin.

### <a name="remove-part-of-a-path"></a>Yolun bir bölümünü kaldırma

Doğrudan **seçim aracını** kullanın.

Silmek istediğiniz segmenti içeren yolu seçin ve sil **düğmesine** tıklayın.

### <a name="remove-a-point-in-a-path"></a>Yol içinde bir nokta kaldırma

Yolu **seçmek** için Seçim aracını kullanın. Ardından Kalem **aracını** kullanarak kaldırmak istediğiniz noktaya tıklayın.

### <a name="add-a-point-to-a-path"></a>Yola nokta ekleme

Yolu **seçmek** için Seçim aracını kullanın. Nokta **eklemek** istediğiniz yolda herhangi bir yere tıklamak için Kalem aracını kullanın.

## <a name="convert-a-shape-to-a-path"></a>Şekli yola dönüştürme

Bir şekli, yolu değiştirerek aynı şekilde değiştirmek için şekli bir yola dönüştürebilirsiniz. Şekli seçin ve ardından Biçim **Yolu'Yola Dönüştür.**  >    >  

**Kısa bir video izleyin:** ![ Yüklü özellikleri yapılandırma ](../designers/media/bldadminconsoleinitialconfigicon.png) [Yollarla çalışma: Şekli yoluna dönüştürme.](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147)

> [!NOTE]
> **Yola Dönüştür** şu anda en az `TargetPlatformVersion` 10.0.16299.0 veya sonraki bir sürümü olan UWP uygulamaları için kullanılamaz.

## <a name="combine-paths"></a>Yolları birleştirme

Yolları ve şekilleri tek bir yolda birleştirebilirsiniz.

![Yolları birleştirme](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|Sayı|Eylem|
|-|-|
|![Birleştirme öncesi iki şekil](../designers/media/b1_1.png)|Birleştirme öncesi iki şekil|
|![Birleştir](../designers/media/b1_2.png)|Birleştir|
|![Böl](../designers/media/b1_3.png)|Böl|
|![Kesiştir](../designers/media/b1_4.png)|Kesiştir|
|![Çakışmayı hariç tut](../designers/media/b1_5.png)|Örtüşmeyi Dışla|
|![Çıkar](../designers/media/b1_6.png)|Çıkar|

**Kısa bir video izleyin:** ![ Yüklü özellikleri yapılandırma ](../designers/media/bldadminconsoleinitialconfigicon.png) [Yollarla çalışma: Yolları birleştirin.](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195)

## <a name="create-a-compound-path"></a>Bileşik yol oluşturma

Bileşik yol oluşturduğunuzda, yolların herhangi bir kesişen bölümleri sonuçtan çıkartılır ve sonuçlanan yol en alt yolun görsel özelliklerini kabul eder.

Bileşik yolu oluşturduk sonra herhangi bir zamanda parçalara ayırabilirsiniz.

![Bileşik yolu kesme](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**Kısa bir video izleyin:** ![ Yüklü özellikleri yapılandırma ](../designers/media/bldadminconsoleinitialconfigicon.png) [Yollarla çalışma: Bileşik yol oluşturun.](https://www.youtube.com/watch?v=Io5bC0-nH6Q)

## <a name="create-a-clipping-path"></a>Kırpma yolu oluşturma

Bir kırpma yolu, kırpma yolu dışına düşen maskelenmiş nesnenin kısımlarını saklayarak, diğer nesneye uygulanan bir yol veya şekildir.

![Kırpma yolu](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**Kısa bir video izleyin:** ![ Yüklü özellikleri yapılandırma ](../designers/media/bldadminconsoleinitialconfigicon.png) [Yollarla çalışma: Bir kırpma yolu oluşturun.](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232)
