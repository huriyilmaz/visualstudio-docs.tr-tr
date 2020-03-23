---
title: 'Adım 3: Geri sayım sayıcı ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ca2dce7f6f9ddc484b67f250f34d69747c6e46e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579876"
---
# <a name="step-3-add-a-countdown-timer"></a>Adım 3: Geri sayım sayıcı ekleme

Bu öğreticinin üçüncü bölümünde, sınav katılımcısının bitirmesi için kalan saniye sayısını izlemek için bir geri sayım sayıcı eklersiniz.

> [!NOTE]
> Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

## <a name="to-add-a-countdown-timer"></a>Geri sayım sayıcıeklemek için

1. Önceki yordamda yaptığınız gibi **timeLeft**adlı bir tamsayı değişkeni ekleyin. Kodunuz aşağıdaki gibi görünmelidir.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Şimdi, belirttiğiniz süreden sonra bir olayı yükselten bir zamanlayıcı gibi saniyeleri gerçekten sayan bir yönteme ihtiyacınız var.

2. Tasarım penceresinde, bir <xref:System.Windows.Forms.Timer> denetimi Araç **Kutusu'nun** **Bileşenler** kategorisinden formunuza taşıyın.

     Denetim, tasarım penceresinin altındaki gri alanda görünür.

3. Formda, az önce eklediğiniz **zamanlayıcı1** simgesini seçin ve **Interval** özelliğini **1000**olarak ayarlayın.

     Aralık değeri milisaniye olduğundan, 1000 değeri <xref:System.Windows.Forms.Timer.Tick> olayın her saniye ateşlemeye neden olur.

4. Formda, **Zamanlayıcı** denetimini çift tıklatın veya seçin ve sonra **Enter** tuşunu seçin.

     Kod düzenleyicisi görüntülenir ve az önce eklediğiniz Tick olay işleyicisi yöntemini görüntüler.

5. Yeni olay işleyicisi yöntemine aşağıdaki ifadeleri ekleyin.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Eklediğiniz şeye bağlı olarak, zamanlayıcı her saniye zaman zaman **yarıcı** değişkeninin 0'dan büyük olup olmadığını belirleyerek zamanın dolup olmadığını denetler. Eğer öyleise, zaman hala devam ediyor. Zamanlayıcı önce zaman Sol'dan 1 çıkarır ve ardından sınav sahibine kaç saniye kaldığını göstermek için **zamanEtiket** denetiminin **Metin** özelliğini güncelleştirir.

     Zaman kalmazsa, zamanlayıcı **zaman** Etiket denetiminin metnini durdurur ve zaman etiketinin metnini değiştirir, böylece **Zaman'ın kalktılığını gösterir!** Bir ileti kutusu, testin bittiğini ve cevabın açık olduğunu bildirir—bu durumda addend1 ve addend2 ekleyerek. **startButton** denetiminin **Etkin** **özelliği,** sınav sahibinin başka bir test başlatabilmesi için doğru olarak ayarlanır.

     Az önce `if else` bir ifade ekledin, bu da programlara karar vermelerini nasıl söylersin. Bir `if else` deyim aşağıdaki gibi görünür.

    > [!NOTE]
    > Aşağıdaki örnek yalnızca gösteri içindir-- projenize eklemeyin.

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

     Ek sorununa yanıtı göstermek için `else` blota eklediğiniz ifadeye yakından bakın.

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     Deyim, `addend1 + addend2` iki değişkendeki değerleri bir araya getirir. İlk bölüm`sum.Value`( ) doğru yanıtı görüntülemek için toplam NumericUpDown denetiminin **Değer** özelliğini kullanır. Daha sonra testin yanıtlarını denetlemek için aynı özelliği kullanırsınız.

     Sınav alabilenler bir <xref:System.Windows.Forms.NumericUpDown> denetim kullanarak sayıları daha kolay girebilirler, bu yüzden matematik problemlerine cevap olarak bir tane kullanırsınız. Tüm potansiyel cevaplar 0'dan 100'e kadar tam sayılardır. **Minimum,** **Maksimum**ve **Ondalık Basamaklar** özelliklerinin varsayılan değerlerini bırakarak, sınav katılımcılarının ondalık sayılar, negatif sayılar veya çok yüksek sayılar girememesini sağlarsınız. (Sınav alabilenlerin 3.1411'e girmesine izin vermek istiyorsanız, 3.1415 değil, **Ondalık Basamaklar** özelliğini 3 olarak ayarlayabilirsiniz.)

6. `StartTheQuiz()` Yöntemin sonuna üç satır ekleyin, böylece kod aşağıdaki gibi görünür.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Şimdi, testiniz başladığında, **zamanSol** değişkeni 30'a ayarlanır ve **zamanEtiket** denetiminin **Metin** özelliği 30 saniyeye ayarlanır. Sonra <xref:System.Windows.Forms.Timer.Start> Zamanlayıcı denetimi yöntemi geri sayım başlar. (Sınav henüz cevabı kontrol etmez-sonraki gelir.)

7. Programınızı kaydedin, çalıştırın ve ardından formdaki **Başlat** düğmesini seçin.

     Zamanlayıcı geri saymaya başlar. Zaman dolduğunda, sınav biter ve cevap görüntülenir. Aşağıdaki resimde devam eden test gösterilmektedir.

     ![Matematik testi devam ediyor](../ide/media/express_addcountdown.png)<br/>
*Matematik testi devam ediyor*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için Bkz. **[Adım 4: CheckTheAnswer() yöntemini ekleyin.](../ide/step-4-add-the-checktheanswer-parens-method.md)**

- Önceki öğretici adıma dönmek için [bkz.](../ide/step-2-create-a-random-addition-problem.md)
