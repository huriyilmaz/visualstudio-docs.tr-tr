---
title: '7\. Adım: çarpma ve bölme sorunları ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f02827ebd5617485f180f4a16652b1cc841c41f4
ms.sourcegitcommit: 98b02f87c7aa1f5eb7f0d1c86bfa36efa8580c57
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314224"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>7\. Adım: çarpma ve bölme sorunları ekleme

Bu öğreticinin yedinci kısmında çarpma ve bölme sorunları ekleyeceksiniz, ancak önce bu değişikliği nasıl yapacağınızı düşünün. Değerlerin depolanmasını içeren ilk adımı göz önünde bulundurun.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır.
> - Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Kodun tamamlanmış bir sürümünü indirmek için bkz. [tüm matematik testi öğreticisi örneği](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Çarpma ve bölme sorunları eklemek için

1. Forma dört tamsayı değişken ekleyin.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Daha önce yaptığınız gibi `StartTheQuiz()` yöntemini, çarpma ve bölme sorunları için rastgele sayıları dolduracak şekilde değiştirin.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. @No__t_0 yöntemini, çarpma ve bölme sorunlarını da denetleyecek şekilde değiştirin.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Klavye kullanarak çarpma işaretini (×) ve bölme işaretini (÷) kolayca giremezsiniz, böylece görsel C# ve Visual Basic bölme için bir yıldız işareti (*) ve bölme için bir eğik çizgi (/) kabul eder.

4. Zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisinin son kısmını, zaman dolduğunda doğru yanıtı dolduracak şekilde değiştirin.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Programınızı kaydedin ve çalıştırın.

     Aşağıdaki çizimde gösterildiği gibi, test takiciler, testi tamamlamaya yönelik dört sorunu yanıtmalıdır.

     dört problemle ![Math test ](../ide/media/express_finishedquiz.png)<br/>
*Dört problemle* ***matematik sınavından***

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. **[8. Adım: sınavları özelleştirme](../ide/step-8-customize-the-quiz.md)** .

- Önceki öğretici adımına dönmek için bkz. 6. [Adım: çıkarma sorunu ekleme](../ide/step-6-add-a-subtraction-problem.md).
