---
title: 'IDiaStackWalkHelper:: readMemory | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ed505938636c9cccb69a927cdafbcb9589b35bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863804"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Bellek içindeki yürütülebilir dosyanın görüntüsünden bir veri bloğunu okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Parametreler
 `type`

'ndaki Okunan bellek türünü belirten [MemoryTypeEnum numaralandırma](../../debugger/debug-interface-access/memorytypeenum.md) numaralandırmasından bir değer.

 ka

'ndaki Okumaya başlamak için görüntüdeki sanal adres.

 `cbData`

'ndaki Veri arabelleğinin bayt cinsinden boyutu.

 `pcbData`

dışı Gerçekten okunan bayt sayısını döndürür. `pbData`İse `NULL` , bu, kullanılabilir veri baytlarının toplam sayısıdır.

 `pbData`

[in, out] Okunan bellek ile doldurulmuş bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum Numaralandırması](../../debugger/debug-interface-access/memorytypeenum.md)