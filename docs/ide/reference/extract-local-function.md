---
title: Yerel işlevi ayıklama
description: Kodu seçip CTRL + R, CTRL + M yazarak kodun bir parçasını kendi işlevine dönüştürün.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8b1f05e564f5d26c3c470917dbdf9bb9045a689a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143917"
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

    ![çizgi vurgulanmış şekilde Visual Studio kod penceresinin ekran görüntüsü. Hızlı Eylemler ve yeniden düzenlemeler menüsü açık ve yerel işlevi Ayıkla seçilidir.](media/extract-local-function.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
