---
title: 'Nasıl yapılır: temel doku oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a19cd0b68927effc32b0480fdeb7286be8ad8dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664568"
---
# <a name="how-to-create-a-basic-texture"></a>Nasıl Yapılır: Temel Doku Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede, temel bir doku oluşturmak için görüntü Düzenleyicisi 'nin nasıl kullanılacağı gösterilir.

 Bu belge Şu etkinlikleri gösterir:

- Dokunun boyutunu ayarlama

- Ön plan ve arka plan renklerini ayarlama

- Alfa kanalını kullanma (saydamlık)

- **Fill** ve **elips** araçlarını kullanma

- Araç özelliklerini ayarlama

## <a name="creating-a-basic-texture"></a>Temel doku oluşturma
 Oyununuzun veya uygulamanızın görüntülerini ve dokularını oluşturmak ve değiştirmek için görüntü düzenleyicisini kullanabilirsiniz.

 Aşağıdaki adımlarda, "bullseys" hedefini temsil eden bir dokunun nasıl oluşturulacağı gösterilmektedir. İşiniz bittiğinde, doku aşağıdaki resim gibi görünmelidir. Dokuyu dokusundaki daha iyi göstermek için, görüntü Düzenleyicisi bir yeşil, damalı desenli bir model kullanmak üzere yapılandırılmıştır.

 !["Bullseys" hedefi, yeşil renkte gösterilen saydamlıkla](../designers/media/digit-bullseye-texture-in-editor.png "Basamak-Bullseys-doku-ın-düzenleyici")

 Başlamadan önce **Özellikler** penceresinin görüntülendiğinden emin olun. Görüntü boyutunu ayarlamak, araç özelliklerini değiştirmek ve çalışırken renkleri belirlemek için **Özellikler** penceresini kullanın.

#### <a name="to-create-a-bullseye-target-texture"></a>"Bullseys" hedef dokusu oluşturmak için

1. Birlikte çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında daha fazla bilgi için bkz. [Görüntü Düzenleyicisi](../designers/image-editor.md)'ndeki Başlarken bölümü.

2. Görüntü boyutunu 512x512 piksel olarak ayarlayın. **Özellikler** penceresinde **Genişlik** ve **Yükseklik** özelliklerinin değerlerini olarak ayarlayın `512` .

3. Görüntü Düzenleyicisi araç çubuğunda, **Fill** aracını seçin. **Özellikler** penceresi artık, görüntü özellikleriyle birlikte **Fill** aracının özelliklerini görüntüler.

4. Ön plan rengini tamamen saydam siyah olarak ayarlayın. **Özellikler** penceresinde, **renkler** Özellik grubunda **ön plan**' ı seçin. **R**, **G**, **B**ve renk seçicisinin yanındaki **bir** özellik değerlerini olarak ayarlayın `0` .

5. Görüntü Düzenleyicisi araç çubuğunda, **Fill** aracını seçin ve ardından SHIFT tuşunu basılı tutarak görüntüde herhangi bir noktayı seçin. SHIFT tuşunun kullanılması, görüntü içindeki rengin yerini alacak şekilde, Fill renginin alfa değerini sağlar; Aksi halde, alfa değeri, görüntü içindeki renkle birlikte Fill rengini karıştırmak için kullanılır.

   > [!IMPORTANT]
   > Bu adım, önceki adımda yer alan renk seçimiyle birlikte, çizeceğiniz "Bullseye" hedef dokusu için temel görüntünün hazırlanmasını sağlar. Görüntü saydam siyah ile dolduğunda ve hedefin kenarlığı siyah olduğu için, hedef etrafında başka hiçbir yapıt olmaz.

6. Görüntü Düzenleyicisi araç çubuğunda **elips** aracını seçin.

7. Ön plan rengini tamamen opak siyah olarak ayarlayın. **R**, **G**ve **B** özelliklerinin değerlerini `0` ve **bir** özelliğinin değerini olarak ayarlayın `255` .

8. Arka plan rengini tamamen opak beyaz olarak ayarlayın. **Özellikler** penceresinde, **renkler** Özellik grubunda, **arka plan**' ı seçin. **R**, **G**, **B**ve **bir** özelliklerinin değerlerini olarak ayarlayın `255` .

9. Elipsin anahattının genişliğini ayarlayın. **Özellikler** penceresinde, **Görünüm** Özellik grubunda, **Width** özelliğinin değerini olarak ayarlayın `8` .

10. Kenar yumuşatma özelliğinin etkinleştirildiğinden emin olun. **Özellikler** penceresinde, **Görünüm** Özellik grubunda, **Anti-Alias** özelliğinin ayarlandığından emin olun.

11. **Elips** aracını kullanarak piksel koordinatından `(3, 3)` piksel koordinatına bir daire çizin `(508, 508)` . Daireyi daha kolay çizmek için, çizerken SHIFT tuşuna basılı tutabilirsiniz.

    > [!NOTE]
    > Geçerli işaretçi konumunun piksel koordinatları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] durum çubuğunda görüntülenir.

12. Arka plan rengini değiştirin. **R** - `44` , **G** - `165` , **B** - `211` ve **A** ' yı ayarlayın `255` .

13. Piksel koordinatından piksel koordinatına başka bir daire çizin `(64, 64)` `(448, 448)` .

14. Arka plan rengini tamamen opak beyaza çevirin. **R**, **G**, **B**ve **A** 'yı olarak ayarlayın `255` .

15. Piksel koordinatından piksel koordinatına başka bir daire çizin `(128, 128)` `(384, 384)` .

16. Arka plan rengini değiştirin. **R** -, `255` **G** ve **B** ile `64` ve arasında **bir** olarak ayarlayın `255` .

17. Piksel koordinatından piksel koordinatına başka bir daire çizin `(192, 192)` `(320, 320)` .

    "Bullseys" hedef dokusu tamamlanmıştır. Saydamlık ile gösterilen nihai görüntü aşağıda verilmiştir.

    ![Tüm "bullseys" hedef dokusu](../designers/media/gfx-image-demo-bullseye.png "gfx_image_demo_bullseye")

    Bir sonraki adım olarak, bu doku için MıP düzeyleri oluşturabilirsiniz. Bilgi için bkz. [nasıl yapılır: MıP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Görüntü Düzenleyicisi](../designers/image-editor.md)
