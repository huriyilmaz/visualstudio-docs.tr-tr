---
title: Yerel işlevi ayıklama
description: Kodu seçerek ve Ctrl+R, Ctrl+M yazarak kod parçasını kendi yöntemine dönüştürün.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515332"
---
# <a name="extract-local-function-refactoring"></a>Yerel fonksiyon refactoring ayıklama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Varolan bir yöntemden kod parçasını yerel bir işleve dönüştürmenizi sağlar.

**Ne zaman:** Yerel bir işlevden çağrılması gereken bazı yöntemde varolan kodun bir parçası var.

**Neden:** Bu kodu kopyalayabilir/yapıştırabilirsiniz, ancak bu yinelemeye yol açar. Daha iyi bir çözüm kendi yerel işlevi içine bu parçayı yeniden.

## <a name="how-to"></a>Nasıl yapılır

1. Çıkarılacak kodu vurgulayın.

2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için. 

3. **Yerel işlevi ayıkla** seçeneğini belirleyin.

    ![Yerel işlevi ayıklama](media/extract-local-function.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
