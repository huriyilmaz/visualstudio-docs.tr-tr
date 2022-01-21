---
title: 'Öğretici: Windows Forms uygulamasına zamanlayıcı ekleme'
description: Visual Studio Forms uygulamasına zamanlayıcı denetimi ve olay işleyicisi eklemek için Visual Studio IDE'Windows öğrenin.
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
ms.openlocfilehash: 0374a72def5bfaa8edd308c2d6866ed1ce318bd6
ms.sourcegitcommit: 7746657b87b22a7684e79e508af598b02dfe24b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "137610060"
---
# <a name="tutorial-add-a-timer-control-to-a-math-quiz-winforms-app"></a>Öğretici: Matematik testi WinForms uygulamasına Zamanlayıcı denetimi ekleme

Bu dört öğretici serisinde matematik testi oluşturacak. Test, bir sınav sınavını belirli bir süre içinde yanıtlamaya çalışan dört rastgele matematik sorunu içerir.

Test, Zamanlayıcı denetimi kullanır. Bu denetimin ardındaki kod geçen zamanı izler ve sınav sınavını alanların yanıtlarını denetler.

Bu üçüncü öğreticide şunların nasıl olduğunu öğrenirsiniz:

> [!div class="checklist"]
> - Zamanlayıcı denetimi ekleyin.
> - Zamanlayıcı için bir olay işleyicisi ekleyin.
> - Kullanıcının yanıtlarını kontrol etmek, iletileri görüntülemek ve doğru yanıtları doldurmak için kod yazın.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, Matematik testi oluşturma WinForms uygulaması ile [başlayarak önceki öğreticilere göre şekil almaktadır.](tutorial-windows-forms-math-quiz-create-project-add-controls.md) Bu öğreticileri henüz tamamlanmadıysanız, önce bu öğreticilerin üzerinden geçin.

## <a name="add-a-countdown-timer"></a>Geri sayım zamanlayıcısı ekleme

Test sırasındaki zamanı takip etmek için zamanlayıcı bileşeni kullanırsanız. Kalan süre miktarını depolamak için de bir değişkene ihtiyacınız vardır.

1. Önceki öğreticilerde değişkenleri bildir istediğiniz şekilde **timeLeft** adlı bir tamsayı değişkeni ekleyin. **timeLeft bildirimini** diğer bildirimlerin hemen altına koyabilirsiniz. Kodunuz aşağıdaki örnekteki gibi görünüyor olabilir.

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet15":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet15":::

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

1. Form **Windows'de,** araç <xref:System.Windows.Forms.Timer> kutusunun Bileşenler **kategorisinden** **bir denetimi formuza** taşıma. Denetim, tasarım penceresinin altındaki gri alanda görünür.

1. Formda, yeni **ekley** istediğiniz timer1 simgesini seçin ve **Interval** özelliğini **1000 olarak ayarlayın.** Bu aralık milisaniye cinsinden olduğundan, 1000 değeri zamanlayıcının her saniye bir olay <xref:System.Windows.Forms.Timer.Tick> yükseltmesine neden olur.

## <a name="check-the-answers"></a>Yanıtları denetleme

Zamanlayıcı her saniye bir Tick olayı yükselttiklerinden, Bir Tick olayı işleyicisinde geçen zamanı denetlemek mantıklıdır. Bu olay işleyicisinde yanıtları kontrol etmek de pratik bir uygulamadır. Zaman sona ererse veya yanıtlar doğruysa testin sona erer.

Bu olay işleyicisini yazmadan önce matematik sorunlarına verilen yanıtların doğru olup olmadığını `CheckTheAnswer()` belirlemek için adlı bir yöntem ekleyin. Bu yöntemin gibi diğer yöntemlerle aynı olması `StartTheQuiz()` gerekir. Kodunuz aşağıdaki örnekteki gibi görünüyor olabilir.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet17":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet17":::

Bu yöntem matematik sorunlarının yanıtlarını belirler ve sonuçları denetimler içinde yer alan değerlerle <xref:System.Windows.Forms.NumericUpDown> karşılar. Bu kodda:

- Bu Visual Basic yöntem bir değer döndürene kadar her zamanki anahtar sözcük yerine anahtar `Function` `Sub` sözcüğünü kullanır.

- Klavyeyi kullanarak çarpma işaretini (×) ve bölme işaretini (÷) kolayca giresiniz; bu nedenle C# ve Visual Basic çarpma için yıldız (*) ve bölme için eğik çizgi işareti (/) kabul eder.

- C# içinde `&&` `logical and` işlecidir. Bu Visual Basic, eşdeğer işleç `AndAlso` olur. Birden fazla `logical and` koşulun doğru olup olmadığını kontrol etmek için işleci kullanırsiniz. Bu durumda, değerlerin hepsi doğruysa yöntemi değerini `true` döndürür. Aksi takdirde yöntemi değerini `false` döndürür.

- deyimi, `if` denetimin geçerli değerine erişmek için NumericUpDown denetimin **Value** özelliğini kullanır. Bir sonraki bölümde, her denetimde doğru yanıtı görüntülemek için aynı özelliği kullanırsiniz.

## <a name="add-an-event-handler-to-the-timer"></a>Zamanlayıcıya olay işleyicisi ekleme

Artık yanıtları denetlemenin bir yolunu edinebilirsiniz. Şimdi Tick olayı işleyicisi için kodu yazabilirsiniz. Bu kod, zamanlayıcı bir Tick olayı başlattıktan sonra her saniye çalışır. Bu olay işleyicisi, çağırarak sınav sınavını alanların yanıtlarını `CheckTheAnswer()` denetler. Ayrıca testte geçen sürenin ne kadar olduğunu da denetler.

1. Formda Zamanlayıcı denetimine çift **tıklayın** veya seçin ve enter tarak **seçin.** Bu eylemler zamanlayıcıya bir Tick olayı işleyicisi ekler. Kod düzenleyicisi görünür ve Onay işareti işleyicinin yöntemini görüntüler.

1. Aşağıdaki deyimlerini yeni olay işleyicisi yöntemine ekleyin.

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet6":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet6":::

   Testin her saniyesinde bu yöntem çalışır. Kod ilk olarak döndüren değeri `CheckTheAnswer()` denetler.

   - Tüm yanıtlar doğruysa, bu değer olur `true` ve test sona erer:

     - Zamanlayıcı durur.
     - Bir tebrikler iletisi görüntülenir.
     - startButton denetimi **etkin özelliği** olarak ayarlanır, böylece  `true` sınava alan kullanıcı başka bir testi başlatabilirsiniz.

   - `CheckTheAnswer()` `false` döndürürse, kod **timeLeft değerini denetler:**

     - Bu değişken 0'dan büyükse zamanlayıcı **timeLeft'den** 1 çıkarır. Ayrıca **timeLabel** **denetimine** ait Text özelliğini, sınav zamanı olan saniyenin kaç saniye olduğunu gösterecek şekilde de günceller.
     - Zaman kalmazsa zamanlayıcı durur ve **timeLabel** metnini **Time's up olarak değiştirir!** İleti kutusu testin tamam olduğunu ve yanıtların ortaya çıkar olduğunu duyurur. Başlat düğmesi yeniden kullanılabilir hale gelir.

## <a name="start-the-timer"></a>Zamanlayıcıyı başlatma

Test başladığında zamanlayıcıyı başlatmak için aşağıdaki örnekte olduğu gibi yönteminin sonuna `StartTheQuiz()` üç satır ekleyin.

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet7":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet7":::

Testiniz başladığında bu kod **timeLeft** değişkenini 30, **timeLabel** denetimi **text** özelliğini ise 30 saniye olarak ayarlar. Ardından <xref:System.Windows.Forms.Timer.Start> Zamanlayıcı denetimi yöntemi geri sayımı başlatır.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

1. Programınızı kaydedip çalıştırın.

1. Testi **başlat'ı seçin.** Süreölçer saymaya başlar. Zaman bittiğinde test sona erer ve yanıtlar görüntülenir. 

1. Başka bir test başlat ve matematik sorunlarına doğru yanıtları sağla. Zaman sınırı içinde doğru şekilde yanıttığınızda bir ileti kutusu açılır, başlat düğmesi kullanılabilir duruma gelir ve zamanlayıcı durur.

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/quiz-end.png" alt-text="19 saniye kalan tamamlanmış testi gösteren ekran görüntüsü. Testi başlat düğmesi kullanılabilir.":::

## <a name="next-steps"></a>Sonraki adımlar

Matematik testini özelleştirmeyi öğrenmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici 4. bölüm: Matematik testi WinForms uygulamasını özelleştirme](tutorial-windows-forms-math-quiz-customize-ui.md)