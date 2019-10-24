---
title: 'IDiaEnumSourceFiles:: get__NewEnum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::get__NewEnum method
ms.assetid: 8405966c-64b4-4743-9a83-0e27ca2047c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 676ba2e17ccbcab584fc0b2a559027ce35eaaad3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744098"
---
# <a name="idiaenumsourcefilesget__newenum"></a>IDiaEnumSourceFiles::get__NewEnum
Bu Numaralandırıcının <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> sürümünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 pRetVal

dışı Bu Numaralandırıcı <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> sürümünü temsil eden `IUnknown` arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)