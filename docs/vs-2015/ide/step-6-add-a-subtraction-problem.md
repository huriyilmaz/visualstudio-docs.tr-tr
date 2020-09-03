---
title: '6. Adım: çıkarma sorunu ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ec0bdd3ebae52158c5631a880e63ee0f3a455de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671708"
---
# <a name="step-6-add-a-subtraction-problem"></a>6. Adım: Çıkarma Problemi Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticinin altıncı bölümünde, bir çıkarma sorunu ekleyecek ve aşağıdaki görevlerin nasıl gerçekleştirileceğini öğreneceksiniz:

- Çıkarma değerlerini saklayın.

- Sorun için rastgele sayılar oluşturun (ve yanıtın 0 ile 100 arasında olduğundan emin olun).

- Yanıtları denetleyen yöntemi, yeni çıkarma sorununu da denetleyecek şekilde güncelleştirin.

- Zaman aşımı olduğunda olay işleyicisinin doğru yanıtı doldurması için zamanlayıcının Tick olay işleyicisini güncelleştirin.

### <a name="to-add-a-subtraction-problem"></a>Çıkarma sorunu eklemek için

1. Ekleme sorunu ve Zamanlayıcı için tamsayı değişkenleri arasına, çıkarma sorunu için iki tamsayı değişkeni ekleyin. Kod aşağıdaki gibi görünmelidir.

     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]

     Yeni tamsayı değişkenlerinin adları —**eksilen** ve **çıkarılan**— programlama terimleridir. Çıkarılan numara için aritmetik olarak geleneksel adlara sahiptir (çıkarılan) ve çıkarılan çıkarılan sayı (minuend). Aradaki fark, çıkarılan 'in eksi. Programınız değişkenler, denetimler, bileşenler veya yöntemler için özel adlar gerektirmediğinden diğer adları kullanabilirsiniz. Adları basamakla başlatma gibi kuralları izlemeniz gerekir, ancak genellikle x1, X2, X3 ve x4 gibi adları kullanabilirsiniz. Ancak, genel adlar kodun okunmasını zorlaştırabilir ve sorunları neredeyse olanaksız hale getirir. Değişken adlarını benzersiz ve yararlı tutmak için, bu öğreticide daha sonra çarpma (çoğullıve × çarpanı = ürün) ve bölüm (bölünen ÷ bölen = bölüm) için geleneksel adları kullanacaksınız.

     Daha sonra, `StartTheQuiz()` çıkarma sorunu için rastgele değerler sağlamak üzere metodunu değiştirirsiniz.

2. "Çıkarma sorununu doldur" açıklamasında sonra aşağıdaki kodu ekleyin.

     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]

     Çıkarma sorununa yönelik olumsuz yanıtları engellemek için, bu kod, `Next()` `Random` ek sorunun nasıl yaptığından farklı olarak sınıfının yöntemini kullanır. `Next()`Yönteme iki değer verdiğinizde, ilk değerden büyük veya buna eşit ve ikinciden küçük bir rastgele sayı seçer. Aşağıdaki kod, 1 ile 100 arasında rastgele bir sayı seçer ve eksilen değişkeninde depolar.

     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]

     `Next()` `Random` Bu öğreticide daha önce "rasgeleizer" olarak adlandırdığınız sınıfının yöntemini birden çok şekilde çağırabilirsiniz. Birden fazla yoldan çağırabileceğiniz Yöntemler aşırı yüklenmiş olarak adlandırılır ve IntelliSense 'i kullanarak bunları keşfedebilirsiniz. Yöntemi için IntelliSense penceresinin araç ipucunda bir daha göz atın `Next()` .

     ![IntelliSense penceresi araç ipucu](../ide/media/express-overloads.png "Express_Overloads") IntelliSense penceresi araç ipucu

     Araç İpucu **(+ 2 aşırı yükleme**) gösterir. Bu, `Next()` yöntemi iki farklı şekilde çağırabilmeniz anlamına gelir. Aşırı yüklemeler farklı sayılar veya bağımsız değişken türleri içerir, böylece bir diğerinden biraz farklı çalışırlar. Örneğin, bir yöntem tek bir tamsayı bağımsız değişkeni alabilir, ancak aşırı yüklerinden biri tamsayı ve dize alabilir. Ne yapmak istediğinize bağlı olarak doğru aşırı yüklemeyi seçersiniz. Kodu `StartTheQuiz()` yöntemine eklediğinizde, girdiğiniz anda IntelliSense penceresinde daha fazla bilgi görüntülenir `randomizer.Next(` . Aşağıdaki çizimde gösterildiği gibi, aşırı yüklemeler arasında geçiş yapmak için yukarı ok ve aşağı ok tuşlarını seçin.

     ![IntelliSense 'de Next&#40;&#41; yöntemi Için aşırı yükleme](../ide/media/express-nextoverload.png "Express_NextOverload") IntelliSense 'de Next () yöntemi için aşırı yükleme

     Bu durumda, en düşük ve en yüksek değerleri belirtebileceğiniz için son aşırı yüklemeyi seçmek istersiniz.

3. `CheckTheAnswer()`Doğru çıkarma yanıtını denetlemek için yöntemini değiştirin.

     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]

     Visual C# ' de `&&` `logical and` işleçtir. Visual Basic ' de, eşdeğer işleç ' dir `AndAlso` . Bu işleçler, "addend1 ve addend2 toplamının Sum NumericUpDown değerine eşit olup olmadığını ve eksilen eksi çıkarılan değerinin fark NumericUpDown değerine eşit olup olmadığını gösterir. `CheckTheAnswer()`Yöntemi, `true` yalnızca toplama ve çıkarma sorunlarına verilen yanıtların ikisi de doğru olduğunda döndürülür.

4. Zamanlayıcının Tick olay işleyicisinin son bölümünü aşağıdaki kodla değiştirin, böylece zaman aşımı olduğunda doğru yanıtı dolduracaktır.

     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]

5. Kodunuzu kaydedin ve çalıştırın.

     Aşağıdaki çizimde gösterildiği gibi programınız bir çıkarma sorunu içerir.

     ![Çıkarma sorunu Ile matematik testi](../ide/media/express-addsubtract.png "Express_AddSubtract") Çıkarma sorunu ile matematik testi

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [7. Adım: çarpma ve bölme sorunları ekleme](../ide/step-7-add-multiplication-and-division-problems.md).

- Önceki öğretici adımına dönmek için bkz. 5. [Adım: NumericUpDown denetimleri Için olay Işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
