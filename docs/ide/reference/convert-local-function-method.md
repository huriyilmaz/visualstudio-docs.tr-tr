---
title: Yerel işlevi yönteme dönüştürme
description: Yerel bir işlevi yönteme dönüştürmek için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 32808364220cea253d0cc085115bd58de11bedb768e3583dacab833474dd1581
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430147"
---
# <a name="convert-a-local-function-to-a-method"></a>Yerel işlevi yönteme dönüştürme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Yerel bir işlevi yönteme dönüştürme.

**Ne zaman:** Geçerli yerel bağlamınız dışında tanımlamak istediğiniz yerel bir işleviniz var.

**Neden:** Yerel bir işlevi, yerel bağlamınız dışında çağıran bir yönteme dönüştürmek istediğiniz. Yerel işleviniz fazla uzun olduğunda yöntemine dönüştürmek istiyor olabilirsiniz. İşlevi ayrı bir yöntemde tanımladığınız zaman kodunuz daha kolay okunur.

## <a name="convert-local-function-to-method-refactoring"></a>Yerel işlevi yöntem yeniden düzenlemeye dönüştürme

1. İmlecinizi yerel işleve yerleştirin.

    ![Yerel işlevi yöntem kodu örneğine dönüştürme](media/convert-local-function-to-method.png)

2. **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.

    ![Yerel işlevi yöntem kodu düzeltme örneğine dönüştürme](media/convert-local-function-to-method-codefix.png)

2. Yeniden düzenlemeyi kabul etmek için Enter tuşuna basın.

    ![Yerel işlevi yöntem sonucu örneğine dönüştürme](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET İpuçları için geliştirmeler](../csharp-developer-productivity.md)
