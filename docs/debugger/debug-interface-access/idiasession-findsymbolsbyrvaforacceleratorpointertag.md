---
description: Karşılık gelen bir etiket değeri verildiğinde, bu yöntem belirtilen bir ilişkili sanal adreste belirtilen üst Hızlandırıcı saplama işlevinde bulunan simgelerin bir listesini döndürür.
title: 'IDiaSession:: Findsymbolsbyrvaforivatorpointertag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50545be4b99c273b7019931463883efacbb683fb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157065"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Karşılık gelen bir etiket değeri verildiğinde, bu yöntem belirtilen bir ilişkili sanal adreste belirtilen üst Hızlandırıcı saplama işlevinde bulunan simgelerin bir listesini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

'ndaki `IDiaSymbol` Aranmak üzere Hızlandırıcı saplama işlevine karşılık gelen bir.

 `tagValue`

'ndaki İşaretçi etiketi değeri.

 `rva`

'ndaki Göreli sanal adres.

 `ppResult`

dışı `IDiaEnumSymbols` Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi yalnızca `IDiaSymbol` bir Hızlandırıcı saplama işlevine karşılık gelen bir arabirimde çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
