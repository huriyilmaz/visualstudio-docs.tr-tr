---
title: '8\. Adım: testi özelleştirme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cee7b855256f352c9ac9ed39994191f4a9e6d946
ms.sourcegitcommit: 98b02f87c7aa1f5eb7f0d1c86bfa36efa8580c57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314214"
---
# <a name="step-8-customize-the-quiz"></a>8\. Adım: testi özelleştirme

Öğreticinin son bölümünde, testi özelleştirmenin ve daha önce öğrendiklerinizi genişletmenin bazı yollarını keşfedeceksiniz. Örneğin, programın yanıtın hiç bir kesir olmadığı rastgele bölüm sorunları nasıl oluşturduğunu düşünün. Daha fazla bilgi edinmek için `timeLabel` denetimini farklı bir renkle açın ve sınava ipucu sunun.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır.
> - Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Kodun tamamlanmış bir sürümünü indirmek için bkz. [tüm matematik testi öğreticisi örneği](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

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

- Bir <xref:System.Windows.Forms.NumericUpDown> denetimine doğru yanıt girildiğinde, bir sesi oynatarak sınava ipucu sunun. (Her denetimin <xref:System.Windows.Forms.NumericUpDown.ValueChanged> olayı için bir olay işleyicisi yazmanız gerekir ve bu, her bir test, denetimin değerini değiştirdiğinde ateşlenir.)

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğreticiye gitmek için bkz. **[öğretici 3: eşleşen oyun oluşturma](../ide/tutorial-3-create-a-matching-game.md)** .

- Önceki öğretici adımına dönmek için bkz. [7. Adım: çarpma ve bölme sorunları ekleme](../ide/step-7-add-multiplication-and-division-problems.md).
