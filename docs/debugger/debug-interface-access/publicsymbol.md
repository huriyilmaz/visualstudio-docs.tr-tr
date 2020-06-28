---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f552aa8bc887d2b9bcaacdcf2947ac6781a7879c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461114"
---
# <a name="publicsymbol"></a>PublicSymbol
. Exe dosyası oluşturulduğunda, her genel simgeye (en azından, her genel işleve ve veri simgesine) bir `SymTagPublicSymbol` etiket verilir.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun konum parçası; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|`BOOL`|`TRUE`simgenin konumu koddur.|
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|`BOOL`|`TRUE`sembol bir işlevdir.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Bu sembolün bayt cinsinden uzunluğu.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Genel kapsam için simge.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Ortak semboller statik konumlara sahiptir; Ayrıntılar için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|`BOOL`|`TRUE`simgenin konumu yönetilen kodda ise.|
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|`BOOL`|`TRUE`simgenin konumu Microsoft ara dili (MSIL) kodtümcesinde.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Simgenin tamamen düzenlenmiş adı.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Simgenin blok içinde göreli konumu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagPublicSymbol` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Süslenmiş sembol adı.|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Sınıflandırılmamış sembol adının bir kısmı veya tamamı.|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)