---
title: Parametre refactoring oluşturma
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
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094342"
---
# <a name="generate-parameter"></a>Parametre oluşturma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Otomatik olarak bir yöntem parametresi oluşturur.

**Ne zaman:** Geçerli bağlamda var olmayan bir yöntemde bir değişkene başvurur ve bir hata alırsınız; kod düzeltmesi olarak bir parametre oluşturabilirsiniz. 

**Neden:** Bağlamı kaybetmeden yöntem imzanı hızla değiştirebilirsiniz.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi değişken adına yerleştirin ve **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
1. **Parametre oluştur'u**seçin.

   ![Parametre oluşturma](media/generate-parameter.png) 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
