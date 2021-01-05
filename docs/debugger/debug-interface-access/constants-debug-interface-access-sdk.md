---
title: Sabitler (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
description: Hata ayıklama arabirimi erişimi (DIA) SDK 'Sı aracılığıyla bir program hata ayıklama veritabanı (PDB) dosyasının çeşitli bölümlerini belirlemek için kullanılabilecek dize sabitleri listesini görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806eb9207fa60b7147d1e0d7df75871b23f8850d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728756"
---
# <a name="constants-debug-interface-access-sdk"></a>Sabitler (Arabirim Erişimi SDK'sında Hata Ayıklama)
Bu dize sabitleri, bir program hata ayıklama veritabanı (PDB) dosyasının DIA SDK aracılığıyla çeşitli bölümlerini belirlemek için kullanılabilir.

## <a name="constants"></a>Sabitler
Aşağıdakiler C/C++ makroları olarak bildirilmiştir.

|Makroya|Değer|
|-----------|-----------|
|`DiaTable_Symbols`|L "semboller"|
|`DiaTable_Sections`|L "bölümler"|
|`DiaTable_SrcFiles`|L "SourceFiles"|
|`DiaTable_LineNums`|L "LineNumbers"|
|`DiaTable_SegMap`|L "SegmentMap"|
|`DiaTable_Dbg`|L "DBG"|
|`DiaTable_InjSrc`|L "ınjectedsource"|
|`DiaTable_FrameData`|L "FrameData"|

## <a name="example"></a>Örnek
Bu simgelerden birini kullanarak bir örnek aşağıda verilmiştir:

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

## <a name="see-also"></a>Ayrıca bkz.
- [Başvuru](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
