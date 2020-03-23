---
title: 'Adım 7: Çarpma ve bölme problemleri ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a1744b68ad043dcee21dcb5995fbd1908bd81b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579784"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Adım 7: Çarpma ve bölme problemleri ekleme

Bu öğreticinin yedinci bölümünde, çarpma ve bölme sorunları eklersiniz, ancak önce bu değişikliği nasıl yapacağınızı düşünün. Değerleri depolamayı içeren ilk adımı göz önünde bulundurun.

> [!NOTE]
> Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

## <a name="to-add-multiplication-and-division-problems"></a>Çarpma ve bölme problemlerini eklemek için

1. Forma dört tane daha tümseci değişkeni ekleyin.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Daha önce yaptığınız gibi, çarpma ve bölme sorunları için rasgele sayılar doldurmak için `StartTheQuiz()` yöntemi değiştirin.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. `CheckTheAnswer()` Çarpma ve bölme sorunlarını da denetler diye yöntemi değiştirin.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Klavyeyi kullanarak çarpma işaretini (×) ve bölme işaretini (÷) kolayca giremezsiniz, bu nedenle C# ve Visual Basic çarpma için yıldız işaretini (*) ve bölme için bir kesme işaretini (/) kabul eder.

4. Zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisinin son bölümünü değiştirin, böylece zaman dolduğunda doğru yanıtı doldurur.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Programınızı kaydedin ve çalıştırın.

     Aşağıdaki resimde de görüldüğü gibi, sınav alagelenenler testi tamamlamak için dört soruna cevap vermelidir.

     ![Dört problemli matematik testi](../ide/media/express_finishedquiz.png)<br/>
***Math quiz*** *Dört problemli* matematik testi

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz: Adım 8: Testi özelleştirin.](../ide/step-8-customize-the-quiz.md)**

- Önceki öğretici adıma dönmek için [bkz.](../ide/step-6-add-a-subtraction-problem.md)
