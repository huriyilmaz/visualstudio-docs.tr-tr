---
title: Var olan bir açık türle değiştirmek için kodu yeniden düzenleme
description: Yerel bir değişken ifadesinde var olan bir açık tür ile değiştirmek için hızlı eylemleri nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 01eb6dbe8308520235e03f5c10662fdea7933a0912c708b9030b4b7a28c9bb15
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429984"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Var olan öğesini açık bir türle değiştirecek şekilde yeniden düzenleme

Yerel bir değişken bildiriminde [var](/dotnet/csharp/language-reference/keywords/var) olan bir açık tür ile değiştirmek için bu yeniden düzenlemeyi kullanın.

Bu yeniden düzenleme için geçerlidir:

- C#

## <a name="why-to-use-an-explicit-type"></a>Neden açık bir tür kullanılmalıdır

Aşağıda açık türde bir değişken bildirmek için bazı nedenler verilmiştir:

- Kodun okunabilirliğini geliştirmek için.

- Bildiriminde değişkeni başlatmak istemediğinizde.

Ancak, bir değişken anonim bir türle başlatıldığında ve nesnenin özelliklerine sonraki bir noktada erişildiğinde, [var](/dotnet/csharp/language-reference/keywords/var) kullanılması gerekir. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Giriş işaretini `var` anahtar sözcüğe yerleştirin.

1. **CTRL** tuşuna basın + **.** ya da ![ kod dosyasının kenar boşluğundaki screwdriver screwdriver simge ](../media/screwdriver-icon.png) simgesine tıklayın.

   ![Açık tür hızlı eylemler menüsünü kullan](media/use-explicit-type.png)

1. **Açık türü kullan**' ı seçin. Ya [da Değişiklikleri Önizle iletişim kutusunu](../../ide/preview-changes.md) açmak Için **Değişiklikleri Önizle** ' yi seçin ve ardından **Uygula**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Örtük olarak yazılan değişkenler (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
