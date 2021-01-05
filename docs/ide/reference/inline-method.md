---
title: Satır içi metot
description: Visual Studio 'daki hızlı eylemler ve yeniden düzenlemeler menüsünü kullanarak satır içi Yöntem bildirimlerini yeniden düzenleme ve daha net bir sözdizimi sağlama hakkında bilgi edinin.
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
ms.openlocfilehash: 655c6dad03b05b257aec3d92199321a0e0e93d22
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761426"
---
# <a name="inline-method"></a>Satır içi metot

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

    ![Visual Studio 'daki hızlı eylemler ve yeniden düzenlemeler menüsünün ' satır Içi ' Createpencere öğesi () ' öğesini Dönüştür ' ü ve ardından gösterilen C# kod değişikliklerini kaydır.](media/inline-method-remove-declaration.png)

   Özgün yöntem bildirimini korumak için **Satır içine al ve koru `<QualifiedMethodName>`** seçeneğini belirleyin: 

    ![Visual Studio 'daki hızlı eylemleri ve yeniden düzenlemeler menüsünü Dönüştür ' satır Içi ve ' Createpencere öğesi () ' seçili ve C# kod değişikliklerini belirtilen şekilde tutun.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
