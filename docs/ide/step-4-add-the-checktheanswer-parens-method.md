---
title: '4. Adım: CheckTheAnswer() yöntemi ekleme'
description: Matematik sorunlarının yanıtlarının doğru olup olmadığını belirlemek için CheckTheAnswer()yöntemi yazmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e5f8d7a0c4856a9ff65d99512cf686ad80113d9b
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398632"
---
# <a name="step-4-add-the-checktheanswer-method"></a>4. Adım: CheckTheAnswer() yöntemi ekleme

Bu öğreticinin dördüncü bölümünde matematik problemlerinin yanıtlarının doğru olup olmadığını belirleyen `CheckTheAnswer()` bir yöntemi yazacaksiniz. Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçası. Öğreticiye genel bakış için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçası. Öğreticiye genel bakış için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-verify-whether-the-answers-are-correct"></a>Yanıtların doğru olup olmadığını doğrulamak için

> [!NOTE]
> Bu yöntem bir değer döndür Visual Basic her zamanki anahtar sözcük yerine anahtar sözcüğünü `Function` `Sub` kullanır. Bu kadar basit bir işlemdir: Alt değer değer değildir ancak işlev tarafından 30000000000000000000000000000000000000000000000000

1. yöntemini `CheckTheAnswer()` ekleyin. Bu yöntem, gibi diğer yöntemlerle aynı şekilde `StartTheQuiz()` olmalı.

     Bu yöntem çağrıldıklarında addend1 ve addend2 değerlerini ekler ve sonucu toplam denetiminde yer alan değerle <xref:System.Windows.Forms.NumericUpDown> karşılar. Değerler eşitse yöntemi değerini `true` döndürür. Aksi takdirde yöntemi değerini `false` döndürür. Kodunuz aşağıdaki gibi görünüyor olabilir.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs" id="Snippet8":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Ardından, zamanlayıcının olay işleyicisi için yönteminde yeni yöntemi çağıran kodu <xref:System.Windows.Forms.Timer.Tick> güncelleştirerek yanıtı kontrol `CheckTheAnswer()` edin.

2. Aşağıdaki kodu yönteminde deyimine ekleyin; böylece kullanıcı yanıt doğru olduğunda zamanlayıcı `if else` `Timer1_Tick()` durur.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs" id="Snippet10":::

     Yanıt doğruysa `CheckTheAnswer()` `true` döndürür. Olay işleyicisi zamanlayıcıyı durdurur, bir tebrikler iletisi gösterir ve ardından Başlat **düğmesini yeniden** kullanılabilir yapar. Aksi takdirde test devam eder.

3. Programınızı kaydedin, çalıştırın, bir teste başlayabilir ve ekleme sorununa doğru yanıtı silmiş olur.

    > [!NOTE]
    > Yanıtınızı girerken, yanıtını girmeye başlamadan önce varsayılan değeri seçmeniz veya sıfırı el ile silmeniz gerekir. Bu davranışı daha sonra bu öğreticide düzelteceğiz.

     Doğru yanıtı sağlarsanız bir ileti kutusu açılır, Başlat **düğmesi** kullanılabilir duruma gelir ve zamanlayıcı durur.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için **[bkz. 5. Adım: NumericUpDown denetimleri için Enter olay işleyicileri ekleme.](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**

- Önceki öğretici adımına dönmek için bkz. [3. Adım: Geri sayım zamanlayıcısı ekleme.](../ide/step-3-add-a-countdown-timer.md)
