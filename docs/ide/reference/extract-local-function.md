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
ms.openlocfilehash: 8b1f05e564f5d26c3c470917dbdf9bb9045a689a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725740"
---
# <a name="extract-local-function-refactoring"></a>Yerel işlevi yeniden düzenlemeyi ayıklama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Bir kod parçasını mevcut bir yöntemden yerel bir işleve çevirmenizi sağlar.

**Ne zaman:** Yerel bir işlevden çağrıllanması gereken bir yöntemde mevcut kodun bir parçasına sahipsiniz.

**Neden:** Bu kodu kopyalayıp yapıştırabilirsiniz, ancak bu yinelemeye yol açabilecektir. Daha iyi bir çözüm, bu parçanın kendi yerel işlevi olarak yeniden düzenlemesidir.

## <a name="how-to"></a>Nasıl yapılır

1. Ayıklanan kodu vurgulayın.

2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için. 

3. **Yerel işlevi ayıkla** seçeneğini belirleyin.

    ![Satır vurgulanmış Visual Studio penceresinin ekran görüntüsü. Hızlı Eylemler ve Yeniden Düzenleme menüsü açık ve Yerel işlevi ayıkla seçilidir.](media/extract-local-function.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
