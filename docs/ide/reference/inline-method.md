---
title: Satır içi metot
description: Satır içi yöntem bildirimlerini yeniden düzenleme ve daha net bir söz dizimi Visual Studio Hızlı Eylemler ve Yeniden Düzenlemeler menüsünü kullanmayı öğrenin.
ms.date: 11/03/2020
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
ms.openlocfilehash: 5a1f72867dff23cdb39a789079e94576aa66dd01
ms.sourcegitcommit: ebd651e00fe3bae5914c211c4828219bf7d1fc70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137798567"
---
# <a name="inline-method"></a>Satır içi metot

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Satır içi yöntem yeniden düzenlemesi. 

**Tesis:** Tek bir deyim gövdesi içindeki statik, örnek ve uzantı yönteminin kullanımlarını özgün yöntem bildirimini kaldırma seçeneğiyle değiştirmek istediğiniz.

**Neden:**  Bu yeniden düzenleme daha net bir söz dizimi sağlar.

## <a name="how-to"></a>Nasıl yapılır

1. Yöntemin kullanımına dikkat edin.

2. **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.

3. Aşağıdaki seçeneklerden birini belirleyin: 
    
   Satır içi yöntem bildirimini kaldırmak için **Satır içi `<QualifiedMethodName>`** seçeneğini belirleyin: 

    !['Satır içi 'CreateWidget()' öğesini dönüştür'Visual Studio C# kod değişikliklerinin gösterildiği Hızlı Eylemler ve Yeniden Düzenleme menüsünün ekran görüntüsü.](media/inline-method-remove-declaration.png)

   Özgün yöntem bildirimini korumak için **Satır içine al ve koru `<QualifiedMethodName>`** seçeneğini belirleyin: 

    !['Satır içi dönüştürme ve 'CreateWidget()' öğesini seçili Visual Studio C# kod değişikliklerinin gösterildiği Hızlı Eylemler ve Yeniden Düzenleme menüsünün ekran görüntüsü.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
