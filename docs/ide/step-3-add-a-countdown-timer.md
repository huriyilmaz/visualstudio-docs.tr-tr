---
title: '3\. Adım: geri sayım Zamanlayıcısı ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97188d7dcaff2133c22f4954146ba5e977ab2c6d
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776059"
---
# <a name="step-3-add-a-countdown-timer"></a>3\. Adım: geri sayım Zamanlayıcısı ekleme

Bu öğreticinin üçüncü bölümünde, bir geri sayım süreölçeri ekleyerek, test takici 'in tamamlaması için kalan saniye sayısını izleyebilirsiniz.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Geri sayım Zamanlayıcısı eklemek için

1. Önceki yordamda yaptığınız gibi, **timeleft**adlı bir tamsayı değişkeni ekleyin. Kodunuzun aşağıdaki gibi görünmesi gerekir.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Artık, belirttiğiniz süre sonunda bir olay harekete geçiren bir zamanlayıcı gibi saniye sayısını sayan bir yönteme ihtiyacınız vardır.

2. Tasarım penceresinde, **araç kutusu** **bileşen** kategorisinden bir <xref:System.Windows.Forms.Timer> denetimini formunuza taşıyın.

     Denetim, tasarım penceresinin altındaki gri alanda görüntülenir.

3. Formunda, az önce eklediğiniz **Süreölçer1** simgesini seçin ve **Interval** özelliğini **1000**olarak ayarlayın.

     Aralık değeri milisaniyelik olduğundan, 1000 değeri <xref:System.Windows.Forms.Timer.Tick> olayının her saniye başlatılmasına neden olur.

4. Formunda **Zamanlayıcı** denetimine çift tıklayın veya seçin ve ardından **ENTER** tuşunu seçin.

     Kod Düzenleyicisi görünür ve az önce eklediğiniz Tick olay işleyicisinin yöntemini görüntüler.

5. Aşağıdaki deyimlerini yeni olay işleyicisi yöntemine ekleyin.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Ne eklediklerinize bağlı olarak Zamanlayıcı, **timeleft** tamsayı değişkeninin 0 ' dan büyük olup olmadığını belirleyerek, zaman aşımına uğrar ve sürenin bitmediğini denetler. Varsa, zaman hala kalır. Süreölçer ilk olarak 1 ' den zaman kaldı ve sonra **timeLabel** denetiminin **Text** özelliğini güncelleştirir ve bu da, kaç saniye kaldığını test eden bir şekilde görüntüler.

     Zaman yoksa, süreölçer yanıt vermez ve **timeLabel** denetiminin metin değişikliğini **zaman** aşımına göre gösterir. Bir ileti kutusu, sınavın daha fazla olduğunu ve yanıtın ortaya çıkarduğunu duyurduğunu ve bu durumda addend1 ve addend2 ekleyerek ortaya çıkarduğunu duyurur. **StartButton** denetiminin **Enabled** özelliği **true** olarak ayarlanır, böylece test takici başka bir test başlatabilir.

     Yalnızca bir `if else` ifadesini eklemiş olursunuz, bu, programları kararlar almak için nasıl söylersiniz. `if else` bir ifade aşağıdaki gibi görünür.

    > [!NOTE]
    > Aşağıdaki örnek yalnızca tanıtım amaçlıdır; projenize eklemeyin.

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

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     İfade `addend1 + addend2` iki değişkendeki değerleri birlikte ekler. İlk parça (`sum.Value`) doğru yanıtı göstermek için Sum NumericUpDown denetiminin **Value** özelliğini kullanır. Daha sonra test yanıtlarını denetlemek için aynı özelliği kullanırsınız.

     Test sahipleri <xref:System.Windows.Forms.NumericUpDown> bir denetim kullanarak daha kolay sayı girebilir, bu da matematik sorunlarına yönelik yanıtlar için bir tane kullanmanızı sağlar. Tüm olası yanıtlar 0 ile 100 arasında tüm sayılardır. **Minimum**, **Maksimum**ve **DecimalPlaces** özelliklerinin varsayılan değerlerini bırakarak, test takipçilerin ondalık sayı, negatif sayı veya çok yüksek sayı girememesini sağlayabilirsiniz. (Test takipçilerin 3,141 girmelerini, ancak 3,1415 değil, izin vermek istiyorsanız, **DecimalPlaces** özelliğini 3 olarak ayarlayabilirsiniz.)

6. `StartTheQuiz()` yönteminin sonuna üç satır ekleyin, bu nedenle kod aşağıdaki gibi görünür.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Artık, test başladıktan sonra **timeleft** değişkeni 30 olarak ayarlanır ve **timeLabel** denetiminin **Text** özelliği 30 saniyeye ayarlanır. Sonra Zamanlayıcı denetiminin <xref:System.Windows.Forms.Timer.Start> yöntemi geri sayıma başlar. (Test yanıtı henüz denetlemez.)

7. Programınızı kaydedin, çalıştırın ve ardından formdaki **Başlat** düğmesini seçin.

     Süreölçer, sayıyı aşağı doğru olarak başlatır. Zaman çalıştığında, test sonlanır ve yanıt görüntülenir. Aşağıdaki çizimde devam eden bir test gösterilmektedir.

     ![matematik testi devam ediyor](../ide/media/express_addcountdown.png)<br/>
*Matematik testi devam ediyor*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 4. **[Adım: CheckTheAnswer () metodunu ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md)** .

- Önceki öğretici adımına dönmek için bkz. 2. [Adım: rastgele bir ek sorun oluşturma](../ide/step-2-create-a-random-addition-problem.md).
