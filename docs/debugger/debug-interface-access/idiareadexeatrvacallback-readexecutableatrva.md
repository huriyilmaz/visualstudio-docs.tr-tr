---
title: 'Idiareadexeatrboş Allback:: ReadExecutableAtRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a417669c381036fffac87b4d7e56c66fa31f728
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466464"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Yürütülebilir dosyadan belirtilen göreli sanal adresten (RVA) başlayarak belirtilen bayt sayısını okur.

## <a name="syntax"></a>Söz dizimi

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

'ndaki Okumaya başlamak için çalıştırılabilir dosyadaki RVA.

 `cbData`

'ndaki Okunacak bayt sayısı.

 `pcbData`

dışı Okunan bayt sayısını döndürür.

 `data[]`

[in, out] Dosyadan okunan bayt ile doldurulmuş bir dizi.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bir sanal adresi kullanarak bir yürütülebilir dosyadan veri baytları yüklemek için ÇYA destek kodu tarafından çağırılır. Bu yöntem, [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu desteklemek için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)