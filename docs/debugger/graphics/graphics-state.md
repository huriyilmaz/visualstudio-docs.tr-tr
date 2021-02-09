---
title: Grafik durumu | Microsoft Docs
description: Her çizim çağrısının grafik durumunu görerek işleme sorunlarını giderin. Önceki çağrıdan değiştirilen durum bölümleri vurgulanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c6f909d7e250be193bb446d25cd4182d4f062ebe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888608"
---
# <a name="graphics-state"></a>Grafik Durumu
Visual Studio grafik tanılama 'daki durum penceresi, çizim çağrısı gibi geçerli olay sırasında etkin olan grafik durumunu anlamanıza yardımcı olur.

## <a name="understanding-the-state-window"></a>Durum penceresini anlama
 Durum penceresi, işlemeyi etkileyen durumu birlikte toplar ve tek bir yerde hiyerarşik olarak sunar. Uygulamanızın kullandığı Direct3D sürümüne bağlı olarak, durum penceresinde sunulan bilgiler fark edebilir.

### <a name="state-views"></a>Durum görünümleri
 Durum tablosunu birkaç farklı yolla görüntüleyebilirsiniz:

|Görünüm|Description|
|----------|-----------------|
|API giriş durumu görünümü|Bu görünüm, durumu oluşturan Direct3D nesnelerine benzer bir düzende durumu gösterir.|
|Mantıksal giriş durumu görünümü|Bu görünüm, durumu oluşturan Direct3D nesnelerinin yerleşimini yansıtmayan bir mantıksal görünümde durumu gösterir.|
|Sabitlenmiş durum görünümü|Bir hiyerarşi yerine sabitlenmiş durum görünümü, sabitlenmiş durum öğelerini tamamen nitelenmiş adlara sahip düz bir liste halinde sunar. Bu görünüm, az sayıda satırda farklı durum paketlerinden çok sayıda durum öğesi görüntülemek mümkündür.|

##### <a name="to-change-the-state-view"></a>Durum görünümünü değiştirmek için

- Durum penceresinde, sol üst taraftaki başlık çubuğunda, kullanmak istediğiniz durum görünümü stiline karşılık gelen düğmeyi seçin.

  - **API giriş durumu görünümünü göster**

  - **Mantıksal durum görünümünü göster**

  - **Sabitlenmiş durum görünümünü göster**

> [!IMPORTANT]
> **API giriş durumunda** durumu sabitleyebilir ya da **sabitlenmiş durum görünümünde** görüntülenmek üzere **mantıksal durum görünümlerini gösterebilirsiniz** .

### <a name="state-table-format"></a>Durum tablosu biçimi
 Durum penceresi birçok bilgi sütununu gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|Ad|Durum öğesinin adı. Bu öğe bir durum grubunu temsil ediyorsa, öğe görüntülenecek şekilde genişletilebilir.<br /><br /> **API giriş durumu görünümü** ve **mantıksal durum görünümü** durumlarında, durumlar arasındaki hiyerarşik ilişkiyi göstermek için adlar girintilenir.<br /><br /> **Sabitlenmiş durum görünümü** durumunda, tam olarak nitelenmiş adlar düz bir listede görüntülenir.|
|Değer|Durum öğesinin değeri.|
|Tür|Durum öğesinin türü.|

### <a name="changed-state"></a>Değiştirilen durum
 Grafik durumu genellikle sonraki çizim çağrıları arasında artımlı olarak değişir ve çok sayıda işleme sorunu durum yanlış değiştirildiğinde oluşur. Önceki çizim çağrısından bu yana hangi durumun değiştiğini bulmanıza yardımcı olmak için, değiştirilen durum bir yıldız işareti ile işaretlenir ve kırmızı renkte görüntülenir. bu durum yalnızca durumun kendisine değil, üst durum öğesine de uygulanır, böylece, en yüksek düzeyde değiştirilen durumu kolayca belirleyebilir ve sonra ayrıntılara gidebilirsiniz.

### <a name="pinning-state"></a>Sabitleme durumu
 Birçok uygulama, benzer nesneleri sırayla işlerken, bilinen bir durum kümesini değiştirerek, çizim çağrısından çizim çağrısına geçiş yaparken nasıl değiştiğini izleyebilmeniz için değişen durumları yerinde sabitlemek faydalı olur.

 Bu, belirli bir durumdaki bir değişiklikten kaynaklanan bir sorunun kaynağını yalıtdıysanız da yararlı olabilir.

##### <a name="to-pin-state-in-place"></a>Durumu yerinde sabitlemek için

1. Durum penceresinde ilgilendiğiniz durumu bulun. İlgilendiğiniz ayrıntıları bulmak için üst düzey durumu genişletmeniz gerekebilir.

2. İmleci ilgilendiğiniz durumunun üzerine yerleştirin. Durum öğesinin solunda bir PIN simgesi görüntülenir.

3. Durum öğesini yerinde sabitlemek için raptiye simgesini seçin.
