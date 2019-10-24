---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741628"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Bu yöntem belirtilen yerel değişkenin değerini ham bayt olarak alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Parametreler
 `pInstance`

'ndaki Değerini almak için bir yerel değişken örneğini temsil eden bir `IDiaLVarInstance` nesnesi.

 `cbDataMax`

'ndaki Arabellekteki `pbData` tarafından işaret edilen en fazla bayt sayısı. Bu en fazla 8 bayt (`sizeof(ULONGLONG)`) olabilir.

 `pcbData`

dışı Arabellekte depolanan gerçek bayt sayısını döndürür.

 `pbData`

dışı Verilerle doldurulacak bir arabellek. Bu `NULL` olamaz.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)