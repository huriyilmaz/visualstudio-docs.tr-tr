---
title: Sabitler (Arabirim Erişimi SDK'sı Hata Ayıklama) | Microsoft Docs
description: Hata ayıklama arabirimi erişimi (DIA) SDK'sı aracılığıyla bir program hata ayıklama veritabanı (PDB) dosyasının çeşitli bölümlerini tanımlamak için kullanılan dize sabitlerinin listesine bakın.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7ebbaa42789d18b6d08cffe862e38ddcfe494eed5a7c2acd36a772986c95ce96
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345757"
---
# <a name="constants-debug-interface-access-sdk"></a>Sabitler (Arabirim Erişimi SDK'sında Hata Ayıklama)
Bu dize sabitleri, bir program hata ayıklama veritabanı (PDB) dosyasının farklı bölümlerini DIA SDK.

## <a name="constants"></a>Sabitler
Aşağıdakiler C/C++ makroları olarak bildirilmez.

|Makro|Değer|
|-----------|-----------|
|`DiaTable_Symbols`|L"Semboller"|
|`DiaTable_Sections`|L"Bölümler"|
|`DiaTable_SrcFiles`|L"SourceFiles"|
|`DiaTable_LineNums`|L"LineNumbers"|
|`DiaTable_SegMap`|L"SegmentMap"|
|`DiaTable_Dbg`|L"Dbg"|
|`DiaTable_InjSrc`|L"InjectedSource"|
|`DiaTable_FrameData`|L"FrameData"|

## <a name="example"></a>Örnek
Bu simgelerden birini kullanan bir örnek aşağıdaki gibidir:

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
Üst bilgi: dia2.h

## <a name="see-also"></a>Ayrıca bkz.
- [Başvuru](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
