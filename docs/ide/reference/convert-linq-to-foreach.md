---
title: LINQ sorgusunun foreach deyimine dönüştürülmesi için yeniden düzenleme kodu
description: Sorgu sözdiziminde yazılmış herhangi bir LINQ sorgusunun foreach deyimine dönüştürülmesi.
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
ms.openlocfilehash: 6e1b24cb8406ff29659eb79d1d9fa856db628b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094086"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>LINQ'yi foreach deyimine dönüştürmek için yeniden düzenleme

[LINQ sorgu sözdizimini](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) deyimine dönüştürmek için bu yeniden düzenlemeyi kullanın.

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Nasıl kullanılır?

1. `from`'den başlayarak linq sorgusunun tamamını seçin.

   > [!NOTE]
   > Bu yeniden düzenleme yalnızca yöntem sözdizimi ile ifade edilen LINQ sorgularını dönüştürmek için kullanılabilir.

1. **Ctrl**+tuşuna**basın.** veya kod dosyasının kenar boşluğundaki tornavida ![simgesi simgesini](../media/screwdriver-icon.png) tıklatın.

   ![LINQ'yi her hızlı işlem menüsüne dönüştürün](media/convert-linq-to-foreach.png)

1. **'Foreach' için Dönüştür'ü**seçin. Veya, [Değişiklikleri Önizleme](../../ide/preview-changes.md) iletişim kutusunu açmak için Değişiklikleri **Önizleyin'i** seçin ve ardından **Uygula'yı**seçin.

> [!NOTE]
> C# için, bu refactorings tarafından oluşturulan kod [var](/dotnet/csharp/language-reference/keywords/var) `foreach` döngü yineleme değişkeni için açık bir tür veya var kullanır. Oluşturulan koddaki açık veya örtülü tür, kapsamda bulunan kod stili ayarlarına bağlıdır. Bu özel kod stili **ayarları, Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **C#** > **Code Style** > **General** > **\'var' tercihleri**altında makine düzeyinde veya [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) dosyasındaki çözüm düzeyinde yapılandırılır. **Seçenekler'de**kod stili ayarını değiştirirseniz, değişikliklerin etkili olması için kod dosyasını yeniden açın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](/dotnet/standard/using-linq)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
