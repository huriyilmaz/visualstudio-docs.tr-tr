---
title: '2. Adım: rastgele bir ek sorun oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54dee9c25fc9b8ddf1f8cf6c54c40d68ce53dc6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671855"
---
# <a name="step-2-create-a-random-addition-problem"></a>2. Adım: Rasgele bir Toplama Problemi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticinin ikinci bölümünde, rastgele sayıları temel alan matematik sorunları ekleyerek testi zorlayıcı hale getirebilirsiniz. Ayrıca `StartTheQuiz()` , adlı ve sorunları dolduran ve geri sayım zamanlayıcısını Başlatan bir yöntem de oluşturabilirsiniz. Bu öğreticide daha sonra çıkarma, çarpma ve bölme sorunlarını ekleyeceğiz.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-create-a-random-addition-problem"></a>Rastgele bir ek sorun oluşturmak için

1. Form tasarımcısında, formunu (Form1) seçin.

2. Menü çubuğunda, **Görünüm**, **kod**' ı seçin.

     Form1.cs veya Form1. vb, kullandığınız programlama diline bağlı olarak görünür, böylece formun arkasındaki kodu görüntüleyebilmenizi sağlayabilirsiniz.

3. `Random` `new` Aşağıdaki gibi kodun en üstüne yakın bir ifade ekleyerek bir nesne oluşturun.

     [!code-csharp[VbExpressTutorial3Step2#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial3Step2#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#1)]

     Formunuza bir nesne eklediniz `Random` ve nesne **rastgele**olarak adlandırılıyordu.

     `Random` bir nesne olarak bilinir. Daha önce bu kelimeyi duydunuz ve bir sonraki öğreticide programlamanın anlamı hakkında daha fazla bilgi edindiniz. Şimdilik, `new` düğmeler, Etiketler, paneller, Openfileiletişimler, Coloriletişimler, ses çalarlar, Randoms ve hatta formlar oluşturmak için deyimleri kullanabileceğiniz ve bu öğelerin nesneler olarak adlandırıldığına yalnızca unutmayın. Programınızı çalıştırdığınızda form başlatılır ve arkasındaki kod bir `Random` nesne oluşturur ve **rasgeleleştirici**olarak adlandırır.

     Kısa süre içinde yanıtları denetlemek için bir yöntem oluşturacaksınız, böylece test her bir sorun için oluşturduğu rastgele sayıları depolamak için değişkenleri kullanmalıdır. Bkz. [değişkenler](https://msdn.microsoft.com/library/4cfaa06d-4ae3-4307-897b-cf599dc24caa) veya [türler](https://msdn.microsoft.com/library/f782d7cc-035e-4500-b1b1-36a9881130ad). Değişkenleri düzgün şekilde kullanmak için, bunları bildirmeniz gerekir, bu da adlarını ve veri türlerini listelemesi anlamına gelir.

4. Forma iki tamsayı değişkeni ekleyin ve **addend1** ve **addend2**olarak adlandırın.

    > [!NOTE]
    > Tamsayı değişkeni, C# veya Visual Basic tamsayı olarak bilinir. Bu tür bir değişken,-2147483648 ile 2147483647 arasında pozitif veya negatif bir sayı depolar ve ondalık basamak değil yalnızca tam sayıları depolayabilirler.

     `Random`Aşağıdaki kodun gösterdiği gibi, nesneyi eklemek üzere bir tamsayı değişkeni eklemek için benzer bir sözdizimi kullanırsınız.

     [!code-csharp[VbExpressTutorial3Step2#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial3Step2#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#2)]

5. `StartTheQuiz()` `Random` `Next()` Etiketli rastgele sayıları göstermek için nesnenin metodunu kullanan ve adlı bir yöntem ekleyin. `StartTheQuiz()` sonunda tüm sorunları doldurup süreölçeri başlatır, bu nedenle bir yorum ekleyin. İşlevin aşağıdaki gibi görünmesi gerekir.

     [!code-csharp[VbExpressTutorial3Step2#3](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#3)]
     [!code-vb[VbExpressTutorial3Step2#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#3)]

     Kodda **rasgeleleştirici** sonrasında nokta (.) girdiğinizde bir IntelliSense penceresinin açılıp açıldığına ve `Random` çağırabilmeniz gereken tüm nesne yöntemlerini gösterir. Örneğin, IntelliSense `Next()` yöntemi aşağıdaki gibi listeler.

     ![Next yöntemi](../ide/media/express-randomwhite.png "Express_RandomWhite") Next yöntemi

     Bir nesneden sonra bir nokta girdiğinizde, IntelliSense, nesne üyelerinin bir listesini (özellikler, Yöntemler ve olaylar gibi) gösterir.

    > [!NOTE]
    > `Next()`Yöntemi `Random` nesnesiyle kullandığınızda `randomizer.Next(50)` (örneğin, öğesini çağırdığınızda) 50 ' den küçük bir rastgele sayı alırsınız (0 ile 49 arasında). Bu örnekte, çağırılır `randomizer.Next(51)` . İki rastgele sayının, 0 ile 100 arasında bir yanıt ekleyecek şekilde 50 değil 51 ' i kullandınız. Yöntemine 50 geçirirseniz, `Next()` 0 ile 49 arasında bir sayı seçer. bu nedenle, olası en yüksek yanıt 100 değil 98. Yöntemdeki ilk iki deyimden sonra iki tamsayı değişkeninin her biri `addend1` ve `addend2` , 0 ile 50 arasında rastgele bir sayı tutar. Bu ekran görüntüsünde Visual C# kodu gösterilir, ancak IntelliSense Visual Basic için aynı şekilde çalışmaktadır.

     Bu deyimlere daha yakından göz atın.

     [!code-csharp[VbExpressTutorial3Step2#18](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#18)]
     [!code-vb[VbExpressTutorial3Step2#18](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#18)]

     Deyimler, **plusLeftLabel** ve **plusRightLabel** 'nin **metin** özelliklerini iki rastgele sayıyı görüntüleyecek şekilde ayarlar. `ToString()`Sayıları metne dönüştürmek için tamsayının metodunu kullanmanız gerekir. (Programlamada dize metin anlamına gelir. Etiket denetimleri yalnızca metin değil, sayıları görüntüler.

6. Tasarım penceresinde **Başlat** düğmesini çift tıklayın ya da seçin ve ardından Enter tuşunu seçin.

     Bir test takici bu düğmeyi seçtiğinde, test başlaması gerekir ve bu davranışı uygulamak için yeni bir tıklama olayı işleyicisi eklediniz.

7. Aşağıdaki iki deyimi ekleyin.

     [!code-csharp[VbExpressTutorial3Step2#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial3Step2#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#4)]

     İlk ifade yeni `StartTheQuiz()` yöntemi çağırır. İkinci ifade, test bir test sırasında düğmeyi seçememesi için **startButton** denetiminin **Enabled** özelliğini **false** olarak ayarlar.

8. Kodunuzu kaydedin, çalıştırın ve sonra **Başlat** düğmesini seçin.

     Aşağıdaki çizimde gösterildiği gibi rastgele bir ek sorun belirir.

     ![Rastgele ek sorun](../ide/media/express-additionproblem.png "Express_AdditionProblem") Rastgele ek sorun

     Öğreticinin bir sonraki adımında, toplamı ekleyeceksiniz.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 3. [Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md).

- Önceki öğretici adımına dönmek için bkz. [1. Adım: proje oluşturma ve Formunuza etiket ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
