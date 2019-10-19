---
title: '8\. Adım: oyuncunun kazandığını doğrulamak için bir yöntem ekleyin'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d53740d0970aba2c5b0442ded722c648f759f724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575129"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>8\. Adım: oyuncunun kazandığını doğrulamak için bir yöntem ekleyin
Eğlenceli bir oyun oluşturdunuz, ancak bitirmek için bir şeye daha ihtiyaç var. Oyuncu, oynatıcı WINS 'e göre sona erdirmek için, oynatıcının kazanıldığını doğrulamak üzere bir `CheckForWinner()` yöntemi eklemeniz gerekir.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Oyuncunun kazanıp kazanmadığını doğrulamak üzere bir yöntem eklemek için

1. Aşağıdaki kodda gösterildiği gibi, `timer1_Tick()` olay işleyicisinin altında, kodunuzun altına bir `CheckForWinner()` yöntemi ekleyin.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs.Microsoft.com ](../ide/media/docs-programming-language-control.png) için dil denetimi ![Programming     

     Yöntemi, <xref:System.Windows.Forms.TableLayoutPanel> her bir etikette gezinmek C# için Visual Basic içinde veya `For Each` döngüsünde başka bir `foreach` döngüsünü kullanır. Bu, arka planla eşleşip eşleşmediğini doğrulamak üzere C# her etiketin simge rengini denetlemek için eşitlik işlecini (`==` içinde `=` ve Visual Basic) kullanır. Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir. Bu durumda program, yöntemin geri kalanını atlamak için bir `return` ekstresi kullanır. Döngü `return` ifadesini yürütmeden tüm etiketleri alırsa, bu, formdaki tüm simgelerin eşleştirildiği anlamına gelir. Program, oyunu kazanmak için bir MessageBox gösterir ve ardından oyunun sona erdirmek için formun `Close()` yöntemini çağırır.

2. Sonra, etiketin <xref:System.Windows.Forms.Control.Click> olay işleyicisinin yeni `CheckForWinner()` metodunu çağırmasını sağlayabilirsiniz. Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. Aşağıdaki kodda gösterildiği gibi, seçili ikinci simgenin rengini ayarladığınız çizgiyi bulun ve ardından `CheckForWinner()` yöntemini hemen sonra çağırın.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazandığınızda, program bir kutlama **MessageBox** (aşağıdaki resimde gösterildiği gibi) görüntüler ve kutuyu kapatır.

     MessageBox ](../ide/media/express_tut4step8.png) ile ![Matching oyunu<br/>
**MessageBox** ile **eşleşen oyun**

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 9. [Adım: diğer özellikleri deneyin](../ide/step-9-try-other-features.md).

- Önceki öğretici adımına dönmek için bkz. 7. [Adım: çiftleri görünür tut](../ide/step-7-keep-pairs-visible.md).
