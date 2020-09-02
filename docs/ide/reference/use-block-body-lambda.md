---
title: Lambda ifadesi veya blok gövdesi kullanma
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531910"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Lambda ifadeleri için ifade gövdesi veya blok gövdesi kullan

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Bir lambda ifadesini bir ifade gövdesi veya blok gövdesi kullanmak için yeniden düzenlemenize olanak tanır.

**Ne zaman:** Lambda ifadelerini bir ifade gövdesi veya blok gövdesi kullanmak üzere tercih edersiniz.

**Neden:** Lambda ifadeleri, Kullanıcı tercihlerinize göre okunabilirliğini geliştirmek için yeniden düzenlenmiş olabilir.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Lambda ifadesi gövdesi veya blok gövdesini yeniden düzenleme

1. İmlecinizi bir lambda işlecinin sağına yerleştirin.
2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

  ![Lambda ifadesi/blok gövdesi kullan](media/block-body-lambda.png)

3. **Lambda ifadeleri için blok gövdesi kullan** veya **lambda ifadeleri için ifade gövdesi**kullan ' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)