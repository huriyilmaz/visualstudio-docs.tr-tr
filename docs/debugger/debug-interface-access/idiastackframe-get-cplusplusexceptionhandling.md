---
description: C++ özel durum işlemenin etkin olup olmadığını gösteren bir bayrak alır.
title: 'IDiaStackFrame:: get_cplusplusExceptionHandling | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_cplusplusExceptionHandling method
ms.assetid: f2631820-c986-40ca-b61e-230d7a9c426c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e5f4f6d622497ee5ac149a74d3b35b0f7d0a6911
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161462"
---
# <a name="idiastackframeget_cplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
C++ özel durum işlemenin etkin olup olmadığını gösteren bir bayrak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_cplusplusExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` C++ özel durum işlemenin bu çerçeve için geçerli olup olmadığını döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Özelliğin desteklenip desteklenmediğini döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 C++ özel durum işleme, yapılandırılmış veya sistem özel durum işlemeyle aynı değildir.

 Yapılandırılmış özel durum işlemenin geçerli olup olmadığını anlamak için, [IDiaStackFrame:: get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)
