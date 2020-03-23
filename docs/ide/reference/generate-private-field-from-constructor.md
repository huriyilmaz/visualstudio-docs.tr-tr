---
title: Oluşturucudan özel alan oluşturma
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
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094023"
---
# <a name="generate-private-field-from-constructor"></a>Oluşturucudan özel alan oluşturma

Bu yeniden düzenleme aşağıdakiler için geçerlidir: 

- C# 

- Visual Basic

**Ne:** Bir oluşturucudan özel alan oluşturun. 

**Ne zaman:** Hızlı bir şekilde bir oluşturucu özel bir alan eklemek istiyorum.

**Neden:** Özel alanlar yazmak zaman alıcı ve yinelenen olabilir. Bu refactoring kullanarak hızlı ve program daha sağlam hale getirir.

## <a name="how-to"></a>Nasıl yapılır 

1. İmlecinizi oluşturucunun içindeki parametre adı üzerine yerleştirin.

2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   
3. Alan Oluşturma **ve başlatma**seçeneğini seçin.

   ![Oluşturucudan özel alan oluşturma](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Ayrıca bkz. 

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
