---
title: 'Adım 10: Ek düğmeler ve onay kutusu için kod yazın'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0dc7281b51d0efe0d19020df6a154e332ad9bb0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579431"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Adım 10: Ek düğmeler ve onay kutusu için kod yazın

Şimdi diğer dört yöntemi tamamlamaya hazırsınız. Bu kodu kopyalayıp yapıştırabilirsiniz, ancak bu öğreticiden en iyi şekilde yararlanmak istiyorsanız, kodu yazın ve IntelliSense'i kullanın.

Bu kod, daha önce eklediğiniz düğmelere işlevsellik ekler. Bu kod olmadan düğmeler hiçbir şey yapmaz. Düğmeler, denetimleri <xref:System.Windows.Forms.Control.Click> etkinleştirdiğinizde farklı şeyler yapmak <xref:System.Windows.Forms.CheckBox.CheckedChanged> için olaylarında kod kullanır (ve onay kutusu olayı kullanır). Örneğin, resmi `clearButton_Click` `ClearButton_Click` **Temizle** düğmesini seçtiğinizde etkinleştirilen (veya) olay, **Görüntü** özelliğini **null** (veya **hiçbir şey)** olarak ayarlayarak geçerli görüntüyü siler. Koddaki her olay, kodun ne yaptığını açıklayan açıklamalar içerir.

> [!TIP]
> En iyi yöntem olarak: Her zaman kodunuzu yorumlayın. Yorumlar bir kişinin okuyabileceği bilgilerdir ve kodunuzu anlaşılır hale getirmek için zamana değer. Yorum satırındaki her şey uygulama tarafından yoksayılır. C#'da, bir satırı başlangıçta (//) iki ileri eğik çizgi yazarak yorum lar ve Visual Basic'te tek bir tırnak işaretiyle (') başlayarak bir satırı yorumla.

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Ek düğmeler ve onay kutusu için kod yazma

**Form1** kod dosyanıza *(Form1.cs* veya *Form1.vb)* aşağıdaki kodu ekleyin.

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Kodunuz "camelCase" harflerini görüntülemeyebilir.

## <a name="next-steps"></a>Sonraki adımlar

* Bir sonraki öğretici adıma gitmek için **[Adım 11'e bakın: Uygulamanızı çalıştırın ve diğer özellikleri deneyin.](../ide/step-11-run-your-program-and-try-other-features.md)**

* Önceki öğretici adıma dönmek için [Bkz. Adım 9: Kodunuzu gözden geçirin, yorumlayın ve sınatın.](../ide/step-9-review-comment-and-test-your-code.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
