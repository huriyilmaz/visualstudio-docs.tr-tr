---
title: 'Adım 8: Testi özelleştirin'
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
ms.openlocfilehash: e568a9fa844802ddab934264cbc316d3514fe577
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579372"
---
# <a name="step-8-customize-the-quiz"></a>Adım 8: Testi özelleştirin

Öğreticinin son bölümünde, testi özelleştirmenin ve zaten öğrendiklerinizi genişletmenin bazı yollarını keşfedeceksiniz. Örneğin, programın, yanıtın hiçbir zaman bir kesir olmayan rasgele bölme sorunlarını nasıl oluşturduğunu düşünün. Daha fazla bilgi `timeLabel` edinmek için denetimi farklı bir renge çevirin ve sınava girene bir ipucu verin.

> [!NOTE]
> Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

## <a name="to-customize-the-quiz"></a>Testi özelleştirmek için

- Sınavda yalnızca beş saniye kaldığında, **BackColor** özelliğini ayarlayarak **zaman Etiket** denetimini kırmızıya çevirin.

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Sınav bittiğinde rengi sıfırla.

- Doğru yanıt bir denetime girildiğinde bir ses çalarak <xref:System.Windows.Forms.NumericUpDown> sınav anına bir ipucu verin. (Her denetimolayı <xref:System.Windows.Forms.NumericUpDown.ValueChanged> için bir olay işleyicisi yazmanız gerekir ve bu olay, sınav alıcısı denetimin değerini değiştirdiğinde yanar.)

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğreticiye gitmek için **[Bkz. Öğretici 3: Eşleşen bir oyun oluşturun.](../ide/tutorial-3-create-a-matching-game.md)**

- Önceki öğretici adıma dönmek için [bkz.](../ide/step-7-add-multiplication-and-division-problems.md)
