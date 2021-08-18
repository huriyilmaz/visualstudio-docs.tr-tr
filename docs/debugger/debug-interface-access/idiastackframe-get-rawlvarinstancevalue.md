---
description: Bu yöntem, belirtilen yerel değişkenin değerini ham bayt olarak verir.
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 065e15ccbaa714a46eb388c2550e6e1db45558f2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074663"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Bu yöntem, belirtilen yerel değişkenin değerini ham bayt olarak verir.

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

[in] Değerini `IDiaLVarInstance` almak için bir yerel değişken örneğini temsil eden nesne.

 `cbDataMax`

[in] Arabellekte tarafından işaret eden maksimum bayt `pbData` sayısı. Bu, en fazla 8 bayt ( ) `sizeof(ULONGLONG)` olabilir.

 `pcbData`

[out] Arabellekte depolanan gerçek bayt sayısını döndürür.

 `pbData`

[out] Verilerle doldurulacak bir arabellek. Bu `NULL` olamaz.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
