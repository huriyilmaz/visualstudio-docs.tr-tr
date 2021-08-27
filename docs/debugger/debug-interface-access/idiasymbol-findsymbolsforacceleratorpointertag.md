---
description: Karşılık gelen bir etiket değeri verildiğinde, bu yöntem bu saplama işlevinde bulunan simgelerin bir listesini döndürür.
title: 'IDiaSymbol:: Findsymbolsforivatorpointertag | Microsoft Docs'
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
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980702"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag

Karşılık gelen bir etiket değeri verildiğinde, bu yöntem bu saplama işlevinde bulunan simgelerin bir listesini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsForAccleratorPointerTag (
   DWORD             tagValue,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametreler
 `tagValue`

'ndaki Pointee sembol kayıtlarının bulunduğu işaretçi etiketi değeri.

 `ppResult`

dışı `IDiaEnumSymbols` Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
