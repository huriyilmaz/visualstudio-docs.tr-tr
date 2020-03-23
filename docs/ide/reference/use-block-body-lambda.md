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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531910"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Lambda ifadeleri için ifade gövdesi veya blok gövdesi kullanma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Bir ifade gövdesi veya blok gövde kullanmak için bir lambda ifade refactor sağlar.

**Ne zaman:** Lambda ifadelerini bir ifade gövdesi veya blok gövde kullanmak için tercih edersiniz.

**Neden:** Lambda ifadeleri kullanıcı tercihinize göre okunabilirliği artırmak için yeniden kullanılabilir.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Lambda ifade vücut veya blok vücut refactoring

1. İmlecinizi bir lambda operatörünün sağına yerleştirin.
2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

  ![Lambda expression/block body kullanın](media/block-body-lambda.png)

3. **lambda ifadeleri için blok gövdesini kullan'ı** seçin veya **lambda ifadeleri için ifade gövdesini kullanın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET Geliştiricileri için ipuçları](../csharp-developer-productivity.md)