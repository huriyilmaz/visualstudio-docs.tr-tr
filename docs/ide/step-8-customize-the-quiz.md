---
title: '8. Adım: Testi özelleştirme'
description: timeLabel denetimi farklı bir renge dönüş yapmayı ve sınava alma ipucunu vermeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 028bf80fc32bac728463f3f1fdc7748914a45666
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048498"
---
# <a name="step-8-customize-the-quiz"></a>8. Adım: Testi özelleştirme

Öğreticinin son bölümünde testi özelleştirmenin ve öğrendiklerini genişletmenin bazı yollarını keşfedersiniz. Örneğin, programın yanıtın hiçbir zaman kesirli olduğu rastgele bölme sorunları oluşturduğuna bir düşün. Daha fazla bilgi edinmek için `timeLabel` denetimi farklı bir renge döndürin ve sınava alan kullanıcıya bir ipucu verme.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçası. Öğreticiye genel bakış için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-customize-the-quiz"></a>Testi özelleştirmek için

- Testte yalnızca beş saniye kalarak BackColor özelliğini ayarerek **timeLabel** denetimi **kırmızısını** döndürebilirsiniz.

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Test son bu olduğunda rengi sıfırlayın.

- Doğru yanıt bir denetime girilirken bir ses çalarak sınava girene bir ipucu <xref:System.Windows.Forms.NumericUpDown> verir. (Her denetimin olayı için bir olay işleyicisi yazmanız gerekir. Bu işleyici, testi alan, denetimin <xref:System.Windows.Forms.NumericUpDown.ValueChanged> değerini her değiştirirken etkindir.)

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğreticiye gitmek için bkz. **[Öğretici 3: Eşleşen bir oyun oluşturma.](../ide/tutorial-3-create-a-matching-game.md)**

- Önceki öğretici adımına dönmek için [bkz. 7. Adım: Çarpma ve bölme sorunları ekleme.](../ide/step-7-add-multiplication-and-division-problems.md)
