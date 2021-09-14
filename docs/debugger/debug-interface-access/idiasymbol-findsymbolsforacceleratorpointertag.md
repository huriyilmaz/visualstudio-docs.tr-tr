---
description: Karşılık gelen bir etiket değeri verildi, bu yöntem bu saplama işlevinde yer alan sembollerin bir numaralama döndürür.
title: IDiaSymbol::findSymbolsForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b5ccf90584cfc948fc4ecb886dd20ada5cbf6036
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626714"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag

Karşılık gelen bir etiket değeri verildi, bu yöntem bu saplama işlevinde yer alan sembollerin bir numaralama döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsForAccleratorPointerTag (
   DWORD             tagValue,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametreler
 `tagValue`

[in] İşaret simgesi kayıtlarının bulunduğu işaretçi etiketi değeri.

 `ppResult`

[out] Sonuçla `IDiaEnumSymbols` başlatılan arabirim işaretçisinin işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
