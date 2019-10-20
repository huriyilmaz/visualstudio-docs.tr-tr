---
title: '4\. Adım: CheckTheAnswer () metodunu ekleme | Microsoft Docs'
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671776"
---
# <a name="step-4-add-the-checktheanswer-method"></a>4\. Adım: CheckTheAnswer() Yöntemi Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticinin dördüncü bölümünde, matematik sorunlarına verilen yanıtların doğru olup olmadığını belirleyen `CheckTheAnswer()` bir yöntem yazacaksınız. Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Visual Basic ' de takip ediyorsanız, her zamanki `Sub` anahtar sözcüğü yerine `Function` anahtar sözcüğünü kullanırsınız çünkü bu yöntem bir değer döndürür. Oldukça basittir: Sub bir değer döndürmez, ancak bir işlev yapar.

### <a name="to-verify-whether-the-answers-are-correct"></a>Yanıtların doğru olup olmadığını doğrulamak için

1. @No__t_0 yöntemi ekleyin.

     Bu yöntem çağrıldığında, addend1 ve addend2 değerlerini ekler ve sonucu, Sum `NumericUpDown` denetimindeki değeri karşılaştırır. Değerler eşitse, yöntem `true` bir değer döndürür. Aksi takdirde, yöntemi `false` bir değer döndürür. Kodunuzun aşağıdaki gibi görünmesi gerekir.

     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]

     Daha sonra, yeni `CheckTheAnswer()` yöntemini çağırmak üzere zamanlayıcının Tick olayı işleyicisi için yöntemindeki kodu güncelleştirerek yanıtı kontrol edersiniz.

2. Aşağıdaki kodu `if else` ifadeye ekleyin.

     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]

     Yanıt doğruysa, `CheckTheAnswer()` `true` döndürür. Olay işleyicisi zamanlayıcıyı durduruyor, kutlama iletisini gösterir ve sonra **Başlat** düğmesini tekrar kullanılabilir yapar. Aksi takdirde, test devam eder.

3. Programınızı kaydedin, çalıştırın, bir test başlatın ve ek sorun için doğru bir yanıt sağlayın.

    > [!NOTE]
    > Yanıtınızı girerken, yanıtınızı girmeden önce varsayılan değeri seçmeniz ya da sıfırı el ile silmeniz gerekir. Bu davranışı daha sonra bu öğreticide düzelteceksiniz.

     Doğru bir yanıt sağladığınızda, bir ileti kutusu açılır, **Başlat** düğmesi kullanılabilir hale gelir ve Zamanlayıcı durduruluyor.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 5. [Adım: NumericUpDown denetimleri Için olay Işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).

- Önceki öğretici adımına dönmek için bkz. 3. [Adım: geri sayım Zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md).
