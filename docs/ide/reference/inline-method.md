---
title: Inline yöntemi
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402298"
---
# <a name="inline-method"></a>Inline yöntemi

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Satır içi yöntemi yeniden düzenleme. 

**Ne zaman:** Tek bir ifade gövdesinde bir statik, örnek ve Genişletme yönteminin kullanımlarını, özgün Yöntem bildirimini kaldırma seçeneğiyle değiştirmek istiyorsunuz.

**Neden:**  Bu yeniden düzenleme, daha temiz bir sözdizimi sağlar.

## <a name="how-to"></a>Nasıl yapılır

1. Giriş işaretini yöntemin kullanımına yerleştirin.

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

3. Aşağıdaki seçeneklerden birini belirleyin: 
    
   Satır içi yöntem bildirimini kaldırmak için **Satır içi `<QualifiedMethodName>`** seçeneğini belirleyin: 

    ![Sınıf soyut yap](media/inline-method-remove-declaration.png)

   Özgün yöntem bildirimini korumak için **Satır içine al ve koru `<QualifiedMethodName>`** seçeneğini belirleyin: 

    ![Sınıf soyut yap](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
