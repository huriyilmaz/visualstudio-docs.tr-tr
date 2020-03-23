---
title: Tüm (parametreler) için null denetimleri ekleme
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74782309"
---
# <a name="add-null-checks-for-all-parameters"></a>Tüm parametreler için null denetimleri ekleme 

Bu yeniden düzenleme aşağıdakiler için geçerlidir: 

- C# 

**Ne:** Geçersiz kılınabilir, denetlenemeyen parametrelerin geçersizliğini kontrol eden ifadeler oluşturur ve ekler. `if` 

**Ne zaman:** Geçerli tüm yöntem parametreleri için null denetimleri hızla eklemek istiyorsunuz.

**Neden:** Birçok parametre için null denetimleri yazma zaman alıcı ve yinelenen olabilir. Bu refactoring kullanarak hızlı ve program daha sağlam hale getirir.  

## <a name="how-to"></a>Nasıl yapılır 

1. İmlecinizi yöntemin içindeki herhangi bir parametrenin üzerine yerleştirin.

2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

   ![Hızlı eylemler ve yeniden düzenleme](media/add-null-checks-for-all-parameters.png)
   
3. Tüm parametreler **için null denetimleri ekleme**seçeneğini seçin.

   ![Tümü için null denetimleri ekleme](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Ayrıca bkz. 

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
