---
title: Değer Değiştirilemiyor İletişim Kutusu | Microsoft Docs
description: Bir değişkeni hata ayıklayıcı penceresinde veya QuickWatch Visual Studio geçersiz değere değiştirmeye çalışma sırasında görüntülenen Değer Değiştirimiyor iletişim kutusunu gözden geçirebilirsiniz.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129759"
---
# <a name="cannot-change-value-dialog-box"></a>Değer Değiştirilemez İletişim Kutusu
## <a name="error"></a>Hata
 `The value of this variable cannot be changed`&#124; diğer `The name`  `does not exist in the current context` &#124; *iletilerin adını girin*

 Bu ileti kutusu, bir değişkenin içeriğini hata ayıklayıcı penceresinde (Otomatikler, İzleme veya Yereller pencereleri) veya QuickWatch iletişim kutusunda geçersiz bir değerle değiştirmeye çalışmanız sırasında görüntülenir. Örneğin, bir tamsayı değişkeninin değerini bir karakter dizesi olarak ayarlamayı denersiniz, bu ileti kutusu görüntülenir.

## <a name="solution"></a>Çözüm
 Hata ayıklayıcı penceresine veya QuickWatch iletişim kutusuna yazarak ayarlamaya çalıştığın değişken için yasal bir değeri temsil ettiğine emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcıda İfadeler](../debugger/expressions-in-the-debugger.md)