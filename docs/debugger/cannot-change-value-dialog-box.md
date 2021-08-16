---
title: Değer Değiştirimiyor İletişim Kutusu | Microsoft Docs
description: Hata ayıklayıcısı penceresinde veya QuickWatch'da Visual Studio geçersiz bir değere değiştirmeye çalışma sırasında görüntülenen Değer Değiştirimiyor iletişim kutusunu gözden geçirebilirsiniz.
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
ms.openlocfilehash: 48cf700f41695e41f3b5fca5dba72c1538aa0fdec201dfa0f47f733e1a327b9c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346043"
---
# <a name="cannot-change-value-dialog-box"></a>Değer Değiştirilemez İletişim Kutusu
## <a name="error"></a>Hata
 `The value of this variable cannot be changed`&#124; diğer `The name`  `does not exist in the current context` &#124; *bir ad*

 Bu ileti kutusu, bir hata ayıklayıcı penceresinde (Otomatikler, İzleme veya Yereller pencereleri) veya QuickWatch iletişim kutusunda bir değişkenin içeriğini geçersiz bir değerle değiştirmeye çalışmanız sırasında görüntülenir. Örneğin, bir tamsayı değişkeninin değerini bir karakter dizesi olarak ayarlamayı denersiniz, bu ileti kutusu görüntülenir.

## <a name="solution"></a>Çözüm
 Hata ayıklayıcı penceresine veya QuickWatch iletişim kutusuna yazarak ayarlamaya çalıştığın değişken için yasal bir değeri temsil ettiğine emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcıda İfadeler](../debugger/expressions-in-the-debugger.md)