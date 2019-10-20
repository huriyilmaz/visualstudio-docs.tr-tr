---
title: '8\. Adım: testi özelleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6084daea11d981477bbee6f210e1faf718b58d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646917"
---
# <a name="step-8-customize-the-quiz"></a>8\. Adım: Testi Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğreticinin son bölümünde, testi özelleştirmenin ve daha önce öğrendiklerinizi genişletmenin bazı yollarını keşfedeceksiniz. Örneğin, programın yanıtın hiç bir kesir olmadığı rastgele bölüm sorunları nasıl oluşturduğunu düşünün. Daha fazla bilgi edinmek için `timeLabel` denetimini farklı bir renkle açın ve sınava ipucu sunun.

### <a name="to-customize-the-quiz"></a>Testi özelleştirmek için

- Bir test içinde yalnızca beş saniye kaldığında, **BackColor** özelliğini (`timeLabel.BackColor = Color.Red;`) ayarlayarak **timeLabel** denetimini kırmızı olarak açın. Test üzerindeyken rengi sıfırlayın.

- Bir NumericUpDown denetimine doğru yanıt girildiğinde, bir sesi oynatarak sınava ipucu sunun. (Her denetimin `ValueChanged()` olayı için bir olay işleyicisi yazmanız gerekir ve bu, her bir test, denetimin değerini değiştirdiğinde ateşlenir.)

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sınavın tamamlanmış bir sürümünü indirmek için bkz. [tüm matematik testi öğreticisi örneği](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

- Sonraki öğreticiye gitmek için bkz. [öğretici 3: eşleşen oyun oluşturma](../ide/tutorial-3-create-a-matching-game.md).

- Önceki öğretici adımına dönmek için bkz. [7. Adım: çarpma ve bölme sorunları ekleme](../ide/step-7-add-multiplication-and-division-problems.md).
