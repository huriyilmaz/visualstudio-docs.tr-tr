---
title: '2. Adım: Rastgele bir toplama problemi oluşturma'
description: Rastgele sayılara göre matematik sorunları ekleyerek, testi zorlayıcı hale getirme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 91d747e856d162b25db7fee059a3922f5f1ad5a6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040884"
---
# <a name="step-2-create-a-random-addition-problem"></a>2. Adım: Rastgele bir toplama problemi oluşturma

Bu öğreticinin ikinci bölümünde, rastgele sayıları temel alan matematik sorunları ekleyerek testi zorlayıcı hale getirebilirsiniz. Ayrıca `StartTheQuiz()` , adlı ve sorunları dolduran ve geri sayım zamanlayıcısını Başlatan bir yöntem de oluşturabilirsiniz. Bu öğreticide daha sonra çıkarma, çarpma ve bölme sorunlarını ekleyeceğiz.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Rastgele bir ek sorun oluşturmak için

1. Form tasarımcısında, formunu (**Form1**) seçin.

2. Menü çubuğunda kodu **görüntüle**' yi seçin  >  .

     Kullandığınız programlama diline bağlı olarak *Form1. cs* veya *Form1. vb* görünür, böylece formun arkasındaki kodu görüntüleyebilmenizi sağlayabilirsiniz.

3. <xref:System.Random> `new` Aşağıdaki gibi kodun en üstüne yakın bir ifade ekleyerek bir nesne oluşturun.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet1":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Formunuza rastgele bir nesne eklediniz ve nesne **rastgele** olarak adlandırılıyordu.

     `Random` bir nesne olarak bilinir. Daha önce bu kelimeyi duydunuz ve bir sonraki öğreticide programlamanın anlamı hakkında daha fazla bilgi edindiniz. Şimdilik, `new` düğmeler, Etiketler, paneller, Openfileiletişimler, Coloriletişimler, ses çalarlar, Randoms ve hatta formlar oluşturmak için deyimleri kullanabileceğiniz ve bu öğelerin nesneler olarak adlandırıldığına yalnızca unutmayın. Programınızı çalıştırdığınızda, form başlatılır ve arkasındaki kod rastgele bir nesne oluşturur ve **rasgeleleştirici** olarak adlandırır.

     Kısa süre içinde yanıtları denetlemek için bir yöntem oluşturacaksınız, böylece test her bir sorun için oluşturduğu rastgele sayıları depolamak için değişkenleri kullanmalıdır. Bkz. [değişkenler](/dotnet/visual-basic/programming-guide/language-features/variables/index) veya [türler](/dotnet/csharp/programming-guide/types/index). Değişkenleri düzgün şekilde kullanmak için, bunları bildirmeniz gerekir, bu da adlarını ve veri türlerini listelemesi anlamına gelir.

4. Forma iki tamsayı değişkeni ekleyin ve **addend1** ve **addend2** olarak adlandırın.

    > [!NOTE]
    > Tamsayı değişkeni, C# veya Visual Basic tamsayı olarak bilinir. Bu tür bir değişken,-2147483648 ile 2147483647 arasında pozitif veya negatif bir sayı depolar ve ondalık basamak değil yalnızca tam sayıları depolayabilirler.

     Aşağıdaki kodun gösterdiği gibi, rastgele nesneyi eklemek için yaptığınız gibi, bir tamsayı değişkeni eklemek için benzer bir sözdizimi kullanırsınız.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet2":::

5. `StartTheQuiz()` <xref:System.Random.Next> Etiketli rastgele sayıları göstermek için Random nesnesinin metodunu kullanan ve adında bir yöntem ekleyin. `StartTheQuiz()` sonunda tüm sorunları doldurup süreölçeri başlatır, bu nedenle bir yorum ekleyin. İşlevin aşağıdaki gibi görünmesi gerekir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet3":::

     Koddan sonra nokta (.) girdiğinizde `randomizer` bir IntelliSense penceresi açılır ve çağırabilmeniz için tüm rasgele nesne yöntemlerini gösterir. Örneğin, IntelliSense `Next()` yöntemi aşağıdaki gibi listeler.

     ![Next yöntemi](../ide/media/express_randomwhite.png)<br/>
*Next yöntemi*

     Bir nesneden sonra bir nokta girdiğinizde, IntelliSense, nesne üyelerinin bir listesini (özellikler, Yöntemler ve olaylar gibi) gösterir.

    > [!NOTE]
    > `Next()`Yöntemi `Random` nesnesiyle kullandığınızda `randomizer.Next(50)` (örneğin, öğesini çağırdığınızda) 50 ' den küçük bir rastgele sayı alırsınız (0 ile 49 arasında). Bu örnekte, çağırılır `randomizer.Next(51)` . İki rastgele sayının, 0 ile 100 arasında bir yanıt ekleyecek şekilde 50 değil 51 ' i kullandınız. Yöntemine 50 geçirirseniz, `Next()` 0 ile 49 arasında bir sayı seçer. bu nedenle, olası en yüksek yanıt 100 değil 98. Yöntemdeki ilk iki deyim çalıştıktan sonra, **addend1** ve **addend2** iki tamsayı değişkeninin her biri, 0 ile 50 arasında rastgele bir sayı tutar. Bu ekran görüntüsünde C# kodu gösterilmektedir, ancak IntelliSense Visual Basic için aynı şekilde çalışmaktadır.

     Bu deyimlere daha yakından göz atın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet18":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet18":::

     Deyimler, **plusLeftLabel** ve **plusRightLabel** 'nin **metin** özelliklerini iki rastgele sayıyı görüntüleyecek şekilde ayarlar. `ToString()`Sayıları metne dönüştürmek için tamsayının metodunu kullanmanız gerekir. (Programlamada dize metin anlamına gelir. Etiket denetimleri yalnızca metin değil, sayıları görüntüler.

6. Tasarım penceresinde **Başlat** düğmesini çift tıklayın ya da seçin ve ardından **ENTER** tuşunu seçin.

     Bir test takici bu düğmeyi seçtiğinde, test başlaması gerekir ve bu davranışı uygulamak için yeni bir tıklama olayı işleyicisi eklediniz.

7. Aşağıdaki iki deyimi ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet4":::

     İlk ifade yeni `StartTheQuiz()` yöntemi çağırır. İkinci ifade, test bir test sırasında düğmeyi seçememesi için **startButton** denetiminin **Enabled** özelliğini **false** olarak ayarlar.

8. Kodunuzu kaydedin, çalıştırın ve sonra **Başlat** düğmesini seçin.

     Aşağıdaki ekran görüntüsünde gösterildiği gibi rastgele bir ek sorun belirir.

     ![Rastgele ek sorun](../ide/media/express_additionproblem.png)<br/>
*Rastgele ek sorun*

     Öğreticinin bir sonraki adımında, toplamı ekleyeceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 3. **[Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md)**.

- Önceki öğretici adımına dönmek için bkz. [1. Adım: proje oluşturma ve Formunuza etiket ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
