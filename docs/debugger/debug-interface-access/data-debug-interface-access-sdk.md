---
title: Veri (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94e1be7a1809c52683be045f71fcc681a6b270a8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745293"
---
# <a name="data-debug-interface-access-sdk"></a>Veriler (Arabirim Erişimi SDK'sında Hata Ayıklama)
Parametreler, yerel değişkenler, genel değişkenler ve sınıf üyeleri gibi tüm değişkenler `SymTagData` simgeleri tarafından tanımlanır. Sabit değerler (`LocIsConstant`) bu türle de tanımlanır.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Bir alan ise, [CV_access_e sabit](../../debugger/debug-interface-access/cv-access-e.md)listesinin değerlerinden biri.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun konum parçası; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|Bu veri adresine başka bir sembol tarafından başvuruluyorsa `TRUE`.|
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Konumun bit konumu; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md) (DIA SDK v 8.0 'da desteklenmez).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Bu bir yapı, birleşim veya sınıf alanı ise, sınıfın simgesi.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Sınıf üst simgesinin KIMLIĞI.|
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|veriler derleyici tarafından oluşturulduysa `TRUE`.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|veriler sabit olarak işaretlenmişse `TRUE`.|
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|[DataKind sabit listesi](../../debugger/debug-interface-access/datakind.md) değerlerinden biri.|
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|veriler toplanmış bir veri türünün parçasıysa (yalnızca DIA SDK v 8.0 ve üzeri sürümlerde) `TRUE`.|
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|veriler birden çok simgenin toplamasını (yalnızca DIA SDK v 8.0 ve üzeri sürümlerde) bölündüğünde `TRUE`.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Bitfield uzunluğu; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan compiland, Function veya Block sembolü.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|İzin verilen herhangi bir konum türü; Ayrıntılar için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md)|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Değişkenin adı.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Kayıt içeriğinden fark; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Konum göstergesini Kaydet; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Verilerin bloğu içinde göreli konumu.|
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Verilerin yuva numarasını alır.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|@No__t_0 döndürür ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Verileri temsil eden meta veri belirteci.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Değişken türü için simge.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Değişken türü sembolünün KIMLIĞI.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|veriler hizalanmamış ise `TRUE`.|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Sabit verilerin değeri.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Verilerin yürütülebilir içindeki konumu.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|veriler geçici olarak işaretlenmişse `TRUE`.|

## <a name="see-also"></a>Ayrıca bkz.
- [CV_access_e Numaralandırması](../../debugger/debug-interface-access/cv-access-e.md)
- [DataKind Numaralandırması](../../debugger/debug-interface-access/datakind.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)