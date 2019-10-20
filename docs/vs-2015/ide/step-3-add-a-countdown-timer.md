---
title: '3\. Adım: geri sayım Zamanlayıcısı ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bae5b4a81864cc591491c21218a5d8253dfc61bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671841"
---
# <a name="step-3-add-a-countdown-timer"></a>3\. Adım: Geri Sayım Zamanlayıcısı Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticinin üçüncü bölümünde, bir geri sayım süreölçeri ekleyerek, test takici 'in tamamlaması için kalan saniye sayısını izleyebilirsiniz.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-add-a-countdown-timer"></a>Geri sayım Zamanlayıcısı eklemek için

1. Önceki yordamda yaptığınız gibi, **timeleft**adlı bir tamsayı değişkeni ekleyin. Kodunuzun aşağıdaki gibi görünmesi gerekir.

     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]

     Artık, belirttiğiniz süre sonunda bir olay harekete geçiren bir zamanlayıcı gibi saniye sayısını sayan bir yönteme ihtiyacınız vardır.

2. Tasarım penceresinde, araç kutusu **bileşen** kategorisinden bir `Timer` denetimini formunuza taşıyın.

     Denetim, tasarım penceresinin altındaki gri alanda görüntülenir.

3. Formunda, az önce eklediğiniz **Süreölçer1** simgesini seçin ve **Interval** özelliğini **1000**olarak ayarlayın.

     Aralık değeri milisaniyelik olduğundan, 1000 değeri, Tick olayının her saniye ateşlenmesine neden olur.

4. Formunda Zamanlayıcı denetimine çift tıklayın veya seçin ve ardından Enter tuşunu seçin.

     Kod Düzenleyicisi görünür ve az önce eklediğiniz Tick olay işleyicisinin yöntemini görüntüler.

5. Aşağıdaki deyimlerini yeni olay işleyicisi yöntemine ekleyin.

     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]

     Ne eklediklerinize bağlı olarak Zamanlayıcı, **timeleft** tamsayı değişkeninin 0 ' dan büyük olup olmadığını belirleyerek, zaman aşımına uğrar ve sürenin bitmediğini denetler. Varsa, zaman hala kalır. Zamanlayıcı ilk olarak 1 ' den zaman kaldı ve sonra da `timeLabel` denetiminin **Text** özelliğini güncelleştirir ve bu da testi, kaç saniyelik kaldığını gösterir.

     Zaman yoksa, süreölçer yanıt vermez ve `timeLabel` denetimi metnini, **zaman yukarı** gelecek şekilde gösterir. Bir ileti kutusu, sınavın daha fazla olduğunu ve yanıtın ortaya çıkarduğunu duyurduğunu ve bu durumda addend1 ve addend2 ekleyerek ortaya çıkarduğunu duyurur. @No__t_1 denetiminin **Enabled** özelliği, `true` olarak ayarlanır, böylece test takici başka bir test başlatabilir.

     Yalnızca bir `if else` ifadesini eklemiş olursunuz, bu, programları kararlar almak için nasıl söylersiniz. @No__t_0 bir ifade aşağıdaki gibi görünür.

    > [!NOTE]
    > Aşağıdaki örnek yalnızca gösterim amaçlıdır; projenize eklemeyin.

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

     Ek probleme yanıtını göstermek için `else` bloğuna eklediğiniz ifadeye yakından bakın.

     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]

     İfade `addend1 + addend2` iki değişkendeki değerleri birlikte ekler. İlk parça (`sum.Value`) doğru yanıtı göstermek için Sum `NumericUpDown` denetiminin **Value** özelliğini kullanır. Daha sonra test yanıtlarını denetlemek için aynı özelliği kullanırsınız.

     Test sahipleri `NumericUpDown` bir denetim kullanarak daha kolay sayı girebilir, bu da matematik sorunlarına yönelik yanıtlar için bir tane kullanmanızı sağlar. Tüm olası yanıtlar 0 ile 100 arasında tüm sayılardır. **Minimum**, **Maksimum**ve **DecimalPlaces** özelliklerinin varsayılan değerlerini bırakarak, test takipçilerin ondalık sayı, negatif sayı veya çok yüksek sayı girememesini sağlayabilirsiniz. (Test takipçilerin 3,141 girmelerini, ancak 3,1415 değil, izin vermek istiyorsanız, **DecimalPlaces** özelliğini 3 olarak ayarlayabilirsiniz.)

6. @No__t_0 yönteminin sonuna üç satır ekleyin, bu nedenle kod aşağıdaki gibi görünür.

     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]

     Artık, test başladıktan sonra **timeleft** değişkeni 30 olarak ayarlanır ve `timeLabel` denetiminin **Text** özelliği 30 saniyeye ayarlanır. Sonra `Timer` denetiminin `Start()` yöntemi geri sayıma başlar. (Test yanıtı henüz denetlemez.)

7. Programınızı kaydedin, çalıştırın ve ardından formdaki **Başlat** düğmesini seçin.

     Süreölçer, sayıyı aşağı doğru olarak başlatır. Zaman çalıştığında, test sonlanır ve yanıt görüntülenir. Aşağıdaki çizimde devam eden bir test gösterilmektedir.

     ![Matematik testi devam ediyor](../ide/media/express-addcountdown.png "Express_AddCountdown") Matematik testi devam ediyor

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 4. [Adım: CheckTheAnswer () metodunu ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md).

- Önceki öğretici adımına dönmek için bkz. 2. [Adım: rastgele bir ek sorun oluşturma](../ide/step-2-create-a-random-addition-problem.md).
