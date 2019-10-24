---
title: Değer değiştirilemez Iletişim kutusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97f057edefefd590c37b49d709ecf8a6e029b905
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745737"
---
# <a name="cannot-change-value-dialog-box"></a>Değer Değiştirilemez İletişim Kutusu
## <a name="error"></a>Hata
 &#124; *diğer diğer iletiler* `does not exist in the current context` &#124; `The value of this variable cannot be changed` `The name` *adı*

 Bu ileti kutusu, bir değişkenin içeriğini bir hata ayıklayıcı penceresinde (Oto, Izleme veya Yereller Windows) veya QuickWatch iletişim kutusunda geçersiz bir değerle değiştirmeye çalıştığınızda görüntülenir. Örneğin, bir tamsayı değişkeninin değerini bir karakter dizesine ayarlamaya çalışırsanız bu ileti kutusu görünür.

## <a name="solution"></a>Çözüm
 Hata ayıklayıcı penceresinde veya QuickWatch iletişim kutusunda yazdığınız girişin ayarlamaya çalıştığınız değişken için geçerli bir değeri temsil ettiğini doğrulayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısındaki İfadeler](../debugger/expressions-in-the-debugger.md)