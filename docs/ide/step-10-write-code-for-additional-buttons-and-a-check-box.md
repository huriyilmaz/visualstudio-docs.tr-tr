---
title: '10. Adım: ek düğmeler ve onay kutusu için kod yazma'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2183c0d6ae7d3025bf80711aea6ab246ff166a3
ms.sourcegitcommit: 98b02f87c7aa1f5eb7f0d1c86bfa36efa8580c57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314188"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>10. Adım: ek düğmeler ve onay kutusu için kod yazma

Artık diğer dört yöntemi tamamlamaya hazırsınız. Bu kodu kopyalayabilir ve yapıştırabilirsiniz, ancak bu öğreticiden en iyi şekilde bilgi edinmek istiyorsanız kodu yazın ve IntelliSense kullanın.

Bu kod, daha önce eklediğiniz düğmelere işlevsellik ekler. Bu kod olmadan düğmeler hiçbir şey yapmaz. Düğmeler, denetimleri etkinleştirdiğinizde farklı şeyler yapmak için <xref:System.Windows.Forms.Control.Click> olaylarında kod kullanır (ve onay kutusu <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayını kullanır). Örneğin, **Resmi Temizle** düğmesini seçtiğinizde etkinleştiren `clearButton_Click` (veya `ClearButton_Click`) olayı, **Image** özelliğini **null** (veya **Nothing**) olarak ayarlayarak geçerli görüntüyü siler. Koddaki her olay kodun ne yaptığını açıklayan yorumlar içerir.

> [!TIP]
> En iyi uygulama olarak: kodunuzda her zaman yorum yapın. Yorumlar, bir kişinin okuması ve kodunuzun daha anlaşılır olması için gereken zamana değecektir. Açıklama satırındaki her şey uygulama tarafından yok sayılır. İçinde C#, başlangıca iki eğik çizgi (//) yazarak bir satır yorum yapın ve Visual Basic tek tırnak işaretiyle (') başlayarak bir satırı açıklama olarak görürsünüz.

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Ek düğmeler ve onay kutusu için kod yazma

Aşağıdaki kodu **Form1** kod dosyanıza ekleyin (*Form1.cs* veya *Form1. vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Kodunuz "camelCase" harflerini görüntülenmeyebilir.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için bkz. 11. **[Adım: uygulamanızı çalıştırma ve diğer özellikleri deneme](../ide/step-11-run-your-program-and-try-other-features.md)** .

* Önceki öğretici adımına dönmek için bkz. 9. [Adım: İnceleme, yorum ve test kodunuzu test](../ide/step-9-review-comment-and-test-your-code.md)etme.

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
