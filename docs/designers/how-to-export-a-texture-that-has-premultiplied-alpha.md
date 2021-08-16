---
title: 'Nasıl yapılır: Ön Çarpımlı Alfa kullanan Doku Dışa Aktarma'
description: Görüntü İçeriği İşlem Hattı'nın kaynak görüntüden kullanımı daha basit ve daha sağlam olan önceden oluşturulmuş alfa dokular oluşturma hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 0143a0a69ed1a1d54873c24426c840999191545750fd5618592a37c3f9090b5f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403600"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Nasıl yapılır: Ön çarpımlı alfa kullanan dokuyu dışarı aktarma

Görüntü İçeriği İşlem Hattı, kaynak görüntüden önceden oluşturulmuş alfa dokular oluşturabilirsiniz. Bunların kullanımı daha basit olabilir ve önceden sonuç alfa içermesi gereken dokulardan daha sağlam olabilir.

Bu belge şu etkinlikleri gösterir:

- Görüntü İçeriği İşlem Hattı tarafından işlenecek kaynak görüntüyü yapılandırma.

- Görüntü İçeriği İşlem Hattını önceden oluşturulmuş alfa oluşturmak için yapılandırma.

## <a name="premultiplied-alpha"></a>Önceden sonuçlandırmış alfa
Premultiplied alfa geleneksel, önsal olmayan alfaya göre çeşitli avantajlar sunar çünkü teselin renk katkısını (sahneye ekleyen renk) saydamlıktan (izin veren temel alınan renk miktarı) ayırarak ışığın fiziksel malzemelerle gerçek dünya etkileşimini daha iyi temsil eder. Önceden sonuçlandırmış alfa kullanmanın avantajlarından bazıları:

- Önceden sonuçlanmış alfa ile karıştırma, bir iosalama işlemidir; Birden çok yarı saydam dokuyu karıştırmanın sonucu, dokuların karıştırıldık düzenine bakılmaksızın aynıdır.

- Önceden sonuçlanmış alfa ile karıştırmanın ilgili yapısı nedeniyle, saydam nesnelerin çoklu geçişli işlemesi basitleştirilir.

- Önceden işlenmiş alfa kullanılarak, hem saf ek karıştırma (alfa değeri sıfır olarak ayarlanır) hem de doğrusal olarak irdelenmiş karıştırma eşzamanlı olarak elde edilebilir. Örneğin, bir parçacık sisteminde, eklenebilir olarak karıştırıldı bir yangın parçacığı doğrusal ilişkilendirme kullanılarak karıştırıldı yarı saydam bir duman parçacığı olabilir. Önceden iş parçacıklı alfa olmadan, yangın parçacıklarını duman parçacıklarından ayrı olarak çizmeli ve çekme çağrıları arasında işleme durumunu değiştirmeniz gerekirdi.

- Önişlek alfa sıkıştırması kullanan dokular, daha yüksek kalitelidir ve renksiz kenarları (veya "halo etkisi") göstermez. Bu, önceden işlenen alfa kullanmayan dokuları karıştırırken ortaya çıkar.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Önceden sonuçlandırmış alfa kullanan bir doku oluşturmak için

1. Temel bir dokuyla başlama. Var olan bir görüntü dosyasını yükleme veya Oluşturma: Temel doku oluşturma [konusunda açıklandığı gibi bir tane oluşturun.](../designers/how-to-create-a-basic-texture.md)

2. Doku dosyasını Görüntü İçeriği İşlem Hattı tarafından işlenecek şekilde yapılandırma. Bu **Çözüm Gezgini** doku dosyasının kısayol menüsünü açın ve Özellikler'i **seçin.** Yapılandırma Özellikleri **Genel**  >  **sayfasında** Öğe Türü özelliğini **Görüntü İçeriği İşlem** Hattı **olarak ayarlayın.** İçerik özelliğinin **Evet,** Derlemeden  Hariç Tut özelliğinin Hayır olarak ayarlanmış olduğundan **emin olun** ve uygula **düğmesini** seçin.  Görüntü **İçeriği İşlem Hattı** yapılandırma özelliği sayfası görüntülenir.

3. Önceden oluşturulmuş alfa oluşturmak için Görüntü İçeriği İşlem Hattını yapılandırma. Yapılandırma Özellikleri **Görüntü İçeriği** İşlem Hattı Genel sayfasında Convert to  >    >   **pre-multiplied alpha format** özelliğini **Evet (/generatepremultipliedalpha) olarak ayarlayın.**

4. Tamam **düğmesini** seçin.

   Projeyi derlemek için Görüntü İçeriği İşlem Hattı kaynak görüntüyü çalışma biçiminden belirttiğiniz çıkış biçimine dönüştürür. Bu, görüntünün önceden sonuçlanmış alfa biçimine dönüştürülmesi içerir ve sonuç projenin çıkış dizinine kopyalanır.