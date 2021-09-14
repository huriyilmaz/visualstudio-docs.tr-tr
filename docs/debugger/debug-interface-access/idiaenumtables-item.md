---
description: Bir tabloyu dizin veya ad ile alır.
title: IDiaEnumTables::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 30e224b7edb621cb31d4124ac092e39e53f801fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629936"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Bir tabloyu dizin veya ad ile alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Parametreler
 `index`

[in] Alınarak [IDiaTable'ın](../../debugger/debug-interface-access/idiatable.md) dizini veya adı. Bir tamsayı varyantı kullanılırsa, 0 ile `count` -1 aralığında olmalıdır; burada `count` [IDiaEnumTables::get_Count yöntemi tarafından döndürülen](../../debugger/debug-interface-access/idiaenumtables-get-count.md) değerdir.

 `table`

[out] İstenen [tabloyu temsil eden bir IDiaTable](../../debugger/debug-interface-access/idiatable.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir dize varyantı belirtilirse, dize belirli bir tabloyu olarak adlar. Ad, Sabitler (Arabirim Erişimi SDK'sı Hata Ayıklama) [içinde tanımlanan tablo adlarından biri olabilir.](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)

## <a name="example"></a>Örnek

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Sabitler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)
