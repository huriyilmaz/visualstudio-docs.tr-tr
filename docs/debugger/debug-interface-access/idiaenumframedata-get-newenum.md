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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 90cdae350c90722cf98611a270c35753cd12197a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630339"
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
