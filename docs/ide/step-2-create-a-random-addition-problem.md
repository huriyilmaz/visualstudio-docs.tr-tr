---
title: '2. Adım: Rastgele bir toplama problemi oluşturma'
description: Rastgele sayılara dayalı matematik sorunları ekleyerek testi zor hale nasıl çözebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 56089560652fd4d229e7cc4974f22169e1c6df43
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397991"
---
# <a name="step-2-create-a-random-addition-problem"></a>2. Adım: Rastgele bir toplama problemi oluşturma

Bu öğreticinin ikinci bölümünde, rastgele sayıları temel alan matematik sorunları ekleyerek testi zor hale bulacaksınız. Ayrıca, adlı ve sorunları dolduran ve geri sayım `StartTheQuiz()` zamanlayıcıyı başlatan bir yöntem de oluşturabilirsiniz. Bu öğreticinin devamlarında çıkarma, çarpma ve bölme sorunlarını ekleyip ekleyeceğiz.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçası. Öğreticiye genel bakış için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-create-a-random-addition-problem"></a>Rastgele toplama sorunu oluşturmak için

1. Form tasarımcısında formu (**Form1**) seçin.

2. Menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.**

     *Form1.cs* veya *Form1.vb,* kullandığınız programlama diline bağlı olarak görüntülenir, böylece formun arkasındaki kodu görüntüebilirsiniz.

3. Aşağıdaki <xref:System.Random> gibi kodun `new` üst kısmında deyimi ekleyerek bir nesnesi oluşturun.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet1":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Formuza bir Rastgele nesne eklediniz ve nesne rastgeleleştirici **olarak adlandırılmıştır.**

     `Random` nesne olarak bilinir. Muhtemelen bu sözcüğü daha önce duymuş ve sonraki öğreticide programlamanın ne anlama geldiğini daha fazla öğrendiniz. Şimdilik düğmeler, `new` etiketler, paneller, OpenFileDialogs, ColorDialogs, SoundPlayers, Randoms ve hatta formlar oluşturmak için deyimleri kullanabileceğinizi ve bu öğelere nesne olarak da anılanları unutmayın. Programınızı çalıştırarak form başlatıldı ve arkasındaki kod rastgele bir nesne oluşturur ve rastgele bir nesne **olarak adlar.**

     Kısa süre içinde yanıtları kontrol etmek için bir yöntem oluşturacağız. Bu nedenle testin her bir sorun için oluşturacakları rastgele sayıları depolamak için değişkenleri kullanması gerekir. Bkz. [Değişkenler](/dotnet/visual-basic/programming-guide/language-features/variables/index) veya [Türler.](/dotnet/csharp/programming-guide/types/index) Değişkenleri düzgün bir şekilde kullanmak için, bunları bildirmiş ve bu da adlarını ve veri türlerini listelemeniz gerektiği anlamına gelir.

4. Forma iki tamsayı değişkeni ekleyin ve **addend1** ve **addend2 olarak ad girin.**

    > [!NOTE]
    > Tamsayı değişkeni, C# içinde int veya bir tamsayıda tamsayı Visual Basic. Bu tür bir değişken, -2147483648 ile -2147483647 pozitif veya negatif bir sayıyı depolar ve ondalık sayıları değil yalnızca tam sayıları depolar.

     Aşağıdaki kodda da olduğu gibi rastgele nesneyi eklemek için olduğu gibi tamsayı değişkeni eklemek için benzer bir söz dizimi kullanırsiniz.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet2":::

5. Etiketlerde rastgele sayıları göstermek için Random nesnesinin yöntemini kullanan ve adlı `StartTheQuiz()` <xref:System.Random.Next> bir yöntem ekleyin. `StartTheQuiz()` sonunda tüm sorunları dolduracak ve zamanlayıcıyı başlatacak, bu nedenle bir açıklama ekleyin. İşlev aşağıdaki gibi görünüyor olabilir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet3":::

     Kodun içine nokta (.) girdikten sonra bir IntelliSense penceresi açılır ve çağırabilirsiniz Random nesnesinin tüm `randomizer` yöntemlerini gösterir. Örneğin, IntelliSense yöntemini `Next()` aşağıdaki gibi listeler.

     ![Next yöntemi](../ide/media/express_randomwhite.png)<br/>
*Next yöntemi*

     Bir nesnenin ardından nokta girerken IntelliSense, özellikler, yöntemler ve olaylar gibi nesnenin üyelerinin listesini gösterir.

    > [!NOTE]
    > yöntemini nesnesiyle birlikte kullanarak örneğin çağrısında `Next()` `Random` `randomizer.Next(50)` 50'den küçük (0 ile 49 arasında) rastgele bir sayı alırsınız. Bu örnekte adlı bir örnek `randomizer.Next(51)` kullandık. Rastgele iki sayanın 0 ile 100 arasında bir yanıt eklemesi için 50 değil 51 kullandın. yöntemine 50'yi geçersiniz, 0 ile 49 arasında bir sayı seçer, bu nedenle mümkün olan en yüksek yanıt `Next()` 100 değil 98'tir. yönteminde ilk iki deyim çalıştır edildikten sonra, **addend1** ve **addend2** olmak için iki tamsayı değişkeninin her biri 0 ile 50 arasında rastgele bir sayı tutar. Bu ekran görüntüsünde C# kodu ve IntelliSense aynı şekilde Visual Basic.

     Bu deyimlere daha yakından bakın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet18":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet18":::

     deyimleri, **plusLeftLabel** ve **plusRightLabel'in Text** özelliklerini rastgele iki sn görüntüleye kadar ayarlatır.  Sayıları metne dönüştürmek için `ToString()` tamsayının yöntemini kullan gerekir. (Programlamada dize, metin anlamına gelir. Etiket denetimleri sayı değil yalnızca metin görüntüler.

6. Tasarım penceresinde Başlat düğmesine çift tıklayın **veya** seçin ve enter **tuşuna** basın.

     Sınava alan bir kullanıcı bu düğmeyi seçerken testin başlaması gerekir ve bu davranışı uygulamak için bir Tıklama olayı işleyicisi ekledik.

7. Aşağıdaki iki deyimi ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet4":::

     İlk deyim yeni yöntemi `StartTheQuiz()` çağrılır. İkinci deyim **startButton** **denetimin Enabled** özelliğini **False** olarak ayarlar, böylece sınava alan kullanıcı test sırasında düğmeyi seçez.

8. Kodunuzu kaydedin, çalıştırın ve başlat **düğmesini** seçin.

     Aşağıdaki ekran görüntüsünde gösterildiği gibi rastgele bir toplama sorunu görüntülenir.

     ![Rastgele toplama sorunu](../ide/media/express_additionproblem.png)<br/>
*Rastgele toplama sorunu*

     Öğreticinin sonraki adımlarında toplamı eksersiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. **[3. Adım: Geri sayım zamanlayıcısı ekleme.](../ide/step-3-add-a-countdown-timer.md)**

- Önceki öğretici adımına dönmek için [bkz. 1. Adım: Proje oluşturma ve formnize etiketler ekleme.](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)
