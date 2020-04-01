---
title: '4. Adım: CheckTheAnswer() yöntemi ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 199cee66013392a253139abf8ef1b88b502abac2
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472617"
---
# <a name="step-4-add-the-checktheanswer-method"></a>4. Adım: CheckTheAnswer() yöntemi ekleme

Bu öğreticinin dördüncü bölümünde, matematik sorunlarının `CheckTheAnswer()`yanıtlarının doğru olup olmadığını belirleyen bir yöntem yazacaksınız. Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

> [!NOTE]
> Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

## <a name="to-verify-whether-the-answers-are-correct"></a>Yanıtların doğru olup olmadığını doğrulamak için

> [!NOTE]
> Visual Basic'te birlikte takip ediyorsanız, bu `Function` yöntem bir değer `Sub` döndürdüğünden, her zamanki anahtar kelime yerine anahtar kelimeyi kullanırsınız. Gerçekten bu kadar basit: bir alt bir değer döndürmez, ama bir işlev yapar.

1. `CheckTheAnswer()` Yöntemi ekleyin. Bu yöntem, yaptığınız diğer yöntemlerle aynı doğrultuda `StartTheQuiz()`olmalıdır.

     Bu yöntem çağrıldığında, addend1 ve addend2 değerlerini ekler ve sonucu toplam <xref:System.Windows.Forms.NumericUpDown> denetimindeki değerle karşılaştırır. Değerler eşitse, `true`yöntem . Aksi takdirde, yöntem `false`bir değer döndürür. Kodunuz aşağıdaki gibi görünmelidir.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Ardından, zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisinin yeni `CheckTheAnswer()` yöntemi çağırması için yöntemdeki kodu güncelleştirerek yanıtı denetlersiniz.

2. `Timer1_Tick()` Yöntemdeki `if else` ifadeye aşağıdaki kodu ekleyin, böylece kullanıcı yanıtı doğru aldığında zamanlayıcı durur.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Yanıt doğruysa, `CheckTheAnswer()` döndürür. `true` Olay işleyicisi zamanlayıcıyı durdurur, bir tebrik iletisi gösterir ve ardından **Başlat** düğmesini yeniden kullanılabilir hale getirir. Aksi takdirde, sınav devam ediyor.

3. Programınızı kaydedin, çalıştırın, bir test başlatın ve ekleme sorununa doğru bir yanıt sağlayın.

    > [!NOTE]
    > Yanıtınızı girdiğinizde, yanıtınızı girmeye başlamadan önce varsayılan değeri seçmeniz veya sıfırı el ile silmeniz gerekir. Bu davranışı daha sonra bu öğreticide düzelteceksiniz.

     Doğru bir yanıt verdiğinizde, bir ileti kutusu açılır, **Başlat** düğmesi kullanılabilir hale gelir ve zamanlayıcı durur.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[Bkz. Adım 5: SayısalUpDown denetimleri için olay işleyicileri girin.](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**

- Önceki öğretici adıma dönmek için [bkz: Adım 3: Geri sayım sayıcı ekleyin.](../ide/step-3-add-a-countdown-timer.md)
