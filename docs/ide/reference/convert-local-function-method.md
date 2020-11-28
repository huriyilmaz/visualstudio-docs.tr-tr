---
title: Yerel bir işlevi bir yönteme Dönüştür
description: Bir yerel işlevi bir yönteme dönüştürmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 64a46fc6221f00e6bb130be8010cb2544a00dcc8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305568"
---
# <a name="convert-a-local-function-to-a-method"></a>Yerel bir işlevi bir yönteme Dönüştür

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Yerel bir işlevi bir yönteme dönüştürün.

**Ne zaman:** Geçerli yerel bağlamınızın dışında tanımlamak istediğiniz bir yerel işleviniz var.

**Neden:** Yerel bir işlevi bir yönteme dönüştürmek istiyorsunuz, böylece bunu yerel içeriğiniz dışında çağırabilirsiniz. Yerel işleviniz çok uzun süren bir yönteme dönüştürmek isteyebilirsiniz. İşlevi ayrı bir yöntemde tanımladığınızda, kodunuzun okunması daha kolay olur.

## <a name="convert-local-function-to-method-refactoring"></a>Yerel işlevi yeniden düzenleme yöntemine Dönüştür

1. İmlecinizi yerel işleve yerleştirin.

    ![Yerel bir işlevi bir yöntem kodu örneğine Dönüştür](media/convert-local-function-to-method.png)

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

    ![Yerel işlevi Yöntem kodu düzeltmesini örnekle Dönüştür](media/convert-local-function-to-method-codefix.png)

2. Yeniden düzenlemeyi kabul etmek için ENTER tuşuna basın.

    ![Yerel işlevi Yöntem sonucu örneğine Dönüştür](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
