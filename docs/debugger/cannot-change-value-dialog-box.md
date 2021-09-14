---
title: Değer değiştirilemez Iletişim kutusu | Microsoft Docs
description: bir değişkeni hata ayıklayıcı penceresinde veya quickwatch 'ta geçersiz bir değerle değiştirmeye çalışırsanız Visual Studio görünen değeri değiştir iletişim kutusunu inceleyin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dcdb605421c1e18b6a27e5d93999dc6e3d2320f8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630926"
---
# <a name="cannot-change-value-dialog-box"></a>Değer Değiştirilemez İletişim Kutusu
## <a name="error"></a>Hata
 `The value of this variable cannot be changed``The name`  `does not exist in the current context` *Diğer diğer iletiler* &#124; &#124; adı

 Bu ileti kutusu, bir değişkenin içeriğini bir hata ayıklayıcı penceresinde (Oto, Izleme veya Yereller Windows) veya QuickWatch iletişim kutusunda geçersiz bir değerle değiştirmeye çalıştığınızda görüntülenir. Örneğin, bir tamsayı değişkeninin değerini bir karakter dizesine ayarlamaya çalışırsanız bu ileti kutusu görünür.

## <a name="solution"></a>Çözüm
 Hata ayıklayıcı penceresinde veya QuickWatch iletişim kutusunda yazdığınız girişin ayarlamaya çalıştığınız değişken için geçerli bir değeri temsil ettiğini doğrulayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcıdaki İfadeler](../debugger/expressions-in-the-debugger.md)