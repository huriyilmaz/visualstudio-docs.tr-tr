---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a0c0052ca7183a0c53080a4e51bddd2cdfbf72ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854894"
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

'ndaki `IDiaLVarInstance` Değerini almak için bir yerel değişken örneğini temsil eden nesne.

 `cbDataMax`

'ndaki Arabellekte tarafından işaret edilen en fazla bayt sayısı `pbData` . Bu en fazla 8 bayt ( `sizeof(ULONGLONG)` ) olabilir.

 `pcbData`

dışı Arabellekte depolanan gerçek bayt sayısını döndürür.

 `pbData`

dışı Verilerle doldurulacak bir arabellek. Bu, olamaz `NULL` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)