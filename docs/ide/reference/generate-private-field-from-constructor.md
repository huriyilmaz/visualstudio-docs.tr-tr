---
title: Oluşturucudan özel alan oluştur
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527663"
---
# <a name="generate-private-field-from-constructor"></a>Oluşturucudan özel alan oluştur

Bu yeniden düzenleme için geçerlidir: 

- C# 

**Ne:** Bir oluşturucudan özel bir alan oluşturun. 

**Ne zaman:** Bir oluşturucudan hızlıca bir özel alan eklemek istiyorsunuz.

**Neden:** Özel alanlar yazmak zaman alıcı ve tekrarlı olabilir. Bu yeniden düzenlemenin kullanılması hızlıdır ve programı daha sağlam hale getirir.

## <a name="how-to"></a>Nasıl yapılır 

1. İmlecinizi Oluşturucu içindeki parametre adına yerleştirin.

2. **Ctrl**+tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   
3. **Alan oluşturma ve başlatma**seçeneğini belirleyin.

   ![Oluşturucudan özel alan oluştur](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Ayrıca bkz. 

- [Yeniden Düzenleme](../refactoring-in-visual-studio.md)
