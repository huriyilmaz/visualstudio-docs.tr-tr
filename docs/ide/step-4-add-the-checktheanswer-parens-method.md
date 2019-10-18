---
title: '4\. Adım: CheckTheAnswer () metodunu ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 075c56a5d5bcb02ee443035ac26d7730f145a445
ms.sourcegitcommit: 98b02f87c7aa1f5eb7f0d1c86bfa36efa8580c57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314085"
---
# <a name="step-4-add-the-checktheanswer-method"></a>4\. Adım: CheckTheAnswer () metodunu ekleme

Bu öğreticinin dördüncü bölümünde, matematik sorunlarına verilen yanıtların doğru olup olmadığını belirleyen `CheckTheAnswer()` bir yöntem yazacaksınız. Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır.
> - Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Kodun tamamlanmış bir sürümünü indirmek için bkz. [tüm matematik testi öğreticisi örneği](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-verify-whether-the-answers-are-correct"></a>Yanıtların doğru olup olmadığını doğrulamak için

> [!NOTE]
> Visual Basic ' de takip ediyorsanız, her zamanki `Sub` anahtar sözcüğü yerine `Function` anahtar sözcüğünü kullanırsınız çünkü bu yöntem bir değer döndürür. Oldukça basittir: Sub bir değer döndürmez, ancak bir işlev yapar.

1. @No__t_0 yöntemi ekleyin.

     Bu yöntem çağrıldığında, addend1 ve addend2 değerlerini ekler ve sonucu, Sum <xref:System.Windows.Forms.NumericUpDown> denetimindeki değeri karşılaştırır. Değerler eşitse, yöntem `true` bir değer döndürür. Aksi takdirde, yöntemi `false` bir değer döndürür. Kodunuzun aşağıdaki gibi görünmesi gerekir.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Daha sonra, yeni `CheckTheAnswer()` yöntemini çağırmak için zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisine yönelik yöntemdeki kodu güncelleştirerek yanıtı kontrol edersiniz.

2. Aşağıdaki kodu `if else` ifadeye ekleyin.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Yanıt doğruysa, `CheckTheAnswer()` `true` döndürür. Olay işleyicisi zamanlayıcıyı durduruyor, kutlama iletisini gösterir ve sonra **Başlat** düğmesini tekrar kullanılabilir yapar. Aksi takdirde, test devam eder.

3. Programınızı kaydedin, çalıştırın, bir test başlatın ve ek sorun için doğru bir yanıt sağlayın.

    > [!NOTE]
    > Yanıtınızı girerken, yanıtınızı girmeden önce varsayılan değeri seçmeniz ya da sıfırı el ile silmeniz gerekir. Bu davranışı daha sonra bu öğreticide düzelteceksiniz.

     Doğru bir yanıt sağladığınızda, bir ileti kutusu açılır, **Başlat** düğmesi kullanılabilir hale gelir ve Zamanlayıcı durduruluyor.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 5. **[Adım: NumericUpDown denetimleri için olay Işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)** .

- Önceki öğretici adımına dönmek için bkz. 3. [Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md).
