---
title: Yerel bir işlevi bir yönteme Dönüştür
description: Bir yerel işlevi bir yönteme dönüştürmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3cecafe64f7ead8157a9cb6c80d2f0a245566390
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919719"
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
