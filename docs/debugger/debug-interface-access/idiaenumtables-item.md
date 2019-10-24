---
title: 'IDiaEnumTables:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743749"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Bir tabloyu bir dizin veya ada göre alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Parametreler
 `index`

'ndaki Alınacak [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 'ın dizini veya adı. Bir tamsayı değişkeni kullanılırsa, `count` [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) yöntemi tarafından döndürülen `count`-1 aralığında olmalıdır.

 `table`

dışı İstenen tabloyu temsil eden bir [IDiaTable](../../debugger/debug-interface-access/idiatable.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir dize değişkeni belirtilmişse, dize belirli bir tabloyu adlandırır. Ad, [sabitler (hata ayıklama arabirimi erişim SDK 'sı)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)olarak tanımlanan tablo adlarından biri olmalıdır.

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