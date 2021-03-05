---
description: Çerçeve veri Numaralandırıcının System. Runtime. InteropServices. ComTypes. IEnumVARIANT sürümünü alır.
title: 'IDiaEnumFrameData:: get__NewEnum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::get__NewEnum method
ms.assetid: f5fe0279-0549-4af5-8f89-bcb535fc5809
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffa18a94d8fb0e393d0814c42bab0406d49b1ee6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159372"
---
# <a name="idiaenumframedataget__newenum"></a>IDiaEnumFrameData::get__NewEnum
<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>Bu Numaralandırıcı sürümünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 pRetVal

dışı `IUnknown` Bu Numaralandırıcı sürümünü temsil eden arabirimi döndürür <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
