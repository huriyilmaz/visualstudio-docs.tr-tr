---
title: 'Adım 6: Çıkarma sorunu ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b6dd2b572074265cca62a45b962c604abf5c849
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579824"
---
# <a name="step-6-add-a-subtraction-problem"></a>Adım 6: Çıkarma sorunu ekleme
Bu öğreticinin altıncı bölümünde, bir çıkarma sorunu ekler ve aşağıdaki görevleri nasıl gerçekleştireceğinizi öğrenirsiniz:

- Çıkarma değerlerini depolayın.

- Sorun için rasgele sayılar oluşturun (ve yanıtın 0 ile 100 arasında olduğundan emin olun).

- Yeni çıkarma sorununu da denetler şekilde yanıtları denetleyen yöntemi güncelleştirin.

- Zamanlayıcınızın <xref:System.Windows.Forms.Timer.Tick> olay işleyicisini güncelleştirin, böylece olay işleyicisi zaman dolduğunda doğru yanıtı doldurur.

> [!NOTE]
> Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

## <a name="to-add-a-subtraction-problem"></a>Çıkarma sorunu eklemek için

1. Çıkarma sorunu için, ekleme sorunu için sonda değişkenleri ile zamanlayıcı arasında iki araratör değişkeni ekleyin. Kod aşağıdaki gibi görünmelidir.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     **Minuend** ve **subtrahend**gibi yeni tamsayı değişkenlerinin adları programlama terimleri değildir. Bunlar, çıkarılan sayı (subtrahend) ve subtrahend'in çıkarıldığı sayı (minuend) için aritmetikteki geleneksel adlardır. Fark minuend eksi subtrahend olduğunu. Programınız değişkenler, denetimler, bileşenler veya yöntemler için belirli adlar gerektirmediği için başka adlar kullanabilirsiniz. Adları basamaklarla başlatmamak gibi kurallara uymanız gerekir, ancak genellikle x1, x2, x3 ve x4 gibi adlar kullanabilirsiniz. Ancak, genel adlar koduokumayı zorlaştırır ve sorunları izlemeyi neredeyse imkansız hale getirir. Değişken adlarını benzersiz ve yararlı tutmak için, bu öğreticinin ilerleyen bölümlerinde çarpma (çarpma ve × çarpan = ürün) ve bölme (temettü ÷ divisor = bölüm) için geleneksel adları kullanırsınız.

     Ardından, çıkarma sorunu `StartTheQuiz()` için rasgele değerler sağlamak için yöntemi değiştirirsiniz.

2. "Çıkarma sorununu doldurun" yorumundan sonra aşağıdaki kodu ekleyin.

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Çıkarma sorunu için negatif yanıtları önlemek için, bu kod sınıfın <xref:System.Random.Next> yöntemini <xref:System.Random> ekleme sorununun yaptığından biraz farklı olarak kullanır. Yönteme `Next()` iki değer verdiğinizde, ilk değerden büyük veya eşit ve ikinci değerden daha az rasgele bir sayı seçer. Aşağıdaki kod 1'den 100'e rastgele bir sayı seçer ve minuend değişkeninde saklar.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     Bu öğreticide `Next()` daha önce "randomize" adını vermiş olduğunuz Random sınıfının yöntemini birden çok şekilde arayabilirsiniz. Birden fazla şekilde arayabilirsiniz yöntemleri aşırı olarak adlandırılır ve bunları keşfetmek için IntelliSense kullanabilirsiniz. Yöntem için IntelliSense penceresinin araç ucuna `Next()` tekrar bakın.

     ![IntelliSense pencere araç ucu](../ide/media/express_overloads.png)<br/>
***IntelliSense*** *pencere araç ucu*

     Araç ipucu **(+ 2 aşırı yük(ler))** gösterir, bu `Next()` da yöntemi iki şekilde çağırabileceğiniz anlamına gelir. Aşırı yüklemeler farklı sayılar veya bağımsız değişken türleri içerir, böylece birbirinden biraz farklı çalışırlar. Örneğin, bir yöntem tek bir tamsayı bağımsız değişkeni alabilir ve aşırı yüklerinden biri bir tamsayı ve bir dize alabilir. Ne yapmasını istediğinize göre doğru aşırı yüklemeyi seçersiniz. `StartTheQuiz()` Kodu yönteme eklediğinizde, girdiğinizde `randomizer.Next(`IntelliSense penceresinde daha fazla bilgi görüntülenir. Aşırı yüklemeler arasında geçiş yapmak için, aşağıdaki resimde gösterildiği gibi **Yukarı Ok** ve Aşağı **Ok** tuşlarını seçin:

     ![IntelliSense Sonraki&#40;&#41; yöntemi için aşırı yükleme](../ide/media/express_nextoverload.png)<br/>
***IntelliSense'de*** ***Next()*** *yöntemi* için *aşırı yükleme*

     Bu durumda, en küçük ve en büyük değerleri belirtebileceğinizden, son aşırı yüklemeyi seçmek istiyorsunuz.

3. Doğru `CheckTheAnswer()` çıkarma yanıtını denetlemek için yöntemi değiştirin.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     C#'da `&&` `logical and` işleç tir. Visual Basic'te eşdeğer `AndAlso`işleç . Bu işleçler "Addend1 ve addend2 toplamı SayısalUpDown toplamının değerine eşitse ve minuend eksi subtrahend arasındaki numericUpDown farkının değerine eşitse." Yöntem `CheckTheAnswer()` yalnızca `true` eklemenin yanıtları ve çıkarma sorunları nın her ikisi de doğruysa döndürür.

4. Zaman aşımına geldiğinde doğru yanıtı dolduracak şekilde zamanlayıcının Tick olay işleyicisinin son bölümünü aşağıdaki kodla değiştirin.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5. Kodunuzu kaydedin ve çalıştırın.

     Programınız, aşağıdaki çizimde gösterildiği gibi bir çıkarma sorunu içerir:

     ![Çıkarma problemi ile matematik testi](../ide/media/express_addsubtract.png)<br/>
***Math quiz*** *Çıkarma problemi ile* matematik testi

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz: Adım 7: Çarpma ve bölme sorunları ekleyin.](../ide/step-7-add-multiplication-and-division-problems.md)**

- Önceki öğretici adıma dönmek için Bkz. [Adım 5: SayısalUpDown denetimleri için olay işleyicileri girin.](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)
