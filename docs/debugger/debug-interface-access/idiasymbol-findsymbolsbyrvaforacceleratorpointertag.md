---
description: Karşılık gelen bir etiket değeri verildiğinde, bu yöntem, belirtilen bir göreli sanal adresteki bu saplama işlevinde bulunan simgelerin bir listesini döndürür.
title: 'IDiaSymbol:: Findsymbolsbyrvaforivatorpointertag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05d468eca9d924fc9c87ed48e01ddee7aa9d3894
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156624"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Karşılık gelen bir etiket değeri verildiğinde, bu yöntem, belirtilen bir göreli sanal adresteki bu saplama işlevinde bulunan simgelerin bir listesini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametreler
 `tagValue`

'ndaki Pointee sembol kayıtlarının bulunduğu işaretçi etiketi değeri.

 `rva`

'ndaki Belirtilen etiket değeriyle pointee değişkenine karşılık gelen sembolleri filtrelemek için kullanılan RVA.

 `ppResult`

dışı `IDiaEnumSymbols` Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi yalnızca `IDiaSymbol` bir Hızlandırıcı saplama işlevine karşılık gelen bir arabirimde çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
