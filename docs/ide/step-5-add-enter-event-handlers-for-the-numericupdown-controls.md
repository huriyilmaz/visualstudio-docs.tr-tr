---
title: 'Adım 5: SayısalUpDown denetimleri için olay işleyicileri girin'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17fb9ba8e82739ddb0a420f52b6f7f945a6454b8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579835"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Adım 5: SayısalUpDown denetimleri için olay işleyicileri girin

Bu öğreticinin beşinci bölümünde, sınav <xref:System.Windows.Forms.Control.Enter> sorunları için yanıt ları girmeyi biraz daha kolaylaştırmak için etkinlik işleyicileri eklersiniz. Bu kod, sınav alıcısı <xref:System.Windows.Forms.NumericUpDown> seçer seçmez ve farklı bir değer girmeye başlar başlamaz her denetimdeki geçerli değeri seçer ve temizler.

> [!NOTE]
> Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

## <a name="to-verify-the-default-behavior"></a>Varsayılan davranışı doğrulamak için

1. Programınızı çalıştırın ve testi başlatın.

     Ekleme sorunu için **SayısalUpDown** denetiminde imleç **0** 'ın (sıfır) yanında yanıp söner.

2. **3**girin ve **denetimin 30'u**gösterdiğini unutmayın.

3. **5**girin ve **350'nin** göründüğünü ancak bir saniyesonra **100'e** değiştirdiğini unutmayın.

     Bu sorunu çözmeden önce neler olduğunu düşünün. **3'e** girdiğinizde **0'ın** neden kaybolmadığını ve **350'nin** neden **100'e** değiştirilmediğini ancak hemen değiştirilmediğini düşünün.

     Bu davranış garip görünebilir, ancak kodun mantığı göz önüne alındığında mantıklı. **Başlat** düğmesini seçtiğinizde, **Etkin** özelliği **False**olarak ayarlanır ve düğme soluk görünür ve kullanılamaz. Programınız, ekleme sorunu için NumericUpDown denetimi olan bir sonraki en düşük TabIndex değerine sahip denetime geçerli seçimi (odak) değiştirir. Sayısal UpDown denetimine gitmek için **Sekme** tuşunu kullandığınızda, imleç denetimin başında otomatik olarak konumlandırılır, bu nedenle girdiğiniz sayılar sağ taraftan değil, sol taraftan görünür. 100 olarak ayarlanmış **MaximumValue** özelliğinin değerinden daha yüksek bir sayı belirttiğiniz zaman, girdiğiniz sayı o özelliğin değeriyle değiştirilir.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>SayısalUpDown denetimi için enter olay işleyicisi eklemek için

1. Formdaki ilk **Sayısal UpDown** denetimini ("toplam" olarak adlandırılır) seçin ve ardından **Özellikler** iletişim kutusunda araç çubuğundaki **Etkinlikler** simgesini seçin.

   ![Özellikler araç çubuğundaki olaylar düğmesi](media/control-properties-events.png)

   **Özellikler** iletişim kutusundaki **Olaylar** sekmesi, formda seçtiğiniz öğe için yanıtverebileceğiniz (işlediğiniz) tüm olayları görüntüler. Sayısal UpDown denetimini seçtiğinizden, listelenen tüm olaylar bununla ilgilidir.

2. **Enter** olayını seçin, `answer_Enter`yazın ve sonra **Enter** tuşuna basın.

   ![Olay işleyicisi yöntem adı girin](media/enter-event.png)

   Toplam NumericUpDown denetimi için bir Enter olay işleyicisi eklediniz ve işleyiciyi **answer_Enter.**

3. **answer_Enter** olay işleyicisi için yöntemde aşağıdaki kodu ekleyin:

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Bu kod karmaşık görünebilir, ancak adım adım bakarsanız bunu anlayabilirsiniz. İlk olarak, yöntemin üst `object sender` bak: C `sender As System.Object` # veya Visual Basic içinde. Bu parametre, olay gönderen olarak bilinen, ateşleyen nesneyi ifade eder. Bu durumda, gönderen nesne NumericUpDown denetimidir. Bu nedenle, yöntemin ilk satırında, gönderenin yalnızca genel bir nesne değil, özellikle bir SayısalUpDown denetimi olduğunu belirtirsiniz. (Her SayısalUpDown denetimi bir nesnedir, ancak her nesne bir SayısalUpDown denetimi değildir.) NumericUpDown denetimi bu yöntemde **answerBox** olarak adlandırılır, çünkü formdaki tüm SayısalUpDown denetimleri için kullanılacaktır, sadece toplam SayısalUpDown denetimi için değil. Bu yöntemde answerBox değişkenini beyan ettiğiniz için, kapsamı yalnızca bu yöntem için geçerlidir. Başka bir deyişle, değişken yalnızca bu yöntem içinde kullanılabilir.

     Sonraki satır, answerBox'ın bir nesneden SayısalUpDown denetimine başarıyla dönüştürülüp dönüştürülmediğini (döküm) doğrular. Dönüştürme başarısız olduysa, değişkenin `null` (C#) veya `Nothing` (Visual Basic) değeri olur. Üçüncü satır, NumericUpDown denetiminde görünen yanıtın uzunluğunu alır ve dördüncü satır bu uzunluğa bağlı olarak denetimdeki geçerli değeri seçer. Şimdi, sınav ait olan kontrol seçtiğinde, Visual Studio geçerli yanıtın seçilmesine neden olan bu olayı ateşler. Sınav alıcısı farklı bir yanıt girmeye başlar başlamaz, önceki yanıt temizlenir ve yeni yanıtla değiştirilir.

4. **Windows Forms Designer'da,** Sayısal **UpDown** denetimi arasındaki farkı seçin.

5. **Özellikler** iletişim kutusunun **Etkinlikler** sayfasında, **Enter** olayına gidin, satırın sonundaki açılır ok'u seçin ve `answer_Enter` sonra eklediğiniz olay işleyicisini seçin.

6. Ürün ve bölüm numericUpDown denetimleri için önceki adımı yineleyin.

7. Programınızı kaydedin ve çalıştırın.

     **Bir SayısalUpDown** denetimi seçtiğinizde, varolan değer otomatik olarak seçilir ve farklı bir değer girmeye başladığınızda temizlenir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz.](../ide/step-6-add-a-subtraction-problem.md)**

- Önceki öğretici adıma dönmek için [bkz.](../ide/step-4-add-the-checktheanswer-parens-method.md)
