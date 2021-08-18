---
description: Yeni .exe oluşturulduğunda, her ortak simgeye (en azından, her genel işlev ve veri simgesi) bir SymTagPublicSymbol etiketi verilir.
title: PublicSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data symbols [C++]
- PublicSymbol symbol
- global functions [C++], as public symbols
ms.assetid: f8d33007-302d-4549-9dad-47fb33ea60b7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 09022b8279290b2ecc977a513e4dabaee1f30eef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097647"
---
# <a name="publicsymbol"></a>PublicSymbol
Yeni .exe oluşturulduğunda, her ortak simgeye (en azından, her genel işlev ve veri simgesi) bir etiket `SymTagPublicSymbol` verilir.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için geçerli olan özellikler gösterilir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun kaydırma bölümü; Ayrıntılar için bkz. [LocationType Numaralama.](../../debugger/debug-interface-access/locationtype.md)|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType Numaralama.](../../debugger/debug-interface-access/locationtype.md)|
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|`BOOL`|`TRUE` simgesinin konumu kodda ise.|
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|`BOOL`|`TRUE` simgesi bir işlevse.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Bu sembolün bayt cinsinden uzunluğu.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Genel kapsamın simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözcük üst simgesinin kimliği.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Genel sembollerin statik konumları vardır; Ayrıntılar için bkz. [Sembol Konumları.](../../debugger/debug-interface-access/symbol-locations.md)|
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|`BOOL`|`TRUE` simgesinin konumu yönetilen kodda ise.|
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|`BOOL`|`TRUE` sembolün konumu Microsoft Ara Dil (MSIL) kodunda ise.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Sembolün tam olarak dekore edilmiş adı.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Sembolün dizin kimliği.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Sembolün bloğu içindeki göreli konumu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagPublicSymbol` [(SymTagEnum Numaralama değerlerinden](../../debugger/debug-interface-access/symtagenum.md) biri).|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Düzeltlanmamış sembol adı.|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Düzeltlanmamış sembol adının bir bölümü veya hepsi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
