---
title: 'öğretici: Windows Forms uygulamasını özelleştirme'
description: math test Windows Forms uygulamasını özelleştirmeyi öğrenin. ayrıca, değerleri temizlemek için olay işleyicileri eklemek üzere Visual Studio ıde 'yi de kullanacaksınız.
ms.custom:
- vs-acquisition
dev_langs:
- CSharp
- VB
ms.date: 01/20/2022
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2d21a7f75c5d045dae172adf90d54c74febeef7e
ms.sourcegitcommit: 7746657b87b22a7684e79e508af598b02dfe24b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "137610048"
---
# <a name="tutorial-customize-a-math-quiz-winforms-app"></a>Öğretici: matematik testi WinForms uygulamasını özelleştirme

Bu dört öğreticilerde, bir matematik testi oluşturacaksınız. Test, bir sınavın belirli bir süre içinde yanıt almaya çalışacağı dört rastgele matematik sorunu içerir.

Bu öğreticide, varsayılan değerleri temizleyerek ve denetimlerin görünümünü özelleştirerek sınavının nasıl gelişdiğini gösterilmektedir.

Bu son öğreticide şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Varsayılan NumericUpDown denetim değerlerini temizlemek için olay işleyicileri ekleyin.
> - Testi özelleştirin.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, [bir Math test WinForms uygulaması oluşturma](tutorial-windows-forms-math-quiz-create-project-add-controls.md)ile başlayan önceki öğreticilerde oluşturulur. Bu öğreticileri tamamlamadıysanız, önce bu öğreticilerden ilerleyin.

## <a name="add-event-handlers-for-the-numericupdown-controls"></a>NumericUpDown denetimleri için olay işleyicileri ekleme

Test, <xref:System.Windows.Forms.NumericUpDown> Test takipçilerin sayı girerken kullandığı denetimleri içerir. Bir yanıt girdiğinizde, önce varsayılan değeri seçmeniz ya da bu değeri el ile silmeniz gerekir. Bir <xref:System.Windows.Forms.Control.Enter> olay işleyicisi ekleyerek, yanıtları girmeyi daha kolay hale getirebilirsiniz. Bu kod, test taki seçtiği ve farklı bir değer girmeye başladığı anda her NumericUpDown denetimindeki geçerli değeri seçer ve temizler.

1. Formdaki ilk NumericUpDown denetimini seçin. **Özellikler** iletişim kutusunda, araç çubuğunda **Olaylar** simgesini seçin.

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/toolbar-events-icon.png" alt-text="Özellikler iletişim kutusunun araç çubuğunu gösteren ekran görüntüsü. Bir şimşek sürgüsü içeren simge çağrılır.":::

   **Özellikler** 'deki **Olaylar** sekmesi, formda seçtiğiniz öğe için yanıt verebildiği tüm olayları görüntüler. Bu durumda, listelenen tüm olaylar NumericUpDown denetimine aittir.

1. **ENTER** olayını seçin, **answer_Enter** girin ve ardından **ENTER**' u seçin.

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/enter-event.png" alt-text="ENTER olayının seçildiği Özellikler iletişim kutusunu gösteren ekran görüntüsü. Yöntem kutusu answer_Enter içerir.":::

   Kod Düzenleyicisi görünür ve **Sum** NumericUpDown denetimi için oluşturduğunuz olay işleyicisini girin.

1. **Answer_Enter** olay işleyicisine yönelik yöntemde aşağıdaki kodu ekleyin:

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet11":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet11":::

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   Bu kodda:

   - İlk satır yöntemini bildirir. Adında bir parametre içerir `sender` . C# ' de parametresi olur `object sender` . Visual Basic, bu `sender As System.Object` . Bu parametre, gönderen olarak bilinen, olayı oluşturan nesnesine başvurur. Bu durumda, Gönderen nesnesi NumericUpDown denetimidir. 
   - Yöntemin içindeki ilk satır, göndereni bir genel nesneden NumericUpDown denetimine çevirir veya dönüştürür. Bu satır, **doğrulamaktadır** adını NumericUpDown denetimine de atar. Formdaki tüm NumericUpDown denetimleri, yalnızca ek sorunun denetimini değil, bu yöntemi kullanır.
   - Sonraki satır, **doğrulamaktadır** 'In bir NumericUpDown denetimi olarak başarıyla dönüştürülmediğini doğrular.
   - Deyimin içindeki ilk satır, `if` Şu anda NumericUpDown denetimindeki yanıtın uzunluğunu belirler.
   - Deyimin içindeki ikinci satır, `if` denetimdeki geçerli değeri seçmek için yanıt uzunluğunu kullanır.

   test, denetimi seçtiğinde Visual Studio bu olayı tetikler. Bu kod geçerli yanıtı seçer. Test eden, farklı bir yanıt girmeye başladıktan hemen sonra geçerli yanıt temizlenir ve yeni Yanıtla değiştirilmiştir.

1. **Windows Form Tasarımcısı**, çıkarma sorununun NumericUpDown denetimini seçin.

1. **Özellikler** Iletişim kutusunun **Olaylar** sayfasında, **ENTER** olayını bulun ve ardından açılan menüden **answer_Enter** ' ı seçin. Bu olay işleyicisi, yeni eklediğiniz bir işleyicidir.

1. Çarpma ve bölme NumericUpDown denetimleri için önceki iki adımı tekrarlayın.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

1. Programınızı kaydedip çalıştırın.

1. Bir test başlatın ve bir NumericUpDown denetimi seçin. Mevcut değer otomatik olarak seçilir ve sonra farklı bir değer girmeye başladığınızda temizlenir.

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/existing-value-selected.png" alt-text="Dört rastgele matematik sorunu ile test uygulamasını gösteren ekran görüntüsü. İlk sorunun varsayılan yanıtı seçilidir.":::

## <a name="customize-your-quiz"></a>Sınavını özelleştirin

Öğreticinin bu son bölümünde, testi özelleştirmenin ve öğrendiklerinizi genişletmenin bazı yollarını keşfedeceksiniz.

### <a name="change-the-color-of-a-label"></a>Bir etiketin rengini değiştirme

- Bir test içinde yalnızca beş saniye kaldığında bu etiketi kırmızıya açmak için **timeLabel** denetiminin **BackColor** özelliğini kullanın.

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

- Test üzerindeyken rengi sıfırlayın.

### <a name="play-a-sound-for-a-correct-answer"></a>Doğru yanıt için ses çal

Bir denetime doğru yanıt girildiğinde, bir sesi oynatarak sınava ipucu sunun <xref:System.Windows.Forms.NumericUpDown> . Bu işlevi uygulamak için, her bir denetimin olayı için bir olay işleyicisi yazın <xref:System.Windows.Forms.NumericUpDown.ValueChanged> . Bu olay türü, her bir test bir denetimin değerini değiştirdiğinde ateşlenir.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler! Bu öğretici serisini tamamladınız. Visual Studio ıde 'de bu programlama ve tasarım görevlerini tamamladınız:

- Windows Forms kullanan bir Visual Studio projesi oluşturuldu
- Etiket, düğme ve NumericUpDown denetimleri eklendi
- Süreölçer eklendi
- Denetimleriniz için olay işleyicilerini ayarlama
- olayları işlemek için yazılan C# veya Visual Basic kodu

Eşleşen bir oyunun nasıl oluşturulacağı hakkında başka bir öğretici serisini öğrenmeye devam edin.
> [!div class="nextstepaction"]
> [Öğretici 3: eşleşen oyun oluşturma](tutorial-windows-forms-create-match-game.md)