---
title: 'Nasıl Yapılır: Temel Doku Oluşturma'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b356d8596581b1c289d9b9aa13a3d5b362e39e58
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769099"
---
# <a name="how-to-create-a-basic-texture"></a>Nasıl yapılır: Temel doku oluşturma

Bu makalede, aşağıdaki etkinlikler dahil olmak üzere temel doku oluşturmak için görüntü Düzenleyicisi 'nin nasıl kullanılacağı gösterilmektedir:

- Dokunun boyutunu ayarlama

- Ön plan ve arka plan renklerini ayarlama

- Alfa kanalını kullanma (saydamlık)

- **Fill** ve **elips** araçlarını kullanma

- Araç özelliklerini ayarlama

## <a name="create-a-basic-texture"></a>Temel doku oluşturma

Oyununuzun veya uygulamanızın görüntülerini ve dokularını oluşturmak ve değiştirmek için görüntü düzenleyicisini kullanabilirsiniz.

Aşağıdaki adımlarda, "bullseys" hedefini temsil eden bir dokunun nasıl oluşturulacağı gösterilmektedir. İşiniz bittiğinde, doku aşağıdaki resim gibi görünmelidir. Dokuyu dokusundaki daha iyi göstermek için, görüntü Düzenleyicisi bir yeşil, damalı desenli bir model kullanmak üzere yapılandırılmıştır.

!["Bullseys" hedefi, yeşil renkte gösterilen saydamlıkla](../designers/media/digit-bullseye-texture-in-editor.png)

Başlamadan önce **Özellikler** penceresinin görüntülendiğinden emin olun. Görüntü boyutunu ayarlamak, araç özelliklerini değiştirmek ve çalışırken renkleri belirlemek için **Özellikler** penceresini kullanın.

### <a name="create-a-bullseye-target-texture"></a>"Bullseys" hedef dokusu oluşturma

1. Çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında daha fazla bilgi için bkz. [görüntü düzenleyici](../designers/image-editor.md#get-started).

2. Görüntü boyutunu 512x512 piksel olarak ayarlayın. **Özellikler** penceresinde **Genişlik** ve **Yükseklik** özelliklerinin değerlerini olarak ayarlayın `512` .

3. Görüntü Düzenleyicisi araç çubuğunda, **Fill** aracını seçin. **Özellikler** penceresi artık, görüntü özellikleriyle birlikte **Fill** aracının özelliklerini görüntüler.

4. Ön plan rengini tamamen saydam siyah olarak ayarlayın. **Özellikler** penceresinde, **renkler** Özellik grubunda **ön plan**' ı seçin. **R**, **G**, **B**ve renk seçicisinin yanındaki **bir** özellik değerlerini olarak ayarlayın `0` .

5. Görüntü Düzenleyicisi araç çubuğunda, **Fill** aracını seçin ve ardından **SHIFT** tuşunu basılı tutarak görüntüde herhangi bir noktayı seçin. **SHIFT** tuşunun kullanılması, görüntü içindeki rengin yerini alacak şekilde, Fill renginin alfa değerini sağlar; Aksi halde, alfa değeri, görüntü içindeki renkle birlikte Fill rengini karıştırmak için kullanılır.

    > [!IMPORTANT]
    > Bu adım, önceki adımda yer alan renk seçimiyle birlikte, çizeceğiniz "Bullseye" hedef dokusu için temel görüntünün hazırlanmasını sağlar. Görüntü saydam siyah ile dolduğunda ve hedefin kenarlığı siyah olduğu için, hedef etrafında başka hiçbir yapıt olmaz.

6. Görüntü Düzenleyicisi araç çubuğunda **elips** aracını seçin.

7. Ön plan rengini tamamen opak siyah olarak ayarlayın. **R**, **G**ve **B** özelliklerinin değerlerini `0` ve **bir** özelliğinin değerini olarak ayarlayın `255` .

8. Arka plan rengini tamamen opak beyaz olarak ayarlayın. **Özellikler** penceresinde, **renkler** Özellik grubunda, **arka plan**' ı seçin. **R**, **G**, **B**ve **bir** özelliklerinin değerlerini olarak ayarlayın `255` .

9. Elipsin anahattının genişliğini ayarlayın. **Özellikler** penceresinde, **Görünüm** Özellik grubunda, **Width** özelliğinin değerini olarak ayarlayın `8` .

10. Kenar yumuşatma özelliğinin etkinleştirildiğinden emin olun. **Özellikler** penceresinde, **Görünüm** Özellik grubunda, **Anti-Alias** özelliğinin ayarlandığından emin olun.

11. **Elips** aracını kullanarak piksel koordinatından `(3, 3)` piksel koordinatına bir daire çizin `(508, 508)` . Daireyi daha kolay çizmek için, çizerken **SHIFT** tuşuna basılı tutabilirsiniz.

    > [!NOTE]
    > Geçerli işaretçi konumunun piksel koordinatları, Visual Studio durum çubuğunda görüntülenir.

12. Arka plan rengini değiştirin. **R** - `44` , **G** - `165` , **B** - `211` ve **A** ' yı ayarlayın `255` .

13. Piksel koordinatından piksel koordinatına başka bir daire çizin `(64, 64)` `(448, 448)` .

14. Arka plan rengini tamamen opak beyaza çevirin. **R**, **G**, **B**ve **A** 'yı olarak ayarlayın `255` .

15. Piksel koordinatından piksel koordinatına başka bir daire çizin `(128, 128)` `(384, 384)` .

16. Arka plan rengini değiştirin. **R** -, `255` **G** ve **B** ile `64` ve arasında **bir** olarak ayarlayın `255` .

17. Piksel koordinatından piksel koordinatına başka bir daire çizin `(192, 192)` `(320, 320)` .

"Bullseys" hedef dokusu tamamlanmıştır. Saydamlık ile gösterilen nihai görüntü aşağıda verilmiştir.

![Tüm "bullseys" hedef dokusu](../designers/media/gfx_image_demo_bullseye.png)

Bir sonraki adım olarak, bu doku için MıP düzeyleri oluşturabilirsiniz. Bilgi için bkz. [nasıl yapılır: MıP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görüntü Düzenleyicisi](../designers/image-editor.md)
