---
title: 'IDiaSession:: Findsymbolsbyrvaforivatorpointertag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf05d60499da0317461d03d05579dce6124385f7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465533"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Karşılık gelen bir etiket değeri verildiğinde, bu yöntem belirtilen bir ilişkili sanal adreste belirtilen üst Hızlandırıcı saplama işlevinde bulunan simgelerin bir listesini döndürür.

## <a name="syntax"></a>Söz dizimi

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

'ndaki `IDiaSymbol`Aranmak üzere Hızlandırıcı saplama işlevine karşılık gelen bir.

 `tagValue`

'ndaki İşaretçi etiketi değeri.

 `rva`

'ndaki Göreli sanal adres.

 `ppResult`

dışı `IDiaEnumSymbols`Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi yalnızca `IDiaSymbol` bir Hızlandırıcı saplama işlevine karşılık gelen bir arabirimde çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)