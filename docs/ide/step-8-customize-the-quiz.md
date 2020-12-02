---
title: '8. Adım: Testi özelleştirme'
description: TimeLabel denetimini farklı bir renk ile nasıl kullanacağınızı öğrenin ve bu testi bir ipucu ile sunun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21403aeb51f342f607575d99a79ce2bdb7aaa54a
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479322"
---
# <a name="step-8-customize-the-quiz"></a>8. Adım: Testi özelleştirme

Öğreticinin son bölümünde, testi özelleştirmenin ve daha önce öğrendiklerinizi genişletmenin bazı yollarını keşfedeceksiniz. Örneğin, programın yanıtın hiç bir kesir olmadığı rastgele bölüm sorunları nasıl oluşturduğunu düşünün. Daha fazla bilgi edinmek için, `timeLabel` denetimi farklı bir renk yapın ve sınava ipucu sunun.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-customize-the-quiz"></a>Testi özelleştirmek için

- Bir test içinde yalnızca beş saniye kaldığında, **BackColor** özelliğini ayarlayarak **timeLabel** denetimini kırmızıya dönüştürün.

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Test üzerindeyken rengi sıfırlayın.

- Bir denetime doğru yanıt girildiğinde, bir sesi oynatarak sınava ipucu sunun <xref:System.Windows.Forms.NumericUpDown> . (Her denetim olayı için bir olay işleyicisi yazmanız gerekir ve bu, her bir <xref:System.Windows.Forms.NumericUpDown.ValueChanged> test, denetimin değerini değiştirdiğinde harekete geçirilir.)

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğreticiye gitmek için bkz. **[öğretici 3: eşleşen oyun oluşturma](../ide/tutorial-3-create-a-matching-game.md)**.

- Önceki öğretici adımına dönmek için bkz. [7. Adım: çarpma ve bölme sorunları ekleme](../ide/step-7-add-multiplication-and-division-problems.md).
