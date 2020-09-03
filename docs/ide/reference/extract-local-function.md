---
title: Yerel işlevi ayıklama
description: Kodu seçip CTRL + R, CTRL + M yazarak kodun bir parçasını kendi yöntemine dönüştürün.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77515332"
---
# <a name="extract-local-function-refactoring"></a>Yerel işlev yeniden düzenlemesi Ayıkla

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Varolan bir yöntemden bir kod parçasını yerel işleve açmanızı sağlar.

**Ne zaman:** Bir yerel işlevden çağrılması gereken bazı bir yöntemde var olan kodun bir parçası var.

**Neden:** Bu kodu kopyalayabilir/yapıştırabilir, ancak çoğaltmaya yol açabilir. Daha iyi bir çözüm, söz konusu parçayı kendi yerel işlevine yeniden düzenleme.

## <a name="how-to"></a>Nasıl yapılır

1. Ayıklanacak kodu vurgulayın.

2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için. 

3. **Yerel işlevi ayıkla** seçeneğini belirleyin.

    ![Yerel işlevi ayıklama](media/extract-local-function.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
