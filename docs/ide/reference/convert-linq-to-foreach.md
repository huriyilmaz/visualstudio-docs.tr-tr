---
title: LINQ sorgusunu foreach ifadesine Dönüştür
ms.custom: SEO-VS-2020
description: Sorgu sözdiziminde yazılmış herhangi bir LINQ sorgusunu foreach ifadesine dönüştürmek için kodu yeniden düzenleyin.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 832c4160d743ca35dbe41eb0f0cbafd81d60dd26
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102564"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>LINQ öğesini foreach ifadesine dönüştürmek için yeniden düzenleme

[LINQ sorgu söz dizimini](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ifadesine dönüştürmek için bu yeniden düzenlemeyi kullanın.

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Nasıl kullanılır?

1. İle başlayan LINQ sorgusunun tamamını seçin `from` .

   > [!NOTE]
   > Bu yeniden düzenleme, yalnızca sorgu söz dizimi ile ifade edilen LINQ sorgularını dönüştürmek için kullanılabilir ve Yöntem sözdizimi değildir.

1. **CTRL** tuşuna basın + **.** ya da ![ kod dosyasının kenar boşluğundaki screwdriver screwdriver simge ](../media/screwdriver-icon.png) simgesine tıklayın.

   ![LINQ to foreach hızlı eylemler menüsünü Dönüştür](media/convert-linq-to-foreach.png)

1. **' Foreach ' olarak Dönüştür** ' ü seçin. Ya [da Değişiklikleri Önizle iletişim kutusunu](../../ide/preview-changes.md) açmak Için **Değişiklikleri Önizle** ' yi seçin ve ardından **Uygula** ' yı seçin.

> [!NOTE]
> C# için, bu yeniden düzenlemeler tarafından oluşturulan kod, döngünün yineleme değişkeni için açık bir tür ya da [var](/dotnet/csharp/language-reference/keywords/var) kullanır `foreach` . Oluşturulan koddaki tür açık veya örtük, kapsamdaki kod stili ayarlarına bağlıdır. Bu özel kod stili ayarları, **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **C#**  >  **kod stili**  >  **genel**  >  **\' var ' tercihleri** altında makine düzeyinde veya bir [editorconfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) dosyasındaki çözüm düzeyinde yapılandırılır. **Seçenekler** ' de bir kod stili ayarını değiştirirseniz değişikliklerin etkili olması için kod dosyasını yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](/dotnet/standard/using-linq)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
