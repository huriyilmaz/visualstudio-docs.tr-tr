---
title: Sabitler (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 931e1ab46793a5ff7e0434949330eaf4dbc820e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164432"
---
# <a name="constants-debug-interface-access-sdk"></a>Sabitler (Arabirim Erişimi SDK'sında Hata Ayıklama)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
```cpp#  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvurunun](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Arabirimler (hata ayıklama arabirimi erişim SDK 'Sı)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
