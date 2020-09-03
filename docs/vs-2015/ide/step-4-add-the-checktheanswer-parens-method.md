---
title: '4. Adım: CheckTheAnswer () metodunu ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbfdc15b06d857b7537a4a327f3201c86d4db2d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671776"
---
# <a name="step-4-add-the-checktheanswer-method"></a>4. Adım: CheckTheAnswer() Yöntemi Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticinin dördüncü bölümünde, `CheckTheAnswer()` matematik sorunlarına verilen yanıtların doğru olup olmadığını belirleyen bir yöntemi yazacaksınız. Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Visual Basic ' de takip ediyorsanız, `Function` `Sub` Bu yöntem bir değer döndürdüğünden, her zamanki anahtar sözcüğü yerine anahtar sözcüğünü kullanırsınız. Oldukça basittir: Sub bir değer döndürmez, ancak bir işlev yapar.

### <a name="to-verify-whether-the-answers-are-correct"></a>Yanıtların doğru olup olmadığını doğrulamak için

1. Yöntemini ekleyin `CheckTheAnswer()` .

     Bu yöntem çağrıldığında, addend1 ve addend2 değerlerini ekler ve sonucu, Sum denetimindeki değer ile karşılaştırır `NumericUpDown` . Değerler eşitse, yöntemi bir değeri döndürür `true` . Aksi takdirde, yöntemi bir değeri döndürür `false` . Kodunuzun aşağıdaki gibi görünmesi gerekir.

     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]

     Daha sonra, yeni yöntemi çağırmak için zamanlayıcının Tick olayı işleyicisine yönelik yöntemdeki kodu güncelleştirerek yanıtı kontrol edersiniz `CheckTheAnswer()` .

2. Aşağıdaki kodu `if else` ifadeye ekleyin.

     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]

     Yanıt doğruysa, `CheckTheAnswer()` döndürür `true` . Olay işleyicisi zamanlayıcıyı durduruyor, kutlama iletisini gösterir ve sonra **Başlat** düğmesini tekrar kullanılabilir yapar. Aksi takdirde, test devam eder.

3. Programınızı kaydedin, çalıştırın, bir test başlatın ve ek sorun için doğru bir yanıt sağlayın.

    > [!NOTE]
    > Yanıtınızı girerken, yanıtınızı girmeden önce varsayılan değeri seçmeniz ya da sıfırı el ile silmeniz gerekir. Bu davranışı daha sonra bu öğreticide düzelteceksiniz.

     Doğru bir yanıt sağladığınızda, bir ileti kutusu açılır, **Başlat** düğmesi kullanılabilir hale gelir ve Zamanlayıcı durduruluyor.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 5. [Adım: NumericUpDown denetimleri Için olay Işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).

- Önceki öğretici adımına dönmek için bkz. 3. [Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md).
