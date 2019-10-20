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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635477"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Nasıl yapılır: ön çarpılmış Alpha içeren bir dokuyu dışarı aktarma

Görüntü Içeriği ardışık düzeni, kaynak görüntüden ön çarpılmış Alfa dokuları oluşturabilir. Bu, kullanımı daha kolay ve ön çarpılmış Alfa içermeyen dokulardan daha sağlam olabilir.

Bu belge Şu etkinlikleri gösterir:

- Görüntü Içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.

- Ön çarpılmış alfa oluşturmak için görüntü Içeriği ardışık düzeni yapılandırma.

## <a name="premultiplied-alpha"></a>Ön çarpılmış Alfa
Önceden çarpılan Alfa, Texel 'nin renk katkısını ayırarak fiziksel malzemelerle gerçek dünya etkileşimini daha iyi temsil ettiğinden, geleneksel, ön çarpılmamış Alfa üzerinden çeşitli avantajlar sunar. sahne), kendi geçiş aşamasından (üzerinden izin verdiği temel rengin miktarı). Önceden çarpılan Alfa kullanmanın avantajlarından bazıları şunlardır:

- Ön çarpılmış alfa ile karıştırma, ilişkilendirilebilir bir işlemdir; birden çok yarı saydam dokuların karıştırılmasını elde etmek, dokuların karıştıralındığı sıra ne olursa olsun aynıdır.

- Ön çarpılmış alfa ile birlikte karışmanın ilişkilendirilebilir doğası nedeniyle, yarı saydam nesnelerin çoklu geçişli işlemesi basitleştirilmiştir.

- Ön çarpılmış alfa kullanarak hem saf ekleme karışımı (alfa ile sıfıra ayarlanarak) hem de doğrusal olarak enterpolasyonlu karıştırma aynı anda elde edilebilir. Örneğin, bir parçacık sisteminde, ek olarak karıştırılan bir ateş partilü, doğrusal ilişkilendirme kullanılarak karıştırılan bir yarı saydam duman parçacığı haline gelebilir. Ön çarpılmış alfa olmadan, ateş parçacıkların duman parçacıkların ayrı olarak çizilmesi ve çizim çağrıları arasındaki işleme durumunu değiştirmeniz gerekir.

- Ön çarpılmış Alfa sıkıştır kullanan dokular, olmadıklarından daha yüksek kaliteden daha yüksek kalitede ve veya "Halo etkisi" gibi, ön çarpılmış Alfa kullanmayan dokuları karıştırabildiklerinde ortaya kalmazlar.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Ön çarpılmış alfa kullanan bir doku oluşturmak için

1. Temel bir dokuyla başlayın. Varolan bir resim dosyasını yükleyin veya [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)bölümünde açıklandığı gibi bir tane oluşturun.

2. Doku dosyasını görüntü Içeriği ardışık düzeni tarafından işlenecek şekilde yapılandırın. **Çözüm Gezgini**, doku dosyasının kısayol menüsünü açın ve ardından **Özellikler**' i seçin. **Yapılandırma özellikleri**  > **genel** sayfasında, **öğe türü** özelliğini **görüntü içeriği ardışık düzeni**olarak ayarlayın. **İçerik** özelliğinin **Evet** olarak ayarlandığından ve **derlemeden hariç tut** ' un **Hayır**olarak ayarlandığından emin olun ve ardından **Uygula** düğmesini seçin. **Görüntü Içeriği ardışık düzen** yapılandırma özelliği sayfası görüntülenir.

3. Ön çarpılmış alfa oluşturmak için görüntü Içeriği ardışık düzenini yapılandırın. **Yapılandırma özellikleri**  > **görüntü içeriği ardışık düzeni**  > **genel** sayfasında, **önceden çarpılmış Alfa biçimini Dönüştür** özelliğini **Evet (/generatepremultipliedalpha)** olarak ayarlayın.

4. **Tamam** düğmesini seçin.

   Projeyi oluşturduğunuzda, görüntü Içeriği ardışık düzeni kaynak görüntüyü çalışma biçiminden belirlediğiniz çıkış biçimine dönüştürür — bu, görüntünün ön çarpılmış Alfa biçimine dönüştürülmesini içerir ve sonuç projenin çıktısına kopyalanır dizinden.