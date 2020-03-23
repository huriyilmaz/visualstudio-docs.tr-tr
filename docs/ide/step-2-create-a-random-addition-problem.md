---
title: 'Adım 2: Rasgele ekleme sorunu oluşturma'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2febef6987cf3440f92f6a6c505840cfe3ca3448
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579880"
---
# <a name="step-2-create-a-random-addition-problem"></a>Adım 2: Rasgele ekleme sorunu oluşturma

Bu öğreticinin ikinci bölümünde, rastgele sayılara dayalı matematik problemleri ekleyerek testi zorlu hale getirirsiniz. Ayrıca, adı verilen `StartTheQuiz()` ve sorunları dolduran ve geri sayım sayıcısını başlatan bir yöntem de oluşturursunuz. Bu öğreticinin ilerleyen bölümlerinde çıkarma, çarpma ve bölme sorunlarını eklersiniz.

> [!NOTE]
> Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

## <a name="to-create-a-random-addition-problem"></a>Rasgele bir ekleme sorunu oluşturmak için

1. Form tasarımcısında, formu seçin (**Form1**).

2. Menü çubuğunda**Kodu** **Görüntüle'yi** > seçin.

     *Form1.cs* veya *Form1.vb,* kullandığınız programlama diline bağlı olarak, formun arkasındaki kodu görüntüleyebilmeniz için görüntülenir.

3. Aşağıdaki <xref:System.Random> gibi kodun `new` üst yanına bir deyim ekleyerek bir nesne oluşturun.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Formunuza rastgele bir nesne eklediniz ve nesneye **randomizatör**adını verdiniz.

     `Random`nesne olarak bilinir. Muhtemelen bu kelimeyi daha önce duymuşsunuzdur ve bir sonraki eğitimde programlamanın ne anlama geldiğini daha iyi öğrenirsiniz. Şimdilik, sadece düğmeler, `new` etiketler, paneller, OpenFileDialogs, ColorDialogs, SoundPlayers, Randoms ve hatta formları oluşturmak için ifadeler kullanabilirsiniz unutmayın ve bu öğeleri nesne olarak adlandırılır. Programınızı çalıştırdığınızda, form başlatılır ve arkasındaki kod rasgele bir nesne oluşturur ve **rasgele**adlandırır.

     Yakında yanıtları denetlemek için bir yöntem oluşturacaksınız, bu nedenle testinizin her sorun için oluşturduğu rasgele sayıları depolamak için değişkenler kullanması gerekir. [Bkz. Değişkenler](/dotnet/visual-basic/programming-guide/language-features/variables/index) veya [Türler](/dotnet/csharp/programming-guide/types/index). Değişkenleri düzgün kullanmak için, adlarını ve veri türlerini listelemek anlamına gelen bunları bildirmeniz gerekir.

4. Forma iki tümsek değişken ekleyin ve **addend1** ve **addend2**adını ekleyin.

    > [!NOTE]
    > Bir toplam değişkeni C# int veya Visual Basic'te bir Integer olarak bilinir. Bu tür değişkenler pozitif veya negatif bir sayıyı -2147483648'den 2147483647'ye kadar saklar ve ondalık sayılar değil, yalnızca tam sayılar depolayabilir.

     Aşağıdaki kodun gösterdiği gibi rasgele nesne eklemek için yaptığınız gibi bir tamsayı değişkeni eklemek için benzer bir sözdizimini kullanırsınız.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5. Etiketlerdeki rasgele sayıları `StartTheQuiz()` göstermek için rasgele nesnenin <xref:System.Random.Next> yöntemini kullanan ve adlı bir yöntem ekleyin. `StartTheQuiz()`sonunda tüm sorunları doldurmak ve daha sonra zamanlayıcı başlatmak, bu yüzden bir yorum ekleyin. İşlev aşağıdaki gibi görünmelidir.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     `randomizer` Koda nokta (.) girdiğinizde, bir IntelliSense penceresi açılır ve araabileceğiniz Rastgele nesnenin tüm yöntemlerini gösterir. Örneğin, IntelliSense `Next()` yöntemi aşağıdaki gibi listeler.

     ![Sonraki yöntem](../ide/media/express_randomwhite.png)<br/>
*Sonraki yöntem*

     Bir nesneden sonra bir nokta girdiğinizde, IntelliSense nesnenin özellikleri, yöntemleri ve olayları gibi üyelerinin listesini gösterir.

    > [!NOTE]
    > Nesneyle `Next()` birlikte yöntemi kullandığınızda, örneğin aradığınızda, `randomizer.Next(50)`50'den (0'dan 49'a) daha az rastgele bir numara alırsınız. `Random` Bu örnekte, `randomizer.Next(51)`'' 51 değil, 50 kullandınız, böylece iki rasgele sayı 0'dan 100'e kadar olan bir cevaba eklenecektir. `Next()` Yönteme 50 geçerseniz, 0'dan 49'a kadar bir sayı seçer, bu nedenle mümkün olan en yüksek cevap 100 değil 98'dir. Yöntem çalışmasında ilk iki deyimden sonra, **addend1** ve **addend2**olmak üzere iki tamsayı değişkeninin her biri 0'dan 50'ye rastgele bir sayı tutar. Bu ekran görüntüsü C# kodunu gösterir, ancak IntelliSense Visual Basic için de aynı şekilde çalışır.

     Bu ifadelere daha yakından bakın.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     İfadeler, iki rasgele sayıyı görüntüleyebilmeleri için **plusLeftLabel** ve **plusRightLabel'in** **Metin** özelliklerini ayarlar. Sayıları metne dönüştürmek için `ToString()` sondayöntemini kullanmanız gerekir. (Programlamada, string metin anlamına gelir. Etiket denetimleri yalnızca metni görüntüler, sayılar değil.

6. Tasarım penceresinde, **Başlat** düğmesini çift tıklatın veya seçin ve sonra **Enter** tuşunu seçin.

     Bir sınav öğrencisi bu düğmeyi seçtiğinde, sınav başlamalıdır ve bu davranışı uygulamak için bir Click olay işleyicisi eklediniz.

7. Aşağıdaki iki ifadeyi ekleyin.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     İlk deyim yeni `StartTheQuiz()` yöntemi çağırır. İkinci deyim, test sahibinin sınav sırasında düğmeyi seçemeyebileceği için **startButton** denetiminin **Etkin** özelliğini **False** olarak ayarlar.

8. Kodunuzu kaydedin, çalıştırın ve ardından **Başlat** düğmesini seçin.

     Aşağıdaki ekran görüntüsünde gösterildiği gibi rasgele bir ekleme sorunu görüntülenir.

     ![Rasgele ekleme sorunu](../ide/media/express_additionproblem.png)<br/>
*Rasgele ekleme sorunu*

     Öğreticinin bir sonraki adımında, toplamı eklersiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz: Adım 3: Geri sayım sayıcı ekleyin.](../ide/step-3-add-a-countdown-timer.md)**

- Önceki öğretici adıma dönmek için [bkz: Adım 1: Proje oluşturun ve formunuza etiket ekleyin.](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)
