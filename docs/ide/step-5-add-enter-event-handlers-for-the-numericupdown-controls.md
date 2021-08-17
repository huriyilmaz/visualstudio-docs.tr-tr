---
title: NumericUpDown denetimleri için Enter olay işleyicileri ekleme
description: Zamanlı matematik testi oluşturma öğreticisinde NumericUpDown denetimleri için Enter olay işleyicileri ekleyin.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2032ae8db33600a232b30c144ae0919d748eec31
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078159"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>5. Adım: NumericUpDown denetimleri için Giriş olay işleyicileri ekleme

Bu öğreticinin beşinci bölümünde, test problemlerinin yanıtlarını girmeyi biraz kolaylaştırmak için olay <xref:System.Windows.Forms.Control.Enter> işleyicileri eksersiniz. Bu kod, sınava giren kişi bunu seçer seçmez her denetimde geçerli değeri seçer ve temizler ve farklı <xref:System.Windows.Forms.NumericUpDown> bir değer girmeye başlar.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçası. Öğreticiye genel bakış için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-verify-the-default-behavior"></a>Varsayılan davranışı doğrulamak için

1. Programınızı çalıştırın ve testi başlatabilirsiniz.

     Toplama sorunu **için NumericUpDown** denetiminde imleç **0** (sıfır) yanında yanıp söner.

2. **3 girin** ve denetimin **30** olduğunu unutmayın.

3. **5 girin** ve **350'nin** görüntülendiğinden ancak bir saniye sonra **100 olarak** değiştiklerini unutmayın.

     Bu sorunu düzeltmeden önce neler olduğunu bir düşün. **3'e girdiğinizde 0'ın** neden kaybolmadiğini ve neden **350'nin** **neden** hemen değil de **100** olarak değiştiğini düşünün.

     Bu davranış garip görünebilir, ancak kodun mantığına göre mantıklıdır. Başlat düğmesini **seçtiğiniz zaman** Etkin **özelliği** **False** olarak ayarlanır ve düğme soluk görünür ve kullanılamaz. Programınız, geçerli seçimi (odak) bir sonraki en düşük TabIndex değerine sahip olan denetimle değiştirir ve bu da toplama sorunu için NumericUpDown denetimidir. Bir NumericUpDown denetimine gitmek için Sekme tuşuna basınca, imleci otomatik olarak denetimin başlangıcına konumlanır. Bu nedenle, girersiniz sayılar sağ taraftan değil, sol taraftan görünür.  **MaximumValue** özelliğinin değerinden daha yüksek olan ve 100 olarak ayarlanmış bir sayı belirttiğinizde, girersiniz sayı bu özelliğin değeriyle değiştirilir.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>NumericUpDown denetimi için Bir Enter olay işleyicisi eklemek için

1. Formda ilk **NumericUpDown** denetimi ("sum" olarak adlandırılır) seçin  ve ardından Özellikler iletişim kutusunda araç **çubuğundaki Olaylar** simgesini seçin.

   ![Özellikler araç çubuğundaki Olaylar düğmesi](media/control-properties-events.png)

   Özellikler **iletişim** kutusundaki **Olaylar sekmesi,** formda seçtiğiniz öğe için yanıt verilebilecek (işleyebilirsiniz) tüm olayları görüntüler. NumericUpDown denetimi seçtiğiniz için listelenen tüm olaylar bu denetime ait olur.

2. Olay **girin'i** seçin, `answer_Enter` yazın ve Enter **tuşuna** basın.

   ![Olay işleyicisi yöntem adını girin](media/enter-event.png)

   Sum NumericUpDown denetimi için bir Enter olay işleyicisi ekledik ve işleyiciyi **answer_Enter.**

3. olay işleyicisi **answer_Enter** yöntemine aşağıdaki kodu ekleyin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet11":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Bu kod karmaşık olabilir, ancak adım adım bakarsanız bunu anabilirsiniz. İlk olarak, yönteminin en üstüne bakın: `object sender` C# veya `sender As System.Object` Visual Basic. Bu parametre, olayı gönderen olarak bilinen, başlatıldı nesnesine başvurur. Bu durumda gönderen nesnesi NumericUpDown denetimidir. Bu nedenle, yönteminin ilk satırda gönderenin yalnızca genel bir nesne değil, özellikle de NumericUpDown denetimi olduğunu belirtirsiniz. (Her NumericUpDown denetimi bir nesnedir, ancak her nesne bir NumericUpDown denetimi değildir.) Yalnızca sum NumericUpDown denetimi için değil, formda tüm NumericUpDown denetimleri için kullanılamayacak olan NumericUpDown denetimi bu yöntemde **answerBox** olarak adlandırılmıştır. Bu yöntemde answerBox değişkenini bildiresiniz, kapsamı yalnızca bu yöntem için geçerlidir. Başka bir deyişle değişkeni yalnızca bu yöntemin içinde kullanılabilir.

     Sonraki satır, answerBox'ın bir nesneden NumericUpDown denetimine başarıyla dönüştürülüp dönüştürüle olmadığını doğrular. Dönüştürme başarısız olursa değişkenin değeri `null` (C#) veya `Nothing` (Visual Basic). Üçüncü satır NumericUpDown denetiminde görüntülenen yanıtın uzunluğunu alır ve dördüncü satır bu uzunluğu temel alarak denetimdeki geçerli değeri seçer. Şimdi, sınav sınavını alan kullanıcı denetimi Visual Studio bu olayı başlattı ve bu da geçerli yanıtın seçili olmasına neden oluyor. Sınava giren kişi farklı bir yanıt girmeye başladığında önceki yanıt temiz olur ve yeni yanıtla değiştirilir.

4. Form **Windows'da** **NumericUpDown denetimi farkını** seçin.

5. Özellikler **iletişim** kutusunun  Olaylar sayfasında Aşağı kaydırarak **Enter** olayına gidin, satırın sonundaki açılan oku seçin ve ardından yeni ekley istediğiniz olay `answer_Enter` işleyicisini seçin.

6. Önceki adımı ürün ve bölüm NumericUpDown denetimleri için tekrarlayın.

7. Programınızı kaydedin ve çalıştırın.

     **NumericUpDown denetimi seçtiğiniz zaman,** farklı bir değer girmeye başsanız mevcut değer otomatik olarak seçilir ve temizlenir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için **[bkz. 6. Adım: Çıkarma sorunu ekleme.](../ide/step-6-add-a-subtraction-problem.md)**

- Önceki öğretici adımına dönmek için [bkz. 4. Adım: CheckTheAnswer() yöntemini ekleme.](../ide/step-4-add-the-checktheanswer-parens-method.md)
