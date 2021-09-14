---
description: Yürütülebilir dosyadan belirtilen göreli sanal adresten (RVA) başlayan belirtilen bayt sayısını okur.
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d98eb6f6a50b7dace957b7012775746e90564bbd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629498"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Yürütülebilir dosyadan belirtilen göreli sanal adresten (RVA) başlayan belirtilen bayt sayısını okur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT ReadExecutableAtRVA ( 
   DWORD  relativeVirtualAddress,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametreler
 `relativeVirtualAddress`

[in] Okumaya başlamak için yürütülebilir dosyada RVA.

 `cbData`

[in] Okunan bayt sayısı.

 `pcbData`

[out] Okunan bayt sayısını döndürür.

 `data[]`

[in, out] Dosyadan okunan baytlarla doldurulmuş bir dizi.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, dia destek kodu tarafından göreli bir sanal adres kullanarak yürütülebilir dosyadan veri baytlarını yüklemek için çağrılır. Bu yöntem, [IDiaDataSource::loadDataForExe yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) desteklemek için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
