---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebc2e4042185b17d7e2f670456cf124c5ce079fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465124"
---
# <a name="idiastackframeget_cplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
C++ özel durum işlemenin etkin olup olmadığını gösteren bir bayrak alır.

## <a name="syntax"></a>Söz dizimi

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