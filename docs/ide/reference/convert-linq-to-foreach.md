---
title: LINQ sorgusunu foreach deyimine dönüştürme
ms.custom: SEO-VS-2020
description: Sorgu söz dizimsinde yazılmış herhangi bir LINQ sorgusunu foreach deyimine dönüştürmek için kodu yeniden düzenleme.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6ef812f37ec4d13d2270ebf7e5471ec82d9efbe4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144073"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>LINQ'i foreach deyimine dönüştürmek için yeniden düzenleme

LINQ sorgu söz dizimlerini [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) [deyimine dönüştürmek](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) için bu yeniden düzenlemeyi kullanın.

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Nasıl kullanılır?

1. ile başlayan LINQ sorgusunun tamamını `from` seçin.

   > [!NOTE]
   > Bu yeniden düzenleme yalnızca sorgu söz dizimi ile ifadelanan LINQ sorgularını dönüştürmek için kullanılabilir, yöntem söz dizimi için kullanılamaz.

1. **Ctrl tuşuna** + **basın.** veya kod dosyasının kenar ![ boşluğundaki ](../media/screwdriver-icon.png) tornavida tornavida simgesine tıklayın.

   ![LINQ'i foreach hızlı eylemleri menüsüne dönüştürme](media/convert-linq-to-foreach.png)

1. **'foreach' olarak dönüştür seçeneğini seçin.** Veya Değişiklikleri **önizle'yi** seçerek Değişiklikleri [Önizle iletişim kutusunu](../../ide/preview-changes.md) açın ve uygula'ya **tıklayın.**

> [!NOTE]
> C# için, bu yeniden düzenleme tarafından oluşturulan kod, döngüde yineleme değişkeni için açık bir tür veya [var](/dotnet/csharp/language-reference/keywords/var) `foreach` kullanır. Oluşturulan kodun türü açık veya örtülü, kapsamda olan kod stili ayarlarına bağlıdır. Bu kod stili ayarları, Araçlar Seçenekler Metin Düzenleyici C# Kod Stili Genel  >    >    >    >    >    >  **\' var'ın** [](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) tercihleri altında veya editorConfig dosyasında çözüm düzeyinde makine düzeyinde yapılandırılır. Seçenekler'de bir kod stili ayarını **değiştirirseniz** değişikliklerin etkili olmak için kod dosyasını yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](/dotnet/standard/using-linq)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
