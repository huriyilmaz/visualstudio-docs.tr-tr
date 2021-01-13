---
title: Yerel işlevi ayıklama
description: Kodu seçip CTRL + R, CTRL + M yazarak kodun bir parçasını kendi işlevine dönüştürün.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129464"
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
