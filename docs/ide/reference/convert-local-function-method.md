---
title: Yerel bir işlevi yönteme dönüştürme
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71301687"
---
# <a name="convert-a-local-function-to-a-method"></a>Yerel bir işlevi yönteme dönüştürme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Yerel bir işlevi yönteme dönüştürün.

**Ne zaman:** Geçerli yerel bağlamınız dışında tanımlamak istediğiniz yerel bir işleviniz vardır.

**Neden:** Yerel bir işlevi, yerel bağlamınızın dışına çağırabilmeniz için bir yönteme dönüştürmek istiyorsunuz. Yerel işleviniz çok uzadığında bir yönteme dönüştürmek isteyebilirsiniz. İşlevinizi ayrı bir yöntemle tanımladığınızda, kodunuzu okumak daha kolaydır.

## <a name="convert-local-function-to-method-refactoring"></a>Yerel işlevi yöntem refactoring'e dönüştürme

1. İmlecinizi yerel fonksiyona yerleştirin.

    ![Yerel bir işlevi yöntem kodu örneğine dönüştürme](media/convert-local-function-to-method.png)

2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

    ![Yerel işlevi yöntem kodu düzeltme örneğine dönüştürme](media/convert-local-function-to-method-codefix.png)

2. Yeniden düzenlemeyi kabul etmek için Enter tuşuna basın.

    ![Yerel işlevi yöntem sonuç örneğine dönüştürme](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET Geliştiricileri için ipuçları](../csharp-developer-productivity.md)
