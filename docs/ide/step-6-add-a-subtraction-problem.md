---
title: '6. Adım: Çıkarma problemi ekleme'
description: Çıkarma problemi eklemeyi ve görevleri gerçekleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8fe427595ec883c3607a769ae837952e092cf1e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061850"
---
# <a name="step-6-add-a-subtraction-problem"></a>6. Adım: Çıkarma problemi ekleme
Bu öğreticinin altıncı bölümünde bir çıkarma sorunu ekleyip aşağıdaki görevlerin nasıl gerçekleştireceklerini öğrenebilirsiniz:

- Çıkarma değerlerini depolar.

- Sorun için rastgele sayılar oluşturma (ve yanıtın 0 ile 100 arasında olduğundan emin olun).

- Yanıtları kontrol alan yöntemini yeni çıkarma sorununu da kontrolacak şekilde güncelleştirin.

- Zaman dolduysa olay <xref:System.Windows.Forms.Timer.Tick> işleyicisi doğru yanıtı dolduracak şekilde zamanlayıcının olay işleyicisini güncelleştirin.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçası. Öğreticiye genel bakış için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-add-a-subtraction-problem"></a>Çıkarma problemi eklemek için

1. Toplama problemi için tamsayı değişkenleri ile zamanlayıcı arasına çıkarma problemi için iki tamsayı değişkeni ekleyin. Kodun aşağıdaki gibi olması gerekir.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet12":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Yeni tamsayı değişkenlerinin adları **(minuend** ve **subtrahend)** programlama terimleri değildir. Bunlar, çıkarılan sayı (altlık) ve alt çıkarılan sayı (minuend) için aritmetik olarak kullanılan geleneksel adlardır. Aradaki fark, yanlış uçtan alt anın eksik olduğudur. Programınız değişkenler, denetimler, bileşenler veya yöntemler için belirli adlar gerektirmeyse de başka adlar kullanabilirsiniz. Adları basamaklarla başlatmama gibi kurallara uymalı, ancak genellikle x1, x2, x3 ve x4 gibi adları kullanabilirsiniz. Ancak, genel adlar kodun okunmalarını zorlaştırabilir ve sorunları takip etmek neredeyse imkansız hale gelir. Değişken adlarını benzersiz ve yararlı tutmak için bu öğreticinin devamlarında çarpma (çarpma ve × çarpanı = ürün) ve bölme (bölünen ÷ böleni = bölüm) için geleneksel adları kullanacağız.

     Ardından, çıkarma problemi için `StartTheQuiz()` rastgele değerler sağlamak için yöntemini değiştirebilirsiniz.

2. "Çıkarma sorununu doldur" açıklamasına aşağıdaki kodu ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet13":::

     Çıkarma sorununun olumsuz yanıtlarını önlemek için, bu kod toplama sorununun yönteminden biraz farklı <xref:System.Random.Next> <xref:System.Random> olarak sınıfının yöntemini kullanır. Yönteme iki değer verebilirsiniz; ilk değerden büyük veya ona eşit ve ikinci değerden küçük `Next()` rastgele bir sayı seçer. Aşağıdaki kod, 1 ile 100 arasında rastgele bir sayı seçer ve bunu minuend değişkende depolar.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet21":::

     Bu öğreticinin başlarında "randomizer" olarak adlandırılmış Rastgele sınıfının yöntemini birden çok `Next()` şekilde çağırabilirsiniz. Birden fazla şekilde çağırabileceğiniz yöntemler aşırı yüklenmiş olarak adlandırılır ve IntelliSense'i kullanarak bunları keşfedebilirsiniz. yöntemi için IntelliSense penceresinin araç ipucuna yeniden `Next()` bakın.

     ![IntelliSense penceresi araç ipucu](../ide/media/express_overloads.png)<br/>
***IntelliSense** _ _window ipucu*

     Araç ipucu **(+ 2 aşırı yükleme)** gösterir; başka bir şekilde yöntemini `Next()` çağırabileceğiniz anlamına gelir. Aşırı yüklemeler farklı sayılar veya bağımsız değişken türleri içerir; böylece bunlar, diğerlerinden biraz farklı çalışır. Örneğin, bir yöntem tek bir tamsayı bağımsız değişkeni, aşırı yüklemelerinden biri de bir tamsayı ve bir dize olabilir. Ne yapmak istediğinize bağlı olarak doğru aşırı yüklemeyi seçersiniz. Kodu yöntemine `StartTheQuiz()` eklerken, girer girmez IntelliSense penceresinde daha fazla bilgi `randomizer.Next(` görünür. Aşırı yüklemelerde döngü yapmak için,  aşağıdaki **çizimde** gösterildiği gibi Yukarı Ok ve Aşağı Ok tuşlarını seçin:

     ![IntelliSense'te Next&#40;&#41; yöntemi için aşırı yükleme](../ide/media/express_nextoverload.png)<br/>
*Için aşırı yükleme*  * **Next()** _ _method in* ***IntelliSense***

     Bu durumda, en düşük ve en yüksek değerleri belirtebilirsiniz, çünkü son aşırı yüklemeyi seçmek istiyor.

3. Yöntemi `CheckTheAnswer()` değiştirerek doğru çıkarma yanıtını denetleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet14":::

     C# içinde `&&` `logical and` işlecidir. Bu Visual Basic, eşdeğer işleç `AndAlso` olur. Bu işleçler "addend1 ve addend2 toplamı NumericUpDown toplamına eşitse ve yanlış uç eksi alt değeri NumericUpDown farkının değerine eşitse". yöntemi `CheckTheAnswer()` yalnızca toplama ve çıkarma `true` sorunlarının yanıtları doğruysa döndürür.

4. Zaman dolduysa doğru yanıtı dolduracak şekilde zamanlayıcının Tick olay işleyicisi son bölümünü aşağıdaki kodla değiştirin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet22":::

5. Kodunuzu kaydedin ve çalıştırın.

     Programınız aşağıdaki çizimde gösterildiği gibi bir çıkarma sorunu içerir:

     ![Çıkarma problemi olan matematik testi](../ide/media/express_addsubtract.png)<br/>
***Matematik testi** _ _with çıkarma problemi*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için **[bkz. 7. Adım: Çarpma ve bölme sorunları ekleme.](../ide/step-7-add-multiplication-and-division-problems.md)**

- Önceki öğretici adımına dönmek için [bkz. 5. Adım: NumericUpDown denetimleri için Enter olay işleyicileri ekleme.](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)
