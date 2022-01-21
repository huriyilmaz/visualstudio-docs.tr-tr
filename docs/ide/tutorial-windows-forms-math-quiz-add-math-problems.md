---
title: 'öğretici: Windows Forms uygulamasına matematik sorunları ekleme'
description: math test Windows Forms uygulamasına bir olay işleyicisi ve rastgele matematik sorunları eklemek için Visual Studio ıde 'yi nasıl kullanacağınızı öğrenin.
ms.custom:
- vs-acquisition
dev_langs:
- CSharp
- VB
ms.date: 01/20/2022
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6b61e41b921120c391e1b18176e076635c5d4213
ms.sourcegitcommit: 7746657b87b22a7684e79e508af598b02dfe24b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "137610052"
---
# <a name="tutorial-add-math-problems-to-a-math-quiz-winforms-app"></a>Öğretici: matematik test WinForms uygulamasına matematik sorunları ekleme

Bu dört öğreticilerde, bir matematik testi oluşturacaksınız. Test, bir sınavın belirli bir süre içinde yanıt almaya çalışacağı dört rastgele matematik sorunu içerir.

denetimler C# veya Visual Basic kodu kullanır. Bu ikinci öğreticide, rastgele sayıları temel alan matematik sorunlarına yönelik kod ekleyerek testi zorlayıcı hale getirebilirsiniz. Ayrıca `StartTheQuiz()` , sorunları dolduracak şekilde adlandırılan bir yöntem oluşturursunuz.

Bu ikinci öğreticide şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Matematik sorunlarında kullanılacak rastgele nesneler oluşturmak için kod yazın.
> - Başlat düğmesi için bir olay işleyicisi ekleyin.
> - Testi başlatmak için kod yazın.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, önceki bir öğreticide derleme yaparken [bir matematik test WinForms uygulaması oluşturur](tutorial-windows-forms-math-quiz-create-project-add-controls.md). Bu öğreticiyi tamamlamadıysanız önce bu öğreticiyi izleyin.

## <a name="create-a-random-addition-problem"></a>Rastgele bir toplama problemi oluşturma

1. Visual Studio projenizde **Windows Form Tasarımcısı**' i seçin.

1. , **Form1** formunu seçin.

1. Menü çubuğunda kodu **görüntüle**' yi seçin  >  . Kullandığınız programlama diline bağlı olarak *Form1. cs* veya *Form1. vb* görünür, böylece formun arkasındaki kodu görüntüleyebilmenizi sağlayabilirsiniz.

1. <xref:System.Random> `new` Kodun üst kısmına yakın bir ifade ekleyerek bir nesne oluşturun.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet1":::

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   `new`Düğme, etiket, panel, Openfileiletişimler, Coloriletişimler, Soundçalarlar, Randoms ve hatta formlar oluşturmak için bu gibi deyimleri kullanabilirsiniz. Bu öğelere *nesneler* denir.

   Programınızı çalıştırdığınızda form başlatılır. Arkasındaki kod, rastgele bir nesne oluşturur ve **rasgeleleştirici** adlandırır.

   Sınavın her bir sorun için oluşturduğu rastgele sayıları depolaması için değişkenlere ihtiyacı vardır. Değişkenleri kullanmadan önce, bunların adlarını ve veri türlerini listelemek anlamına gelir.

1. Forma iki tamsayı değişkeni ekleyin ve **addend1** ve **addend2** olarak adlandırın.

   > [!NOTE]
   > Tamsayı değişkeni, C# veya Visual Basic *tamsayı* *olarak bilinir* . Bu tür bir değişken,-2147483648 ile 2147483647 arasında pozitif veya negatif bir sayı depolar ve ondalık basamak değil yalnızca tam sayıları depolayabilirler.

   Aşağıdaki kodun gösterdiği gibi, rastgele nesneyi eklemek için yaptığınız gibi, bir tamsayı değişkeni eklemek için benzer sözdizimini kullanırsınız.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet2":::

1. Adlı bir yöntem ekleyin `StartTheQuiz()` . Bu yöntem, <xref:System.Random.Next> Etiketler için rastgele sayılar oluşturmak üzere rastgele nesnenin yöntemini kullanır. `StartTheQuiz()` sonunda tüm sorunları doldurup süreölçeri başlatır, bu nedenle bu bilgileri Özet yoruma ekleyin. İşlev aşağıdaki kod gibi görünmelidir.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet3":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet3":::

   `Next()`Yöntemini çağırdığınızda gibi rastgele bir nesne ile kullandığınızda, `randomizer.Next(51)` 51 ' den küçük bir rastgele sayı veya 0 ile 50 arasında bir değer alırsınız. Bu kod `randomizer.Next(51)` , iki rastgele sayının 0 ile 100 arasında bir yanıt eklemesi için çağırır.

   Bu deyimlere daha yakından göz atın.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet18":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet18":::

   Bu deyimler, **plusLeftLabel** ve **plusRightLabel** 'nin **metin** özelliklerini iki rastgele sayıyı görüntüleyecek şekilde ayarlar. Etiket denetimleri değerleri metin biçiminde görüntüler ve programlamada dizeler metin olarak tutar. Her bir tamsayının `ToString()` yöntemi, tamsayıyı bir etiketin görüntüleyeceği metne dönüştürür.

## <a name="create-random-subtraction-multiplication-and-division-problems"></a>Rastgele çıkarma, çarpma ve bölme sorunları oluşturma

Sonraki adım, değişkenleri bildirmek ve diğer matematik sorunları için rastgele değerler sağlamaktır.

1. Ek sorun değişkenlerinden sonra, formunuza kalan matematik sorunları için tamsayı değişkenleri ekleyin. Kod aşağıdaki örnekteki gibi görünmelidir.

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" range="2-27":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" range="14-38":::

1. Yöntemi, `StartTheQuiz()` "çıkarma sorununu doldur" açıklamasında başlayarak aşağıdaki kodu ekleyerek değiştirin.

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" range="35-79":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" range="51-94":::

   Bu kod, <xref:System.Random.Next> <xref:System.Random> ek problemindekinden biraz farklı şekilde sınıfının yöntemini kullanır. `Next()`Yönteme iki değer verdiğinizde, ilk değerden büyük veya buna eşit ve ikinciden küçük bir rastgele sayı seçer.

   `Next()`Yöntemi iki bağımsız değişkenle birlikte kullanarak, çıkarma sorununun pozitif bir yanıt içerdiğinden, çarpma yanıtının en çok 100 ve bölüm yanıtının bir kesir olmamasını sağlayabilirsiniz.

## <a name="add-an-event-handler-to-the-start-button"></a>Başlat düğmesine bir olay işleyicisi ekleme

Bu bölümde, Başlat düğmesi seçildiğinde testi başlatmak için kod eklersiniz. Düğme seçimi gibi bir olaya yeniden eylemde çalışan kod olay işleyicisi olarak adlandırılır.

1. **Windows Form Tasarımcısı**, **test başlat** düğmesine çift tıklayın veya seçin ve ardından **enter**' u seçin. Formun kodu görüntülenir ve yeni bir yöntem görünür.

   Bu eylemler Başlat düğmesine bir tıklama olayı işleyicisi ekler. Bir test takici bu düğmeyi seçtiğinde, uygulama bu yeni yönteme ekleyeceğiniz kodu çalıştırır.

1. Olay işleyicisinin testi başlatabilmesi için aşağıdaki iki deyimi ekleyin.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet4":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet4":::

   İlk ifade yeni `StartTheQuiz()` yöntemi çağırır. İkinci ifade, test eden bir test sırasında düğmeyi seçmemesi için **startButton** denetiminin **Enabled** özelliğini olarak ayarlar `false` .

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

1. Kodunuzu kaydedin.

1. Uygulamanızı çalıştırın ve ardından **Testi Başlat**' ı seçin. Aşağıdaki ekran görüntüsünde gösterildiği gibi rastgele matematik sorunları görüntülenir.

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/random-math-problems.png" alt-text="Dört matematik sorununun tümünde rastgele değerleri gösteren ekran görüntüsü. Sınava başla düğmesi soluk görünür.":::

## <a name="next-steps"></a>Sonraki adımlar

Matematik sınava bir süreölçer eklemek ve kullanıcı yanıtlarını denetlemek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici Bölüm 3: matematik test WinForms uygulamasına bir zamanlayıcı denetimi ekleme](tutorial-windows-forms-math-quiz-add-timer.md)