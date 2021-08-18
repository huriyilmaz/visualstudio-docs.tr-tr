---
title: '4. Adım: CheckTheAnswer() yöntemi ekleme'
description: Matematik sorunlarına verilen yanıtların doğru olup olmadığını belirlemekte bir CheckTheAnswer () yöntemi yazmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b6fd4ded15646f4d1387749edbfa9e174fa18322
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048602"
---
# <a name="step-4-add-the-checktheanswer-method"></a>4. Adım: CheckTheAnswer() yöntemi ekleme

Bu öğreticinin dördüncü bölümünde, `CheckTheAnswer()` matematik sorunlarına verilen yanıtların doğru olup olmadığını belirleyen bir yöntemi yazacaksınız. Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Yanıtların doğru olup olmadığını doğrulamak için

> [!NOTE]
> Visual Basic ' de takip ediyorsanız, `Function` `Sub` bu yöntem bir değer döndürdüğünden, her zamanki anahtar sözcüğü yerine anahtar sözcüğünü kullanırsınız. Oldukça basittir: Sub bir değer döndürmez, ancak bir işlev yapar.

1. Yöntemini ekleyin `CheckTheAnswer()` . Bu yöntem, yaptığınız gibi diğer yöntemleri içeren bir satır içinde olmalıdır `StartTheQuiz()` .

     Bu yöntem çağrıldığında, addend1 ve addend2 değerlerini ekler ve sonucu, Sum denetimindeki değer ile karşılaştırır <xref:System.Windows.Forms.NumericUpDown> . Değerler eşitse, yöntemi bir değeri döndürür `true` . Aksi takdirde, yöntemi bir değeri döndürür `false` . Kodunuzun aşağıdaki gibi görünmesi gerekir.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs" id="Snippet8":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Daha sonra, <xref:System.Windows.Forms.Timer.Tick> yeni yöntemi çağırmak için zamanlayıcının olay işleyicisine yönelik yöntemdeki kodu güncelleştirerek yanıtı kontrol edersiniz `CheckTheAnswer()` .

2. Aşağıdaki kodu `if else` yöntemindeki ifadeye ekleyin `Timer1_Tick()` , böylece Zamanlayıcı, Kullanıcı yanıt hakkını aldığında duraklar.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs" id="Snippet10":::

     Yanıt doğruysa, `CheckTheAnswer()` döndürür `true` . Olay işleyicisi zamanlayıcıyı durduruyor, kutlama iletisini gösterir ve sonra **Başlat** düğmesini tekrar kullanılabilir yapar. Aksi takdirde, test devam eder.

3. Programınızı kaydedin, çalıştırın, bir test başlatın ve ek sorun için doğru bir yanıt sağlayın.

    > [!NOTE]
    > Yanıtınızı girerken, yanıtınızı girmeden önce varsayılan değeri seçmeniz ya da sıfırı el ile silmeniz gerekir. Bu davranışı daha sonra bu öğreticide düzelteceksiniz.

     Doğru bir yanıt sağladığınızda, bir ileti kutusu açılır, **Başlat** düğmesi kullanılabilir hale gelir ve Zamanlayıcı durduruluyor.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 5. **[Adım: NumericUpDown denetimleri için olay Işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**.

- Önceki öğretici adımına dönmek için bkz. 3. [Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md).
