---
title: LINQ sorgusunu foreach ifadesine dönüştürmek için kodu yeniden düzenleme
description: Sorgu sözdiziminde yazılmış herhangi bir LINQ sorgusunu foreach ifadesine Dönüştür.
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bb2cdf96d7f7829ff6a6d1394160548da2adae7f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595754"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>LINQ öğesini foreach ifadesine dönüştürmek için yeniden düzenleme

[LINQ sorgu söz dizimini](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) ifadesine dönüştürmek için bu yeniden düzenlemeyi kullanın.

Bu yeniden düzenleme için geçerlidir:

- C#

## <a name="how-to-use-it"></a>Kullanımı

1. `from`başlayarak LINQ sorgusunun tamamını seçin.

   > [!NOTE]
   > Bu yeniden düzenleme, yalnızca sorgu söz dizimi ile ifade edilen LINQ sorgularını dönüştürmek için kullanılabilir ve Yöntem sözdizimi değildir.

1. Tuşuna **Ctrl**+ **.** ya da kod dosyasının kenar boşluğundaki screwdriver ![screwsürücü simgesine](../media/screwdriver-icon.png) simgesine tıklayın.

   ![LINQ to foreach hızlı eylemler menüsünü Dönüştür](media/convert-linq-to-foreach.png)

1. **' Foreach ' olarak Dönüştür**' ü seçin. Ya [da Değişiklikleri Önizle iletişim kutusunu](../../ide/preview-changes.md) açmak Için **Değişiklikleri Önizle** ' yi seçin ve ardından **Uygula**' yı seçin.

> [!NOTE]
> İçin C#, bu yeniden düzenlemeler tarafından oluşturulan kod, `foreach` döngüsünün yineleme değişkeni için açık bir tür ya da [var](/dotnet/csharp/language-reference/keywords/var) kullanır. Oluşturulan koddaki tür açık veya örtük, kapsamdaki kod stili ayarlarına bağlıdır. Bu özel kod stili ayarları, **araçlar** > **Seçenekler** > **metin Düzenleyicisi** **C#**  > **kod stili** > **genel** >  **\'var olan tercihleri** > veya bir [editorconfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) dosyasındaki çözüm düzeyinde yapılandırılır. **Seçenekler**' de bir kod stili ayarını değiştirirseniz değişikliklerin etkili olması için kod dosyasını yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](/dotnet/standard/using-linq)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
