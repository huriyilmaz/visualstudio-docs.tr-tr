---
title: '8\. Adım: oyuncunun kazandığını doğrulamak için bir yöntem ekleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2481693961dd03815381e9f71ee67cb73464bdf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646935"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>8\. Adım: Oyuncunun Kazandığını Doğrulamak için Yöntem Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eğlenceli bir oyun oluşturdunuz, ancak bitirmek için bir şeye daha ihtiyaç var. Oyuncu, oynatıcı WINS 'e göre sona erdirmek için, oynatıcının kazanıldığını doğrulamak üzere bir `CheckForWinner()` yöntemi eklemeniz gerekir.

### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Oyuncunun kazanıp kazanmadığını doğrulamak üzere bir yöntem eklemek için

1. Aşağıdaki kodda gösterildiği gibi, `timer1_Tick()` olay işleyicisinin altında, kodunuzun altına bir `CheckForWinner()` yöntemi ekleyin.

     [!code-csharp[VbExpressTutorial4Step8#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial4Step8#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#10)]

     Yöntemi, TableLayoutPanel içindeki her bir etikette gezinmek C# için Visual veya `For Each` döngüsünde başka bir `foreach` döngüsünü kullanır Visual Basic. Her etiketin simge rengini, arka planla eşleşip eşleşmediğini C# doğrulayacak şekilde denetlemek için, eşitlik işlecini (`==` Visual içinde `=` ve Visual Basic) kullanır. Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir. Bu durumda program, yöntemin geri kalanını atlamak için bir `return` ekstresi kullanır. Döngü `return` ifadesini yürütmeden tüm etiketleri alırsa, bu, formdaki tüm simgelerin eşleştirildiği anlamına gelir. Program, oyunu kazanmak için bir MessageBox gösterir ve ardından oyunun sona erdirmek için formun `Close()` yöntemini çağırır.

2. Sonra etiketin Click olay işleyicisine yeni `CheckForWinner()` yöntemini çağrı yapın. Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. Aşağıdaki kodda gösterildiği gibi, seçili ikinci simgenin rengini ayarladığınız çizgiyi bulun ve ardından `CheckForWinner()` yöntemini hemen sonra çağırın.

     [!code-csharp[VbExpressTutorial4Step8#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial4Step8#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#11)]

3. Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazandığınızda, program kutlama amaçlı bir MessageBox görüntüler (aşağıdaki resimde gösterildiği gibi) ve sonra da kutuyu kapatır.

     ![MessageBox Ile eşleşen oyun](../ide/media/express-tut4step8.png "Express_Tut4Step8") MessageBox ile eşleşen oyun

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 9. [Adım: diğer özellikleri deneyin](../ide/step-9-try-other-features.md).

- Önceki öğretici adımına dönmek için bkz. 7. [Adım: çiftleri görünür tut](../ide/step-7-keep-pairs-visible.md).
