---
title: Tümü için null denetimleri Ekle (parametreler)
description: Kodunuzda, tüm null yapılabilir, işaretli olmayan parametrelerin null listesini kontrol eden IF deyimleri oluşturma ve ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a53f31b0cdd30585b6f1c5e662787d1d8195187
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785968"
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
