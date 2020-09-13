---
title: Ek düğmeler ve onay kutusu için kod yazma
description: Resim görüntüleyici oluşturma öğreticisinde ek düğmeler ve Cheeck kutusu için kod yazmayı öğrenin.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4d66f7705821025bd5e30ea0d0c7f2dd57d540e4
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036918"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>10. Adım: Ek düğmeler ve onay kutusu için kod yazma

Artık diğer dört yöntemi tamamlamaya hazırsınız. Bu kodu kopyalayabilir ve yapıştırabilirsiniz, ancak bu öğreticiden en iyi şekilde bilgi edinmek istiyorsanız kodu yazın ve IntelliSense kullanın.

Bu kod, daha önce eklediğiniz düğmelere işlevsellik ekler. Bu kod olmadan düğmeler hiçbir şey yapmaz. Düğmeler, <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.CheckBox.CheckedChanged> denetimleri etkinleştirdiğinizde farklı şeyler yapmak için olaylarında kod kullanır (ve onay kutusu olayı kullanır). Örneğin, `clearButton_Click` `ClearButton_Click` **Resmi Temizle** düğmesini seçtiğinizde etkinleştiren (veya) olay, **Image** özelliğini **null** (veya **Nothing**) olarak ayarlayarak geçerli görüntüyü siler. Koddaki her olay kodun ne yaptığını açıklayan yorumlar içerir.

> [!TIP]
> En iyi uygulama olarak: kodunuzda her zaman yorum yapın. Yorumlar, bir kişinin okuması ve kodunuzun daha anlaşılır olması için gereken zamana değecektir. Açıklama satırındaki her şey uygulama tarafından yok sayılır. C# ' ta, başlangıca iki eğik çizgi (//) yazarak ve Visual Basic, tek tırnak işareti (') ile başlayarak bir satırı yorumlayabilirsiniz.

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Ek düğmeler ve onay kutusu için kod yazma

Aşağıdaki kodu **Form1** kod dosyanıza ekleyin (*Form1.cs* veya *Form1. vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Kodunuz "camelCase" harflerini görüntülenmeyebilir.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için bkz. 11. **[Adım: uygulamanızı çalıştırma ve diğer özellikleri deneme](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Önceki öğretici adımına dönmek için bkz. 9. [Adım: İnceleme, yorum ve test kodunuzu test](../ide/step-9-review-comment-and-test-your-code.md)etme.

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
