---
title: 'Nasıl yapılır: ön çarpılmış Alfa içeren dokuyu dışa aktarma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 452048a512a9e2f8d4d44d5db99cc005c0dac55c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664433"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Nasıl yapılır: Ön Çarpımlı Alfa kullanan Doku Dışa Aktarma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görüntü Içeriği ardışık düzeni, kaynak görüntüden ön çarpılmış Alfa dokuları oluşturabilir. Bu, kullanımı daha kolay ve ön çarpılmış Alfa içermeyen dokulardan daha sağlam olabilir.

 Bu belge Şu etkinlikleri gösterir:

- Görüntü Içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.

- Ön çarpılmış alfa oluşturmak için görüntü Içeriği ardışık düzeni yapılandırma.

## <a name="premultiplied-alpha"></a>Ön çarpılmış Alfa
 Önceden çarpılan Alfa geleneksel, ön ödeme olmayan Alpha üzerinden çeşitli avantajlar sunar, çünkü Texel 'nin renk katılımına sahip olan (sahneye eklediği renk), bir fiziksel malzemelerle gerçek dünya etkileşimini daha iyi temsil eder. Önceden çarpılan Alfa kullanmanın avantajlarından bazıları şunlardır:

- Ön çarpılmış alfa ile karıştırma, ilişkilendirilebilir bir işlemdir; birden çok yarı saydam dokuların karıştırılmasını elde etmek, dokuların karıştıralındığı sıra ne olursa olsun aynıdır.

- Ön çarpılmış alfa ile birlikte karışmanın ilişkilendirilebilir doğası nedeniyle, yarı saydam nesnelerin çoklu geçişli işlemesi basitleştirilmiştir.

- Ön çarpılmış alfa kullanarak hem saf ekleme karışımı (alfa ile sıfıra ayarlanarak) hem de doğrusal olarak enterpolasyonlu karıştırma aynı anda elde edilebilir. Örneğin, bir parçacık sisteminde, ek olarak karıştırılan bir ateş partilü, doğrusal ilişkilendirme kullanılarak karıştırılan bir yarı saydam duman parçacığı haline gelebilir. Ön çarpılmış alfa olmadan, ateş parçacıkların duman parçacıkların ayrı olarak çizilmesi ve çizim çağrıları arasındaki işleme durumunu değiştirmeniz gerekir.

- Ön çarpılmış Alfa sıkıştır kullanan dokular, olmadıklarından daha yüksek kaliteden daha yüksek kalitede ve veya "Halo etkisi" gibi, ön çarpılmış Alfa kullanmayan dokuları karıştırabildiklerinde ortaya kalmazlar.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Ön çarpılmış alfa kullanan bir doku oluşturmak için

1. Temel bir dokuyla başlayın. Varolan bir resim dosyasını yükleyin veya [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)bölümünde açıklandığı gibi bir tane oluşturun.

2. Doku dosyasını görüntü Içeriği ardışık düzeni tarafından işlenecek şekilde yapılandırın. **Çözüm Gezgini**, doku dosyasının kısayol menüsünü açın ve ardından **Özellikler**' i seçin. **Yapılandırma özellikleri**, **genel** sayfasında, **öğe türü** özelliğini **görüntü içeriği ardışık düzeni**olarak ayarlayın. **İçerik** özelliğinin **Evet** olarak ayarlandığından ve **derlemeden hariç tut** ' un **Hayır**olarak ayarlandığından emin olun ve ardından **Uygula** düğmesini seçin. **Görüntü Içeriği ardışık düzen** yapılandırma özelliği sayfası görüntülenir.

3. Ön çarpılmış alfa oluşturmak için görüntü Içeriği ardışık düzenini yapılandırın. **Yapılandırma özellikleri**, **görüntü içeriği ardışık düzeni**, **genel** sayfasında, **ön çarpılmış Alfa biçimini Dönüştür** özelliğini **Evet (/generatepremultipliedalpha)** olarak ayarlayın.

4. **Tamam** düğmesini seçin.

   Projeyi oluşturduğunuzda, görüntü Içeriği ardışık düzeni kaynak görüntüyü çalışma biçiminden belirlediğiniz çıkış biçimine dönüştürür — bu, görüntünün ön çarpılmış Alfa biçimine dönüştürülmesini içerir ve sonuç projenin çıkış dizinine kopyalanır.
