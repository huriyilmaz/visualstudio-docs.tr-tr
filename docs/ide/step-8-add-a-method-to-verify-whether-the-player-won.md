---
title: '8\. Adım: Oyuncunun kazanıp kazanmadığını doğrulamak için yöntem ekleme'
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
ms.openlocfilehash: eed7a2796f08e85441c174e882c00fa406cb2379
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289665"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>8\. Adım: Oyuncunun kazanıp kazanmadığını doğrulamak için yöntem ekleme
Eğlenceli bir oyun oluşturdunuz, ancak bitirmek için bir şeye daha ihtiyaç var. Oyuncu, oynatıcı WINS 'e göre sona erdirmek için, oynatıcının kazanıldığını doğrulamak üzere bir `CheckForWinner()` yöntemi eklemeniz gerekir.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Oyuncunun kazanıp kazanmadığını doğrulamak üzere bir yöntem eklemek için

1. Aşağıdaki kodda gösterildiği gibi, `timer1_Tick()` olay işleyicisinin altına kodunuzun altına `CheckForWinner()` yöntemi ekleyin.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs. Microsoft. com @ no__t-1 için ![Programlama dil denetimi     

     Yöntemi, <xref:System.Windows.Forms.TableLayoutPanel> ' teki her bir etikette C# gezinmek Için Visual Basic Visual veya `For Each` döngüsünde başka bir `foreach` döngüsü kullanır. Her etiketin simge rengini, arka planla eşleşip eşleşmediğini doğrulamak üzere C# denetlemek için, eşitlik Işlecini (Visual 'te `==` ve `=` ' Visual Basic) kullanır. Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir. Bu durumda program, yöntemin geri kalanını atlamak için `return` ifadesini kullanır. Döngü `return` ifadesini yürütmeden tüm etiketleri alırsa, bu, formdaki tüm simgelerin eşleştirildiği anlamına gelir. Program, oyunu kazanmak için bir MessageBox gösterir ve ardından oyunun sona erdirmek için formun `Close()` yöntemini çağırır.

2. Ardından, etiketin <xref:System.Windows.Forms.Control.Click> olay işleyicisinin yeni `CheckForWinner()` metodunu çağırmasını sağlayabilirsiniz. Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. Aşağıdaki kodda gösterildiği gibi, seçili ikinci simgenin rengini ayarladığınız çizgiyi bulun ve sonra `CheckForWinner()` yöntemini çağırın.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazandığınızda, program bir kutlama **MessageBox** (aşağıdaki resimde gösterildiği gibi) görüntüler ve kutuyu kapatır.

     MessageBox @ no__t-1 ile 0 ile eşleşen oyun @no__t<br/>
**MessageBox** ile **eşleşen oyun**

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [Adım 9: Diğer özellikleri deneyin @ no__t-0.

- Önceki öğretici adımına dönmek için bkz. [Adım 7: Çiftleri görünür tutun @ no__t-0.
