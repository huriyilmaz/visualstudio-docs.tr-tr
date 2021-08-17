---
title: '3. Adım: Geri sayım zamanlayıcısı ekleme'
description: Sınavda kalan saniye sayısını izlemek için geri sayım zamanlayıcısı ekleme hakkında bilgi edinmek için.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 40716f502366d93fd48760173c29db1bf69bee4e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040846"
---
# <a name="step-3-add-a-countdown-timer"></a>3. Adım: Geri sayım zamanlayıcısı ekleme

Bu öğreticinin üçüncü bölümünde, sınav sınavlarının bitimini takip etmek için kalan saniye sayısını izlemek için bir geri sayım zamanlayıcısı eksersiniz.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçası. Öğreticiye genel bakış için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-add-a-countdown-timer"></a>Geri sayım zamanlayıcısı eklemek için

1. Önceki yordamda olduğu gibi **timeLeft** adlı bir tamsayı değişkeni ekleyin. Kodunuz aşağıdaki gibi görünüyor olabilir.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet5":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Şimdi zamanlayıcı gibi saniyeleri sayan ve belirttiğiniz süreden sonra bir olay yükselten bir yönteme ihtiyacınız var.

2. Tasarım penceresinde, Araç Kutusunun <xref:System.Windows.Forms.Timer> Bileşenler  kategorisindeki bir denetimi **formuza** taşımanız gerekir.

     Denetim, tasarım penceresinin altındaki gri alanda görünür.

3. Formda, yeni **ekley** istediğiniz timer1 simgesini seçin ve **Interval** özelliğini **1000 olarak ayarlayın.**

     Aralık değeri milisaniye olduğundan, 1000 değeri olayın her <xref:System.Windows.Forms.Timer.Tick> saniye etkinliğe neden olur.

4. Formda Zamanlayıcı denetimine çift **tıklayın** veya seçin ve enter **tuşuna** basın.

     Kod düzenleyicisi görüntülenir ve az önce ekleydniz Tick olay işleyicisi için yöntemi görüntüler.

5. Aşağıdaki deyimlerini yeni olay işleyicisi yöntemine ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet6":::

     Zamanlayıcı, eklediklerine bağlı olarak **timeLeft** tamsayı değişkeninin 0'dan büyük olup olmadığını belirleyerek her saniyenin zaman bitip bit olmadığını denetler. Varsa, süre yine de kalır. Zamanlayıcı önce timeLeft'in 1'ini çıkarır ve **ardından timeLabel** **denetimine** ait Text özelliğini test sınav zamanı kaç saniye kalarak gösterir.

     Zaman kalmazsa zamanlayıcı durur ve **timeLabel** denetimi metnini **Time's up** olarak gösterir! İleti kutusu testin tamam olduğunu duyurur ve yanıt ortaya çıkar (bu durumda addend1 ve addend2 ekleriyle). startButton denetimin **Enabled** **özelliği** true olarak **ayarlanır,** böylece sınava alan kullanıcı başka bir testi başlatabilirsiniz.

     Az önce `if else` programlara karar vermelerini nasıl söylersiniz? deyimini ekledik. Deyimi `if else` aşağıdakine benzer.

    > [!NOTE]
    > Aşağıdaki örnek yalnızca gösterim amaçlıdır; bunu projenize eklemeyin.

    ```vb
    If (something that your program will check) Then
        ' One or more statements that will run
        ' if what the program checked is true.
    Else
        ' One or more statements that will run
        ' if what the program checked is false.
    End If
    ```

    ```csharp
    if (something that your program will check)
    {
        // One or more statements that will run
        // if what the program checked is true.
    }
    else
    {
        // One or more statements that will run
        // if what the program checked is false.
    }
    ```

     Toplama sorununun yanıtını göstermek için `else` bloğuna ekleyilen deyimine yakından bakın.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet24":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet24":::

     deyimi, `addend1 + addend2` değerleri iki değişkene ekler. İlk bölüm ( `sum.Value` ), doğru yanıtı görüntülemek için sum NumericUpDown denetimine ait **Value** özelliğini kullanır. Daha sonra testin yanıtlarını kontrol etmek için aynı özelliği kullanacağız.

     Sınava girenler, bir denetim kullanarak sayıları daha kolay bir şekilde girebiliyor. Bu nedenle matematik problemlerinin <xref:System.Windows.Forms.NumericUpDown> yanıtları için bir denetim kullanabilirsiniz. Olası yanıtların hepsi 0 ile 100 arasında tam sayılardır. **Minimum** **,** Maksimum ve **DecimalPlaces** özelliklerinin varsayılan değerlerini bırakarak, sınava girenlerin ondalık, negatif sayı veya sayı girileyemlerinin çok yüksek olmasını sağlarsınız. (Sınava girenlerin 3.141 girmesine izin vermek, ancak 3.1415'i girmek için **DecimalPlaces** özelliğini 3 olarak ayarlayabilirsiniz.)

6. Yönteminin sonuna üç satır `StartTheQuiz()` ekleyin, böylece kod aşağıdaki gibi olur.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs" id="Snippet7":::

     Testiniz başladığında **timeLeft** değişkeni 30, **timeLabel** denetimi **text** özelliği ise 30 saniye olarak ayarlanır. Ardından <xref:System.Windows.Forms.Timer.Start> Zamanlayıcı denetimi yöntemi geri sayımı başlatır. (Test henüz yanıtı kontrol etmese de bir sonraki adım olacak.)

7. Programınızı kaydedin, çalıştırın ve ardından **formda** Başlat düğmesini seçin.

     Süreölçer saymaya başlar. Zaman bittiğinde test sona erer ve yanıt görünür. Aşağıdaki çizimde devam eden test gösterilmiştir.

     ![Matematik testi devam ediyor](../ide/media/express_addcountdown.png)<br/>
*Matematik testi devam ediyor*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için **[bkz. 4. Adım: CheckTheAnswer() yöntemini ekleme.](../ide/step-4-add-the-checktheanswer-parens-method.md)**

- Önceki öğretici adımına dönmek için [bkz. 2. Adım: Rastgele toplama sorunu oluşturma.](../ide/step-2-create-a-random-addition-problem.md)
