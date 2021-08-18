---
title: '8. Adım: Oyuncunun kazanıp kazanmadığını doğrulamak için yöntem ekleme'
description: Oyuncunun kazanarak kazan olup olmadığını belirlemek için bir yöntem eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 270adddde131adf43761ce384e21ff993f161e43
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048511"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>8. Adım: Oyuncunun kazanıp kazanmadığını doğrulamak için yöntem ekleme
Eğlenceli bir oyun oluşturdunuz, ancak bitirmek için bir şeye daha ihtiyaç var. Oyuncu kazanırken oyun sona erer, bu nedenle oyuncunun kazanıp kazanmad `CheckForWinner()` olmadığını doğrulamak için bir yöntem eklemeniz gerekir.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Oyuncunun kazanıp kazanmadığını doğrulamak üzere bir yöntem eklemek için

1. Aşağıdaki `CheckForWinner()` kodda gösterildiği gibi kodunuzun en altına `timer1_Tick()` olay işleyicinin altına bir yöntem ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

      > [!IMPORTANT]
      > C# kod parçacığını veya kod parçacığını görüntülemek için bu sayfanın sağ üst kısmında yer alan programlama dili Visual Basic kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)     

     yöntemi, içinde her `foreach` etiketin üzerinden gitmek için C# Visual Basic içinde `For Each` başka bir döngü <xref:System.Windows.Forms.TableLayoutPanel> kullanır. Her etiketin simge rengini kontrol etmek için (C# ve Visual Basic) eşitlik işlecini kullanır ve arka planla eş olup olmadığını `==` `=` doğrular. Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir. Bu durumda program, yönteminin `return` geri kalanını atlamak için deyimini kullanır. Döngü deyimini yürütmeden tüm etiketlerden geçiyorsa, formda tüm `return` simgelerin eş olduğu anlamına gelir. Program, oyuncunun kazanmayı amaçladığını gösteren bir MessageBox gösterir ve ardından oyunu sona ererken formun `Close()` yöntemini çağıran bir ileti kutusu gösterir.

2. Ardından, etiketin olay <xref:System.Windows.Forms.Control.Click> işleyicisini yeni yöntemi `CheckForWinner()` çağırtır. Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. Seçilen ikinci simgenin rengini ayar seçtiğiniz satırı arayın ve ardından aşağıdaki kodda gösterildiği gibi yöntemini bundan `CheckForWinner()` hemen sonra çağırabilirsiniz.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

3. Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazanırken program, congra congraatory **MessageBox** (aşağıdaki ekran görüntüsünde gösterildiği gibi) görüntüler ve ardından kutuyu kapatır.

     ![MessageBox ile eşleştirme oyunu](../ide/media/express_tut4step8.png)<br/>
***Eşleştirme oyunu** _ _with* ***MessageBox***

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. **[9. Adım: Diğer özellikleri deneyin.](../ide/step-9-try-other-features.md)**

- Önceki öğretici adımına dönmek için bkz. [7. Adım: Çiftleri görünür durumda tutma.](../ide/step-7-keep-pairs-visible.md)
