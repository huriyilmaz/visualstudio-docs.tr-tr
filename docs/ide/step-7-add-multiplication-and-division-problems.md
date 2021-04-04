---
title: '7. Adım: Çarpma ve bölme problemleri ekleme'
description: Çarpma ve bölme sorunları eklemeyi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8027b248fd675a112d64c9889686b9ef9a9c8514
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214193"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>7. Adım: Çarpma ve bölme problemleri ekleme

Bu öğreticinin yedinci kısmında çarpma ve bölme sorunları ekleyeceksiniz, ancak önce bu değişikliği nasıl yapacağınızı düşünün. Değerlerin depolanmasını içeren ilk adımı göz önünde bulundurun.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>Çarpma ve bölme sorunları eklemek için

1. Forma dört tamsayı değişken ekleyin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet15":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Daha önce yaptığınız gibi, `StartTheQuiz()` çarpma ve bölme sorunları için yöntemi rastgele sayıları dolduracak şekilde değiştirin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet16":::

3. Yöntemi, `CheckTheAnswer()` çarpma ve bölme sorunlarını da denetleyecek şekilde değiştirin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet17":::

     Klavyeyi kullanarak çarpma işaretini (×) ve bölme işaretini (÷) kolayca giremezsiniz, böylece C# ve Visual Basic bölme için bir yıldız işareti (*) kabul eder.

4. Zamanlayıcının olay işleyicisinin son bölümünü, <xref:System.Windows.Forms.Timer.Tick> zaman dolduğunda doğru yanıtı dolduracak şekilde değiştirin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet23":::

5. Programınızı kaydedin ve çalıştırın.

     Aşağıdaki çizimde gösterildiği gibi, test takiciler, testi tamamlamaya yönelik dört sorunu yanıtmalıdır.

     ![Dört problemle matematik sınavından](../ide/media/express_finishedquiz.png)<br/>
***Matematik sınavı** _ _with dört sorun *

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. **[8. Adım: testi özelleştirme](../ide/step-8-customize-the-quiz.md)**.

- Önceki öğretici adımına dönmek için bkz. 6. [Adım: çıkarma sorunu ekleme](../ide/step-6-add-a-subtraction-problem.md).
