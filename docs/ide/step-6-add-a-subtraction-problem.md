---
title: '6. Adım: Çıkarma problemi ekleme'
description: Çıkarma sorununun nasıl ekleneceğini ve ayrıca görevlerin nasıl gerçekleştirileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e959a1ef4e813510a7a5963c144022748a4b85c9
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398248"
---
# <a name="step-6-add-a-subtraction-problem"></a>6. Adım: Çıkarma problemi ekleme
Bu öğreticinin altıncı bölümünde, bir çıkarma sorunu ekleyecek ve aşağıdaki görevlerin nasıl gerçekleştirileceğini öğreneceksiniz:

- Çıkarma değerlerini saklayın.

- Sorun için rastgele sayılar oluşturun (ve yanıtın 0 ile 100 arasında olduğundan emin olun).

- Yanıtları denetleyen yöntemi, yeni çıkarma sorununu da denetleyecek şekilde güncelleştirin.

- Zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisini, zaman aşımına uğrar sonra olay işleyicisinin doğru yanıtı doldurması için güncelleştirin.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-subtraction-problem"></a>Çıkarma sorunu eklemek için

1. Ekleme sorunu ve Zamanlayıcı için tamsayı değişkenleri arasına, çıkarma sorunu için iki tamsayı değişkeni ekleyin. Kod aşağıdaki gibi görünmelidir.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet12":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Yeni tamsayı değişkenlerinin adları —**eksilen** ve **çıkarılan**— programlama terimleridir. Çıkarılan numara için aritmetik olarak geleneksel adlara sahiptir (çıkarılan) ve çıkarılan çıkarılan sayı (minuend). Aradaki fark, çıkarılan 'in eksi. Programınız değişkenler, denetimler, bileşenler veya yöntemler için özel adlar gerektirmediğinden diğer adları kullanabilirsiniz. Adları basamakla başlatma gibi kuralları izlemeniz gerekir, ancak genellikle x1, X2, X3 ve x4 gibi adları kullanabilirsiniz. Ancak, genel adlar kodun okunmasını zorlaştırabilir ve sorunları neredeyse olanaksız hale getirir. Değişken adlarını benzersiz ve yararlı tutmak için, bu öğreticide daha sonra çarpma (çoğullıve × çarpanı = ürün) ve bölüm (bölünen ÷ bölen = bölüm) için geleneksel adları kullanacaksınız.

     Daha sonra, `StartTheQuiz()` çıkarma sorunu için rastgele değerler sağlamak üzere metodunu değiştirirsiniz.

2. "Çıkarma sorununu doldur" açıklamasında sonra aşağıdaki kodu ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet13":::

     Çıkarma sorununa yönelik olumsuz yanıtları engellemek için, bu kod, <xref:System.Random.Next> <xref:System.Random> ek sorunun nasıl yaptığından farklı olarak sınıfının yöntemini kullanır. `Next()`Yönteme iki değer verdiğinizde, ilk değerden büyük veya buna eşit ve ikinciden küçük bir rastgele sayı seçer. Aşağıdaki kod, 1 ile 100 arasında rastgele bir sayı seçer ve eksilen değişkeninde depolar.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet21":::

     `Next()`Bu öğreticide daha önce "rasgeleizer" olarak adlandırdığınız Random sınıfının yöntemini birden çok şekilde çağırabilirsiniz. Birden fazla yoldan çağırabileceğiniz Yöntemler aşırı yüklenmiş olarak adlandırılır ve IntelliSense 'i kullanarak bunları keşfedebilirsiniz. Yöntemi için IntelliSense penceresinin araç ipucunda bir daha göz atın `Next()` .

     ![IntelliSense penceresi araç ipucu](../ide/media/express_overloads.png)<br/>
***IntelliSense** _ _window araç ipucu *

     Araç İpucu **(+ 2 aşırı yükleme**) gösterir. Bu, `Next()` yöntemi iki farklı şekilde çağırabilmeniz anlamına gelir. Aşırı yüklemeler farklı sayılar veya bağımsız değişken türleri içerir, böylece bir diğerinden biraz farklı çalışırlar. Örneğin, bir yöntem tek bir tamsayı bağımsız değişkeni alabilir ve aşırı yüklerinden biri tamsayı ve dize alabilir. Ne yapmak istediğinize bağlı olarak doğru aşırı yüklemeyi seçersiniz. Kodu `StartTheQuiz()` yöntemine eklediğinizde, girdiğiniz anda IntelliSense penceresinde daha fazla bilgi görüntülenir `randomizer.Next(` . Aşırı yüklemeler arasında geçiş yapmak için, aşağıdaki çizimde gösterildiği gibi **yukarı ok** ve **aşağı ok** tuşlarını seçin:

     ![IntelliSense 'de Next&#40;&#41; yöntemi için aşırı yükleme](../ide/media/express_nextoverload.png)<br/>
*Için*  * aşırı yükleme **Next ()** _ _Method * ***IntelliSense***

     Bu durumda, en düşük ve en yüksek değerleri belirtebileceğiniz için son aşırı yüklemeyi seçmek istersiniz.

3. `CheckTheAnswer()`Doğru çıkarma yanıtını denetlemek için yöntemini değiştirin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet14":::

     C# ' de `&&` `logical and` işleçtir. Visual Basic ' de, eşdeğer işleç ' dir `AndAlso` . Bu işleçler, "addend1 ve addend2 toplamının Sum NumericUpDown değerine eşit olup olmadığını ve eksilen eksi çıkarılan değerinin fark NumericUpDown değerine eşit olup olmadığını gösterir. `CheckTheAnswer()`Yöntemi, `true` yalnızca toplama ve çıkarma sorunlarına verilen yanıtların ikisi de doğru olduğunda döndürülür.

4. Zamanlayıcının Tick olay işleyicisinin son bölümünü aşağıdaki kodla değiştirin, böylece zaman aşımı olduğunda doğru yanıtı dolduracaktır.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet22":::

5. Kodunuzu kaydedin ve çalıştırın.

     Aşağıdaki çizimde gösterildiği gibi programınız bir çıkarma sorunu içerir:

     ![Çıkarma sorunu ile matematik testi](../ide/media/express_addsubtract.png)<br/>
***Matematik sınavı** _ _with çıkarma sorunu *

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. **[7. Adım: çarpma ve bölme sorunları ekleme](../ide/step-7-add-multiplication-and-division-problems.md)**.

- Önceki öğretici adımına dönmek için bkz. 5. [Adım: NumericUpDown denetimleri için olay Işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
