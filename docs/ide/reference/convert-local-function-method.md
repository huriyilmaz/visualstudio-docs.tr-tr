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
ms.openlocfilehash: 7068c7cb8edf7f44c981496aa2ac81cea7e82903
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085916"
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
