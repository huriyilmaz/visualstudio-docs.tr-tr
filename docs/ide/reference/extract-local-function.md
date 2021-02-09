---
title: Yerel işlevi ayıklama
description: Kodu seçip CTRL + R, CTRL + M yazarak kodun bir parçasını kendi işlevine dönüştürün.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 80ac8f23b5404d70b70166915cd791f2c0d7ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860977"
---
# <a name="extract-local-function-refactoring"></a>Yerel işlev yeniden düzenlemesi Ayıkla

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Varolan bir yöntemden bir kod parçasını yerel işleve açmanızı sağlar.

**Ne zaman:** Bir yerel işlevden çağrılması gereken bazı bir yöntemde var olan kodun bir parçası var.

**Neden:** Bu kodu kopyalayabilir/yapıştırabilir, ancak çoğaltmaya yol açabilir. Daha iyi bir çözüm, söz konusu parçayı kendi yerel işlevine yeniden düzenleme.

## <a name="how-to"></a>Nasıl yapılır

1. Ayıklanacak kodu vurgulayın.

2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için. 

3. **Yerel işlevi ayıkla** seçeneğini belirleyin.

    ![Bir çizgi vurgulanmış şekilde Visual Studio Code penceresinin ekran görüntüsü. Hızlı Eylemler ve yeniden düzenlemeler menüsü açık ve yerel işlevi Ayıkla seçilidir.](media/extract-local-function.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
