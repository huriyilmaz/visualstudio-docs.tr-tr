---
title: 'Adım 8: Oyuncunun kazanıp kazanmadığını doğrulamak için bir yöntem ekleyin'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881fa0d90390a059bea28cb19584381f814396d3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579756"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Adım 8: Oyuncunun kazanıp kazanmadığını doğrulamak için bir yöntem ekleyin
Eğlenceli bir oyun oluşturdunuz, ancak bitirmek için bir şeye daha ihtiyaç var. Oyun oyuncu kazandığında sona ermelidir, bu `CheckForWinner()` nedenle oyuncunun kazanıp kazanmadığını doğrulamak için bir yöntem eklemeniz gerekir.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Oyuncunun kazanıp kazanmadığını doğrulamak üzere bir yöntem eklemek için

1. Aşağıdaki `CheckForWinner()` kodda gösterildiği gibi, kodunuzu `timer1_Tick()` alt, olay işleyicisi altında bir yöntem ekleyin.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > C# kodu snippet'ini veya Visual Basic kod snippet'ini görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dil kontrolü](../ide/media/docs-programming-language-control.png)     

     Yöntem, Visual `foreach` Basic'teki `For Each` C# veya döngüdeki <xref:System.Windows.Forms.TableLayoutPanel>başka bir döngüyü kullanır. Arka planla eşleşip eşleşmediğini doğrulamak için her etiketin simge rengini denetlemek için eşitlik işleci (C#`==` ve `=` Visual Basic'te) kullanır. Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir. Bu durumda, program yöntemin geri kalanını atlamak için bir `return` deyim kullanır. Döngü `return` deyimi yürütmeden tüm etiketlerden geçerse, formdaki tüm simgelerin eşleştirilmiş olduğu anlamına gelir. Program kazanan oyuncu tebrik etmek için bir MessageBox gösterir ve `Close()` daha sonra oyunu sona erdirmek için formun yöntemi çağırır.

2. Ardından, etiketin <xref:System.Windows.Forms.Control.Click> olay işleyicisinin yeni `CheckForWinner()` yöntemi aramasını varsa. Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. İkinci seçilen simgenin rengini ayarladığınız satırı arayın ve `CheckForWinner()` ardından aşağıdaki kodda gösterildiği gibi yöntemi hemen arayın.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazandığınızda, program bir tebrik **MessageBox** görüntüler (aşağıdaki ekran görüntüsünde gösterildiği gibi) ve sonra kutuyu kapatır.

     ![MessageBox ile eşleştirme oyunu](../ide/media/express_tut4step8.png)<br/>
***MessageBox*** *ile* ***eşleştirme oyunu***

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[Bkz. Adım 9: Diğer özellikleri deneyin.](../ide/step-9-try-other-features.md)**

- Önceki öğretici adıma dönmek için [bkz.](../ide/step-7-keep-pairs-visible.md)
