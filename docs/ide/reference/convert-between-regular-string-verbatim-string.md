---
title: Normal dize ve düz metin dizesi değişmez değerleri arasında dönüştürme
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 7e8e239f53f92727072a2fcd6573d6957b7cd3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290571"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>Normal dize ve tam dize değişmez değerlerini yeniden düzenleme arasında Dönüştür

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Normal dize ve tam dize sabit değerleri arasında dönüştürme yapmanızı sağlar.

**Ne zaman:** Kodunuzda alan kazanmak veya daha fazla açıklık sağlamak istersiniz.

**Neden:** Tam bir dize değişmez değerini normal bir dize değişmez değerine dönüştürmek, alanı kaydetmeye yardımcı olabilir. Normal bir dize değişmez değerini tam dize değişmez değerine dönüştürmek daha fazla açıklık sağlayabilir.

## <a name="how-to"></a>Nasıl yapılır

1. Giriş işaretini normal dizeye veya tam dize değişmez değerine yerleştirin:

2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

3. Aşağıdaki seçeneklerden birini belirleyin: 

    **Normal dizeye dönüştür** seçeneğini belirleyin.

    ![Normal dizeye Dönüştür](media/convert-to-regular-string.png)

    **Düz metin dizesine dönüştür** seçeneğini belirleyin.

    ![Tam dizeye Dönüştür](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)