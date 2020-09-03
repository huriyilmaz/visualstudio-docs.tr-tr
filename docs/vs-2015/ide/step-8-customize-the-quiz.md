---
title: '8. Adım: testi özelleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ded65e85a2ae11e96c21fdd852ea12daa4bbcdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299989"
---
# <a name="step-8-customize-the-quiz"></a>8. Adım: Testi Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğreticinin son bölümünde, testi özelleştirmenin ve daha önce öğrendiklerinizi genişletmenin bazı yollarını keşfedeceksiniz. Örneğin, programın yanıtın hiç bir kesir olmadığı rastgele bölüm sorunları nasıl oluşturduğunu düşünün. Daha fazla bilgi edinmek için, `timeLabel` denetimi farklı bir renk yapın ve sınava ipucu sunun.

### <a name="to-customize-the-quiz"></a>Testi özelleştirmek için

- Bir test içinde yalnızca beş saniye kaldığında, **BackColor** özelliğini () ayarlayarak **timeLabel** denetimini kırmızı olarak açın `timeLabel.BackColor = Color.Red;` . Test üzerindeyken rengi sıfırlayın.

- Bir NumericUpDown denetimine doğru yanıt girildiğinde, bir sesi oynatarak sınava ipucu sunun. (Her denetim olayı için bir olay işleyicisi yazmanız gerekir ve bu, her bir `ValueChanged()` test, denetimin değerini değiştirdiğinde harekete geçirilir.)

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğreticiye gitmek için bkz. [öğretici 3: eşleşen oyun oluşturma](../ide/tutorial-3-create-a-matching-game.md).

- Önceki öğretici adımına dönmek için bkz. [7. Adım: çarpma ve bölme sorunları ekleme](../ide/step-7-add-multiplication-and-division-problems.md).
