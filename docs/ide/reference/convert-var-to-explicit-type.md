---
title: Var'ı açık bir türle değiştirmek için yeniden düzenleme kodu
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4ec388564e1851402f085f6bbaefba08dbea212c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595780"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Var'ı açık bir türle değiştirmek için yeniden düzenleme

Yerel bir değişken bildiriminde [var'ı](/dotnet/csharp/language-reference/keywords/var) açık bir türle değiştirmek için bu yeniden düzenlemeyi kullanın.

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

## <a name="why-to-use-an-explicit-type"></a>Neden açık bir tür kullanmak için

Aşağıda, açık bir türü olan bir değişkeni bildirmek için bazı nedenler veremenedenleri ve

- Kodun okunabilirliğini artırmak için.

- Bildirimdeki değişkeni başlatmayı istemediğiniz zaman.

Ancak, bir değişken anonim bir türle baş harfe döndüğünde ve nesnenin özelliklerine daha sonraki bir noktada erişildiğinde [var](/dotnet/csharp/language-reference/keywords/var) kullanılmalıdır. Daha fazla bilgi için bkz: [Örtülü olarak yazılan yerel değişkenler (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Özeni anahtar kelimeye `var` yerleştirin.

1. **Ctrl**+tuşuna**basın.** veya kod dosyasının kenar boşluğundaki tornavida ![simgesi simgesini](../media/screwdriver-icon.png) tıklatın.

   ![Açık tür hızlı eylemler menüsünü kullanma](media/use-explicit-type.png)

1. **Açık türü kullan'ı**seçin. Veya, [Değişiklikleri Önizleme](../../ide/preview-changes.md) iletişim kutusunu açmak için Değişiklikleri **Önizleyin'i** seçin ve ardından **Uygula'yı**seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Örtülü olarak yazılan değişkenler (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
