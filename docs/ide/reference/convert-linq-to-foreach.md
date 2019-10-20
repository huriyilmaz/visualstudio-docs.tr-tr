---
title: LINQ sorgusunu foreach ifadesine dönüştürmek için kodu yeniden düzenleme
description: Sorgu sözdiziminde yazılmış herhangi bir LINQ sorgusunu foreach ifadesine Dönüştür.
ms.date: 05/15/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a618285e1981171eb8f5f2f435fb23d412296b5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654541"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>LINQ öğesini foreach ifadesine dönüştürmek için yeniden düzenleme

[LINQ sorgu söz dizimini](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ifadesine dönüştürmek için bu yeniden düzenlemeyi kullanın.

Bu yeniden düzenleme için geçerlidir:

- C#

## <a name="how-to-use-it"></a>Nasıl kullanılır

1. @No__t_0 başlayarak LINQ sorgusunun tamamını seçin.

   > [!NOTE]
   > Bu yeniden düzenleme, yalnızca sorgu söz dizimi ile ifade edilen LINQ sorgularını dönüştürmek için kullanılabilir ve Yöntem sözdizimi değildir.

1. **Ctrl** + tuşuna basın **.** ya da kod dosyasının kenar boşluğundaki screwdriver ![screwdriver simgesine ](../media/screwdriver-icon.png) simgesine tıklayın.

   ![LINQ to foreach hızlı eylemler menüsünü Dönüştür](media/convert-linq-to-foreach.png)

1. **' Foreach ' olarak Dönüştür**' ü seçin. Ya [da Değişiklikleri Önizle iletişim kutusunu](../../ide/preview-changes.md) açmak Için **Değişiklikleri Önizle** ' yi seçin ve ardından **Uygula**' yı seçin.

> [!NOTE]
> İçin C#, bu yeniden düzenlemeler tarafından oluşturulan kod, `foreach` döngüsünün yineleme değişkeni için açık bir tür ya da [var](/dotnet/csharp/language-reference/keywords/var) kullanır. Oluşturulan koddaki tür açık veya örtük, kapsamdaki kod stili ayarlarına bağlıdır. Bu özel kod stili ayarları, **araçlar**  > **Seçenekler** altında makine düzeyinde yapılandırılır  > **metin düzenleyicisi**  > **C#**  > **kod stili** 0**genel**  **2 @no__t_ 14var ' tercihleri**veya bir [editorconfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) dosyasındaki çözüm düzeyinde. **Seçenekler**' de bir kod stili ayarını değiştirirseniz değişikliklerin etkili olması için kod dosyasını yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](/dotnet/standard/using-linq)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)