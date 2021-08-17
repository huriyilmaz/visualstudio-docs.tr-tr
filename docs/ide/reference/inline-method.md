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
ms.openlocfilehash: 2c474c43451006121f940da5eed66dfb9277806a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101212"
---
# <a name="inline-method"></a>Satır içi metot

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Satır içi yöntem yeniden düzenlemesi. 

**Ne zaman:** Tek bir deyim gövdesi içindeki statik, örnek ve uzantı yönteminin kullanımlarını özgün yöntem bildirimini kaldırma seçeneğiyle değiştirmek istediğiniz.

**Neden:**  Bu yeniden düzenleme daha net bir söz dizimi sağlar.

## <a name="how-to"></a>Nasıl yapılır

1. Yöntemin kullanımına dikkat edin.

2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.

3. Aşağıdaki seçeneklerden birini belirleyin: 
    
   Satır içi yöntem bildirimini kaldırmak için **Satır içi `<QualifiedMethodName>`** seçeneğini belirleyin: 

    !['Satır içi 'CreateWidget()' öğesini dönüştür'Visual Studio C# kod değişikliklerinin gösterildiği Hızlı Eylemler ve Yeniden Düzenleme menüsünün screeenshot'ını seçin.](media/inline-method-remove-declaration.png)

   Özgün yöntem bildirimini korumak için **Satır içine al ve koru `<QualifiedMethodName>`** seçeneğini belirleyin: 

    !['Satır içi'ni Dönüştür ve 'CreateWidget()' öğesini seçili tut ve C# kod değişiklikleri göster'i seçerek Visual Studio'daki Hızlı Eylemler ve Yeniden Düzenleme menüsünün screeenshot'ını seçin.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
