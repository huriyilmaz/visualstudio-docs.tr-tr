---
title: Yerel işlevi ayıklama
description: Kodu seçerek ve Ctrl+R, Ctrl+M yazarak bir kod parçasını kendi işlevine dönüştürebilirsiniz.
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
ms.openlocfilehash: 7ee115eea0342d1e8ce2c34beed7ce1cfadc98d00ea431a1f0a28fc32aee7bdf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121258934"
---
# <a name="extract-local-function-refactoring"></a>Yerel işlev yeniden düzenlemeyi ayıklama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Bir kod parçasını mevcut bir yöntemden yerel bir işleve çevirmenizi sağlar.

**Ne zaman:** Yerel bir işlevden çağrıllanması gereken bir yöntemde mevcut kodun bir parçasına sahipsiniz.

**Neden:** Bu kodu kopyalayıp yapıştırabilirsiniz, ancak bu yinelemeye yol açabilecektir. Daha iyi bir çözüm, bu parçanın kendi yerel işlevi olarak yeniden düzenlemesidir.

## <a name="how-to"></a>Nasıl yapılır

1. Ayıklanan kodu vurgulayın.

2. **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için. 

3. **Yerel işlevi ayıkla** seçeneğini belirleyin.

    ![Satır vurgulanmış Visual Studio penceresinin ekran görüntüsü. Hızlı Eylemler ve Yeniden Düzenleme menüsü açık ve Yerel işlevi ayıkla seçilidir.](media/extract-local-function.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
