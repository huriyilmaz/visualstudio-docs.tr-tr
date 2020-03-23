---
title: 'Nasıl Yapılır: Temel Doku Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 916be87824a86e96d6fcb791cf8181d70e1e8104
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589467"
---
# <a name="how-to-create-a-basic-texture"></a>Nasıl yapılır: Temel doku oluşturma

Bu makalede, aşağıdaki etkinlikler de dahil olmak üzere temel bir doku oluşturmak için Görüntü Düzenleyicisi nasıl kullanılacağı gösteriş:

- Dokunun boyutunu ayarlama

- Ön plan ve arka plan renklerini ayarlama

- Alfa kanalını kullanma (saydamlık)

- **Dolgu** ve **Elips** araçlarını kullanma

- Takım özelliklerini ayarlama

## <a name="create-a-basic-texture"></a>Temel doku oluşturma

Oyununuz veya uygulamanız için resim ve doku oluşturmak ve değiştirmek için Resim Düzenleyicisi'ni kullanabilirsiniz.

Aşağıdaki adımlar, "bullseye" hedefini temsil eden bir dokunun nasıl oluşturulurdu gösteriş tir. Bittiğinde, doku aşağıdaki resim gibi görünmelidir. Dokudaki saydamlığı daha iyi göstermek için, Görüntü Düzenleyicisi onu görüntülemek için yeşil, damalı bir desen kullanacak şekilde yapılandırılmıştır.

![Şeffaflık yeşil gösterilen "Bullseye" hedef](../designers/media/digit-bullseye-texture-in-editor.png)

Başlamadan önce **Özellikler** penceresinin görüntülendiğinden emin olun. Görüntü boyutunu ayarlamak, takım özelliklerini değiştirmek ve çalışırken renkleri belirtmek için **Özellikler** penceresini kullanırsınız.

### <a name="create-a-bullseye-target-texture"></a>Bir "bullseye" hedef dokusu oluşturun

1. Çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında bilgi için [Resim Düzenleyicisi'ne](../designers/image-editor.md#get-started)bakın.

2. Görüntü boyutunu 512x512 piksel olarak ayarlayın. **Özellikler** penceresinde, **Genişlik** ve **Yükseklik** özelliklerinin `512`değerlerini .

3. Görüntü Düzenleyicisi araç çubuğunda **Dolgu** aracını seçin. **Özellikler** penceresi artık **Dolgu** aracının özelliklerini görüntü özellikleriyle birlikte görüntüler.

4. Ön plan rengini tamamen saydam siyaha ayarlayın. **Özellikler** penceresinde, **Renkler** özellik grubunda **Foreground'u**seçin. Renk seçicinin yanındaki **R**, **G**, **B**ve **A** `0`özelliklerini ayarlama.

5. Görüntü Düzenleyicisi araç **çubuğunda, Dolgu** aracını seçin ve ardından **Shift** tuşuna basın ve basılı tutun ve görüntüdeki herhangi bir noktayı seçin. **Shift** tuşunu kullanmak, görüntüdeki rengi değiştirmek için dolgu renginin alfa değerine neden olur; aksi takdirde, alfa değeri dolgu rengini görüntüdeki renkle karıştırmak için kullanılır.

    > [!IMPORTANT]
    > Bu adım, bir önceki adımdaki renk seçimiyle birlikte, temel görüntünün çizeceğiniz "bullseye" hedef dokusu için hazırlanmasını sağlar. Görüntü saydam siyahla doldurulduğunda ve hedefin kenarlığı siyah olduğundan, hedefin etrafında başka bir takma ad yapılmayacak.

6. Görüntü Düzenleyicisi araç çubuğunda **Elips** aracını seçin.

7. Ön plan rengini tamamen opak siyaha ayarlayın. **R**, **G**ve **B** özelliklerinin `0` değerlerini ve **A** özelliğinin `255`değerini .

8. Arka plan rengini tamamen opak beyaza ayarlayın. **Özellikler** penceresinde, **Renkler** özellik grubunda **Arka Plan'ı**seçin. **R**, **G**, **B**ve **A** özelliklerinin değerlerini `255`.

9. Elipsin anahattının genişliğini ayarlayın. **Özellikler** penceresinde, **Görünüm** özelliği grubunda, **Genişlik** özelliğinin değerini `8`.

10. Anti-diğer adı etkin olduğundan emin olun. **Özellikler** penceresinde, **Görünüm** özelliği grubunda, **Anti-diğer ad** özelliğinin ayarlandıkından emin olun.

11. **Elips** aracını kullanarak, piksel koordinatından `(3, 3)` piksel koordinatına `(508, 508)`bir daire çizin. Daireyi daha kolay çizmek için, çizim yaparken **Shift** tuşuna basıp basılı tutabilirsiniz.

    > [!NOTE]
    > Geçerli işaretçi konumunun piksel koordinatları Visual Studio durum çubuğunda görüntülenir.

12. Arka plan rengini değiştirin. **R'yi,** `44` **G'yi** `165` `211`, **B'yi** ve **A'yı** `255`.

13. Piksel koordinatından piksel `(64, 64)` koordinatına `(448, 448)`başka bir daire çizin.

14. Arka plan rengini tamamen opak beyaza geri çevirin. **Ayar R**, **G**, `255` **B**, ve **A** için .

15. Piksel koordinatından piksel `(128, 128)` koordinatına `(384, 384)`başka bir daire çizin.

16. Arka plan rengini değiştirin. **R'yi,** `255` **G** ve `64` **B'yi** ve **A'yı** `255`.

17. Piksel koordinatından piksel `(192, 192)` koordinatına `(320, 320)`başka bir daire çizin.

"Bullseye" hedef dokusu tamamlandı. İşte şeffaflıkla gösterilen son görüntü.

![Tam "bullseye" hedef doku](../designers/media/gfx_image_demo_bullseye.png)

Bir sonraki adım olarak, bu doku için MIP düzeyleri oluşturabilirsiniz. Bilgi için [bkz: MIP düzeyleri oluşturun ve değiştirin.](../designers/how-to-create-and-modify-mip-levels.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görüntü Düzenleyici](../designers/image-editor.md)
