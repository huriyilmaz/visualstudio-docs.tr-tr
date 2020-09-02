---
title: Oluşturucudan özel alan ve Özellik Oluştur
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56bd361d2bffb4ff17b03ac6743837032d1934e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283729"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Oluşturucudan özel alan ve Özellik Oluştur

Bu yeniden düzenleme için geçerlidir: 

- C# 

**Ne:** Bir oluşturucudan özel bir alan veya özellik oluşturun. 

**Ne zaman:** Bir oluşturucudan bir özel alanı veya özelliği hızlıca eklemek ve başlatmak istiyorsunuz.

**Neden:** Özel alanlar ve Özellikler yazmak zaman alabilir ve tekrarlı olabilir. Bu yeniden düzenlemenin kullanılması hızlıdır ve programı daha sağlam hale getirir.

## <a name="how-to"></a>Nasıl yapılır 

1. İmlecinizi Oluşturucu içindeki parametre adına yerleştirin.

2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   
3. Daha sonra aşağıdakilerden birini seçin:

- **Alan oluşturun ve başlatın** veya **özellik oluşturun ve başlatın**.

   ![Oluşturucudan özel alan oluşturma](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Ayrıca bkz. 

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
