---
title: 'IDiaStackFrame:: get_systemExceptionHandling | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_systemExceptionHandling
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2d0be30e7aa07326bd2a1b955cac3d6be78f6aa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741575"
---
# <a name="idiastackframeget_systemexceptionhandling"></a>IDiaStackFrame::get_systemExceptionHandling
Sistem özel durum işlemenin etkin olup olmadığını gösteren bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_systemExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bu çerçeve için sistem özel durum işleme etkin ise `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Özellik desteklenmiyorsa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sistem özel durum işleme, yapılandırılmış özel durum işleme olarak da bilinir. Özel durum işleme ile C++ aynı şey değildir.

 Özel durum işlemenin geçerli olup olmadığını anlamak için, [IDiaStackFrame:: get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md) yöntemini çağırın. C++

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)