---
title: '2\. Adım: rastgele bir ek sorun oluşturma'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f19c7854f2fb3d24010a5ee0e983b8efe4209997
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776035"
---
# <a name="step-2-create-a-random-addition-problem"></a>2\. Adım: rastgele bir ek sorun oluşturma

Bu öğreticinin ikinci bölümünde, rastgele sayıları temel alan matematik sorunları ekleyerek testi zorlayıcı hale getirebilirsiniz. Ayrıca, `StartTheQuiz()` adlı ve sorunları dolduran ve geri sayım zamanlayıcısını Başlatan bir yöntem oluşturursunuz. Bu öğreticide daha sonra çıkarma, çarpma ve bölme sorunlarını ekleyeceğiz.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Rastgele bir ek sorun oluşturmak için

1. Form tasarımcısında, formunu (**Form1**) seçin.

2. Menü çubuğunda > **kodu** **görüntüle** ' yi seçin.

     *Form1.cs* veya *Form1. vb* , kullandığınız programlama diline bağlı olarak görünür, böylece formun arkasındaki kodu görüntüleyebilmenizi sağlayabilirsiniz.

3. Kodun üst kısmına, aşağıdakine benzer bir `new` ifadesini ekleyerek bir <xref:System.Random> nesnesi oluşturun.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Formunuza rastgele bir nesne eklediniz ve nesne **rastgele**olarak adlandırılıyordu.

     `Random`, nesne olarak bilinir. Daha önce bu kelimeyi duydunuz ve bir sonraki öğreticide programlamanın anlamı hakkında daha fazla bilgi edindiniz. Şimdilik, düğme, etiket, panel, Openfileiletişimler, Coloriletişimler, ses çalarlar, Randoms ve hatta formlar oluşturmak için `new` deyimlerini kullanacağınızı unutmayın ve bu öğeler nesneler olarak adlandırılır. Programınızı çalıştırdığınızda, form başlatılır ve arkasındaki kod rastgele bir nesne oluşturur ve **rasgeleleştirici**olarak adlandırır.

     Kısa süre içinde yanıtları denetlemek için bir yöntem oluşturacaksınız, böylece test her bir sorun için oluşturduğu rastgele sayıları depolamak için değişkenleri kullanmalıdır. Bkz. [değişkenler](/dotnet/visual-basic/programming-guide/language-features/variables/index) veya [türler](/dotnet/csharp/programming-guide/types/index). Değişkenleri düzgün şekilde kullanmak için, bunları bildirmeniz gerekir, bu da adlarını ve veri türlerini listelemesi anlamına gelir.

4. Forma iki tamsayı değişkeni ekleyin ve **addend1** ve **addend2**olarak adlandırın.

    > [!NOTE]
    > Tamsayı değişkeni, içinde C# bir int veya Visual Basic tamsayı olarak bilinir. Bu tür bir değişken,-2147483648 ile 2147483647 arasında pozitif veya negatif bir sayı depolar ve ondalık basamak değil yalnızca tam sayıları depolayabilirler.

     Aşağıdaki kodun gösterdiği gibi, rastgele nesneyi eklemek için yaptığınız gibi, bir tamsayı değişkeni eklemek için benzer bir sözdizimi kullanırsınız.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5. `StartTheQuiz()` adında bir yöntem ekleyin ve bu, etiket içindeki rastgele sayıları göstermek için rastgele nesnenin <xref:System.Random.Next> yöntemini kullanır. `StartTheQuiz()`, sonunda tüm sorunları doldurup süreölçeri başlatır, bu nedenle bir yorum ekleyin. İşlevin aşağıdaki gibi görünmesi gerekir.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Koddaki `randomizer` sonra nokta (.) girdiğinizde, bir IntelliSense penceresi açılır ve çağırabilmeniz için tüm rasgele nesne yöntemlerini gösterir. Örneğin, IntelliSense `Next()` yöntemini aşağıdaki şekilde listeler.

     Sonraki yöntemi ![](../ide/media/express_randomwhite.png)<br/>
*Next yöntemi*

     Bir nesneden sonra bir nokta girdiğinizde, IntelliSense, nesne üyelerinin bir listesini (özellikler, Yöntemler ve olaylar gibi) gösterir.

    > [!NOTE]
    > `Next()` yöntemini `Random` nesnesiyle kullandığınızda (örneğin, `randomizer.Next(50)`çağırdığınızda) 50 ' den küçük bir rastgele sayı alırsınız (0 ile 49 arasında). Bu örnekte `randomizer.Next(51)`çağırılır. İki rastgele sayının, 0 ile 100 arasında bir yanıt ekleyecek şekilde 50 değil 51 ' i kullandınız. `Next()` yöntemine 50 geçirirseniz, 0 ile 49 arasında bir sayı seçer. bu nedenle, olası en yüksek yanıt 100 değil 98. Yöntemdeki ilk iki deyim çalıştıktan sonra, **addend1** ve **addend2**iki tamsayı değişkeninin her biri, 0 ile 50 arasında rastgele bir sayı tutar. Bu ekran görüntüsü C# kodu gösterir, ancak IntelliSense Visual Basic için de aynı şekilde çalışmaktadır.

     Bu deyimlere daha yakından göz atın.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Deyimler, **plusLeftLabel** ve **plusRightLabel** 'nin **metin** özelliklerini iki rastgele sayıyı görüntüleyecek şekilde ayarlar. Sayıları metne dönüştürmek için tamsayının `ToString()` yöntemini kullanmanız gerekir. (Programlamada dize metin anlamına gelir. Etiket denetimleri yalnızca metin değil, sayıları görüntüler.

6. Tasarım penceresinde **Başlat** düğmesini çift tıklayın ya da seçin ve ardından **ENTER** tuşunu seçin.

     Bir test takici bu düğmeyi seçtiğinde, test başlaması gerekir ve bu davranışı uygulamak için yeni bir tıklama olayı işleyicisi eklediniz.

7. Aşağıdaki iki deyimi ekleyin.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     İlk ifade yeni `StartTheQuiz()` yöntemini çağırır. İkinci ifade, test bir test sırasında düğmeyi seçememesi için **startButton** denetiminin **Enabled** özelliğini **false** olarak ayarlar.

8. Kodunuzu kaydedin, çalıştırın ve sonra **Başlat** düğmesini seçin.

     Aşağıdaki ekran görüntüsünde gösterildiği gibi rastgele bir ek sorun belirir.

     ![rastgele ek sorun](../ide/media/express_additionproblem.png)<br/>
*Rastgele ek sorun*

     Öğreticinin bir sonraki adımında, toplamı ekleyeceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 3. **[Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md)** .

- Önceki öğretici adımına dönmek için bkz. [1. Adım: proje oluşturma ve Formunuza etiket ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
