---
title: Ek düğmeler ve onay kutusu için kod yazma
description: Resim görüntüleyici oluşturma öğreticisinde ek düğmeler ve onay kutusu için kod yazmayı öğrenin.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
dev_langs:
- CSharp
- VB
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 917919fbb4fc81b00f7f7e9f5600ab8017a5623a
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398383"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>10. Adım: Ek düğmeler ve onay kutusu için kod yazma

Şimdi diğer dört yöntemi tamamlamaya hazır oluruz. Bu kodu kopyalayıp yapıştırabilirsiniz, ancak bu öğreticiden en fazla bilgi edinmek için kodu yazın ve IntelliSense'i kullanın.

Bu kod, daha önce ekley kodunuzla ilgili işlevler ekler. Bu kod olmadan düğmeler herhangi bir şey yapmaz. Düğmeler kendi olaylarında kod <xref:System.Windows.Forms.Control.Click> kullanır (ve denetimler etkinleştirilene kadar farklı şeyler <xref:System.Windows.Forms.CheckBox.CheckedChanged> yapmak için onay kutusu olayı kullanır). Örneğin, Resmi temizle düğmesini seçtiğiniz zaman etkinleştirilen (veya ) olayı, Image özelliğini null (veya hiçbir şey) olarak ayarerek geçerli `clearButton_Click` `ClearButton_Click` görüntüyü **siler.**    Kodda her olay, kodun ne yaptığını açıklayan açıklamalar içerir.

> [!TIP]
> En iyi uygulama olarak: Kodunuzu her zaman açıklama olarak kullanın. Açıklamalar, bir kişinin okuması gereken bilgilerdir ve kodunuzu anlaşılır hale etmeye değer. Açıklama satırına yönelik her şey uygulama tarafından yoksayılır. C# içinde, başında (//) iki eğik çizgi yazarak bir satıra açıklama satırı Visual Basic tek tırnak işareti (') ile başlayarak bir satıra açıklama satırı yazmanız gerekir.

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Ek düğmeler ve onay kutusu için kod yazma

Form1 kod dosyanıza ( **Form1.cs** veya *Form1.vb* ) *aşağıdaki kodu ekleyin.*

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet2":::

  :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet2":::

> [!NOTE]
> Kodunuz "camelCase" harflerini görüntülemeyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için **[bkz. 11. Adım: Uygulamalarınızı çalıştırma ve diğer özellikleri deneme.](../ide/step-11-run-your-program-and-try-other-features.md)**

* Önceki öğretici adımına dönmek için [bkz. 9. Adım:](../ide/step-9-review-comment-and-test-your-code.md)Kodunuzu gözden geçirme, açıklama ve test.

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: Eşleştirme oyunu oluşturma](tutorial-3-create-a-matching-game.md)
