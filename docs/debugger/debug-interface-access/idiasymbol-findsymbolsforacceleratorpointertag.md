---
title: 'IDiaSymbol:: Findsymbolsforivatorpointertag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1544471bd4ff9166d4c8f4c10f48840db6f576f3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741125"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
Bir C++ amp saplama işlevindeki Hızlandırıcı işaretçisi etiketlerinin sayısını döndürür.

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

dışı Sonuçla başlatılan `IDiaEnumSymbols` arabirimi işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)