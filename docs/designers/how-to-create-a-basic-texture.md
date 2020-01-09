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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589467"
---
# <a name="how-to-create-a-basic-texture"></a>Nasıl yapılır: temel doku oluşturma

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

2. Görüntü boyutunu 512x512 piksel olarak ayarlayın. **Özellikler** penceresinde **Genişlik** ve **Yükseklik** özelliklerinin değerlerini `512`olarak ayarlayın.

3. Görüntü Düzenleyicisi araç çubuğunda, **Fill** aracını seçin. **Özellikler** penceresi artık, görüntü özellikleriyle birlikte **Fill** aracının özelliklerini görüntüler.

4. Ön plan rengini tamamen saydam siyah olarak ayarlayın. **Özellikler** penceresinde, **renkler** Özellik grubunda **ön plan**' ı seçin. **R**, **G**, **B**ve renk seçicisinin yanındaki **bir** özellik değerlerini `0`olarak ayarlayın.

5. Görüntü Düzenleyicisi araç çubuğunda, **Fill** aracını seçin ve ardından **SHIFT** tuşunu basılı tutarak görüntüde herhangi bir noktayı seçin. **SHIFT** tuşunun kullanılması, görüntü içindeki rengin yerini alacak şekilde, Fill renginin alfa değerini sağlar; Aksi halde, alfa değeri, görüntü içindeki renkle birlikte Fill rengini karıştırmak için kullanılır.

    > [!IMPORTANT]
    > Bu adım, önceki adımda yer alan renk seçimiyle birlikte, çizeceğiniz "Bullseye" hedef dokusu için temel görüntünün hazırlanmasını sağlar. Görüntü saydam siyah ile dolduğunda ve hedefin kenarlığı siyah olduğu için, hedef etrafında başka hiçbir yapıt olmaz.

6. Görüntü Düzenleyicisi araç çubuğunda **elips** aracını seçin.

7. Ön plan rengini tamamen opak siyah olarak ayarlayın. **R**, **G**ve **B** özelliklerinin değerlerini `0` ve **bir** özelliğin değerini `255`olarak ayarlayın.

8. Arka plan rengini tamamen opak beyaz olarak ayarlayın. **Özellikler** penceresinde, **renkler** Özellik grubunda, **arka plan**' ı seçin. **R**, **G**, **B** **ve Özellikler değerlerini** `255`olarak ayarlayın.

9. Elipsin anahattının genişliğini ayarlayın. **Özellikler** penceresinde, **Görünüm** Özellik grubunda, **Width** özelliğinin değerini `8`olarak ayarlayın.

10. Kenar yumuşatma özelliğinin etkinleştirildiğinden emin olun. **Özellikler** penceresinde, **Görünüm** Özellik grubunda, **Anti-Alias** özelliğinin ayarlandığından emin olun.

11. **Elips** aracını kullanarak piksel koordinatı `(3, 3)` piksel koordinat `(508, 508)`bir daire çizin. Daireyi daha kolay çizmek için, çizerken **SHIFT** tuşuna basılı tutabilirsiniz.

    > [!NOTE]
    > Geçerli işaretçi konumunun piksel koordinatları, Visual Studio durum çubuğunda görüntülenir.

12. Arka plan rengini değiştirin. **R** 'yi `44`, **G** 'ye `165`, **B** 'den `211`ve **A** 'ya `255`olarak ayarlayın.

13. Piksel koordinatı `(64, 64)` piksel koordinat `(448, 448)`başka bir daire çizin.

14. Arka plan rengini tamamen opak beyaza çevirin. **R**, **G**, **B**ve **A** 'yı `255`olarak ayarlayın.

15. Piksel koordinatı `(128, 128)` piksel koordinat `(384, 384)`başka bir daire çizin.

16. Arka plan rengini değiştirin. **R** 'yi `255`, **G** ve **B** 'ye `64`ve **bir** `255`olarak ayarlayın.

17. Piksel koordinatı `(192, 192)` piksel koordinat `(320, 320)`başka bir daire çizin.

"Bullseys" hedef dokusu tamamlanmıştır. Saydamlık ile gösterilen nihai görüntü aşağıda verilmiştir.

![Tüm "bullseys" hedef dokusu](../designers/media/gfx_image_demo_bullseye.png)

Bir sonraki adım olarak, bu doku için MıP düzeyleri oluşturabilirsiniz. Bilgi için bkz. [nasıl yapılır: MıP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görüntü Düzenleyicisi](../designers/image-editor.md)
