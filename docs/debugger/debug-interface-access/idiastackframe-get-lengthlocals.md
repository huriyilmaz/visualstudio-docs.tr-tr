---
title: 'IDiaStackFrame:: get_lengthLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthLocals method
ms.assetid: dbc3e544-578a-4f0b-8d20-f21ad4cbb604
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a812b51f8f874baf0a954b33d8fe25cc382e2d83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465096"
---
# <a name="idiastackframeget_lengthlocals"></a>IDiaStackFrame::get_lengthLocals
Yığına gönderilen yerel değişkenlerin bayt sayısını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_lengthLocals ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Yerel değişkenlerin bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Özelliğin desteklenip desteklenmediğini döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)