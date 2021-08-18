---
description: Segment numaralayıcının System.Runtime.InteropServices.ComTypes.IEnumVARIANT sürümünü alın.
title: IDiaEnumSegments::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get__NewEnum method
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 290f97a34b1564deda79df7976edaf9b95abc953
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044665"
---
# <a name="idiaenumsegmentsget__newenum"></a>IDiaEnumSegments::get__NewEnum
Bu <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> numaralayıcının sürümünü alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 pRetVal

[out] Bu `IUnknown` numaralayıcının <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> sürümünü temsil eden arabirimi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
