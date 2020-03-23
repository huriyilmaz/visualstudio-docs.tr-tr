---
title: 'Nasıl yapılır: Ön Çarpımlı Alfa kullanan Doku Dışa Aktarma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84017bef80f42bd1848833b957abd88297d1e12d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635477"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Nasıl yapılır: Ön çarpımlı alfa kullanan dokuyu dışarı aktarma

Görüntü İçeriği Ardışık Bir kaynak görüntüden önceden çoğaltılmış alfa dokuları oluşturabilir. Bunlar kullanımı daha basit ve önceden çoğaltılmış alfa içermeyen dokulardan daha sağlam olabilir.

Bu belge şu etkinlikleri gösterir:

- Kaynak görüntünün Görüntü İçerik Ardışık Alanı tarafından işlenecek şekilde yapılandırılması.

- Görüntü İçeriği Ardışık Çizgi Sini'yi önceden çoğaltılmış alfa oluşturacak şekilde yapılandırı

## <a name="premultiplied-alpha"></a>Önceden çoğaltılmış alfa
Önceden çoğaltılmış alfa, geleneksel, önceden çoğaltılmayan alfaya göre çeşitli avantajlar sunar, çünkü texel'in renk katkısını (yansıttığı renk) fiziksel malzemelerle ışığın gerçek dünya etkileşimini daha iyi temsil eder. sahne) onun translucency (onun içinizin verdiği altta yatan renk miktarı). Önceden çoğaltılmış alfa kullanmanın avantajlarından bazıları şunlardır:

- Önceden çoğaltılmış alfa ile karıştırma bir bağdaştırıcı bir işlemdir; birden çok yarı saydam dokuları karıştırma sonucu, dokuların harmanlandığı sıraya bakılmaksızın aynıdır.

- Önceden çoğaltılmış alfa ile harmanlamanın etkileşimli doğası nedeniyle, yarı saydam nesnelerin çok geçişli işlemesi basitleştirilmiştir.

- Önceden çoğaltılmış alfa kullanılarak, hem saf katkı karışımı (alfayı sıfıra ayarlayarak) hem de doğrusal enterpolasyonlu harmanlama aynı anda elde edilebilir. Örneğin, bir parçacık sisteminde, katkı yla harmanlanmış bir ateş parçacığı, doğrusal enterpolasyon kullanılarak harmanlanmış yarı saydam bir duman parçacığına dönüşebilir. Önceden çoğaltılmış alfa olmadan, yangın parçacıklarını duman parçacıklarından ayrı olarak çekmeniz ve çizim çağrıları arasında render durumunu değiştirmeniz gerekir.

- Önceden çoğaltılmış alfa kullanan dokular, önceden çoğaltılmış alfa kullanmayan dokuları karıştırdığınızda ortaya çıkan renksiz kenarlar veya "hale efekti" göstermez.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Önceden çarpılmış alfa kullanan bir doku oluşturmak için

1. Temel bir doku ile başlayın. Varolan bir resim dosyasını yükleyin veya nasıl açıklansın: [Temel bir doku oluşturun.](../designers/how-to-create-a-basic-texture.md)

2. Doku dosyasını Görüntü İçerik Ardışık Alanı tarafından işlenir şekilde yapılandırın. **Çözüm Gezgini'nde,** doku dosyasının kısayol menüsünü açın ve ardından **Özellikler'i**seçin. Yapılandırma **Özellikleri** > **Genel** sayfasında, **Madde Türü** özelliğini Görüntü İçerik **Ardışık Alanı**olarak ayarlayın. **İçerik** özelliğinin **Evet** ve **İçten Dışla** olarak Ayarlandıktan emin **olun, Hayır**olarak ayarlandı ve ardından **Uygula** düğmesini seçin. **Resim İçeriği Yapı Denetimi** yapılandırma özelliği sayfası görüntülenir.

3. Önceden çoğaltılmış alfa oluşturmak için Görüntü İçerik Ardışık Hatlar'ı yapılandırın. Yapılandırma **Özellikleri** > **Resim İçerik Boru Hattı** > **Genel** sayfasında, **Önceden çarpılmış alfa biçimi** özelliğini Evet **(/generatepremultipliedalpha)** olarak ayarlayın.

4. **Tamam** düğmesini seçin.

   Projeyi oluşturduğunuzda, Görüntü İçerik Ardışık Bölümü kaynak görüntüyü çalışma biçiminden belirttiğiniz çıktı biçimine dönüştürür — bu, görüntünün önceden çoğaltılmış alfa biçimine dönüştürülmesini içerir ve sonuç projenin çıktısına kopyalanır Dizin.