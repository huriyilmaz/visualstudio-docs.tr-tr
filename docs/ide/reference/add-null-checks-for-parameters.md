---
title: Tümü için null denetimleri Ekle (parametreler)
description: Kodunuzda, tüm null yapılabilir, işaretli olmayan parametrelerin null listesini kontrol eden IF deyimleri oluşturma ve ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5828a2bb28f7b3085cd5d43c452c520a730b8175
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870969"
---
# <a name="add-null-checks-for-all-parameters"></a>Tüm parametreler için null denetimleri ekleme 

Bu yeniden düzenleme için geçerlidir: 

- C# 

**Ne:** `if` Tüm null yapılabilir, işaretli olmayan parametrelerin null listesini denetleyen deyimler oluşturur ve ekler. 

**Ne zaman:** Geçerli tüm Yöntem parametreleri için hızlı bir şekilde null denetimleri eklemek istiyorsunuz.

**Neden:** Birçok parametre için null denetimleri yazmak zaman alabilir ve tekrararda olabilir. Bu yeniden düzenlemenin kullanılması hızlıdır ve programı daha sağlam hale getirir.  

## <a name="how-to"></a>Nasıl yapılır 

1. İmlecinizi yöntemin içindeki herhangi bir parametrenin üzerine yerleştirin.

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   ![Hızlı Eylemler ve yeniden düzenlemeler](media/add-null-checks-for-all-parameters.png)
   
3. **Tüm parametreler için null denetimleri ekleme** seçeneğini belirleyin.

   ![Tümü için null denetimleri Ekle](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Ayrıca bkz. 

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
