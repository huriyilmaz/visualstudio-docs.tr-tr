---
description: Her dönüştürücü bir Symtagdönüştürücü etiketiyle tanımlanır.
title: Dönüştürücü | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- thunk properties [DIA SDK]
- thunk symbol
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f4a06eed799b06a3d2809b4e10dc09090a92f9c9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626630"
---
# <a name="thunk"></a>Dönüştürücü
Her biri `thunk` bir etiketi tarafından tanımlanır `SymTagThunk` .

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|[CV_access_e numaralandırma](../../debugger/debug-interface-access/cv-access-e.md) değerlerinden biri olan (yalnızca DIA SDK v 8.0 veya üzeri) bir değiştirici özniteliğine erişin.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun konum parçası; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Eğer varsa, sınıf üst öğesi (yalnızca DIA SDK V 8.0 veya üzeri).|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Kapsayan sınıf üst sembolünün KIMLIĞI (yalnızca DIA SDK V 8.0 veya üzeri).|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|Dönüştürücü sabit olarak işaretlenmişse (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde) TRUE.|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|Dönüştürücü bir sanal işleve giriş ise (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde) doğru|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|Dönüştürücü statik kabul edildiğinde TRUE (yalnızca DIA SDK V 8.0 veya üzeri).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Dönüştürücü içindeki kodun bayt sayısı.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan compiland, Block veya Function için simge.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Bitiş noktalarında statik konum vardır; Ayrıntılar için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md) numaralandırması.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Dönüştürücü adı.|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|Dönüştürücü yalnızca sanal ise (yalnızca DIA SDK V 8.0 veya üzeri) geçerlıdır.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Bu dönüştürücü modülünün modülü içinde göreli konumu.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagThunk` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Dönüştürücü hedefinin konumunun bir parçasını kaydırın.|
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|Kapsayan bloğunda dönüştürücü hedefinin göreli sanal adresi.|
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Dönüştürücü hedefinin bölüm bölümü.|
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Yürütülebilir görüntüdeki dönüştürücü hedefinin konumu.|
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|[THUNK_ORDINAL numaralandırması](../../debugger/debug-interface-access/thunk-ordinal.md)tarafından tanımlanan dönüştürücü türü.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Bu dönüştürücü türü (yalnızca DIA SDK V 8.0 veya üzeri).|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Tür sembolünün KIMLIĞI (yalnızca DIA SDK V 8.0 veya üzeri).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` dönüştürücü hizalanmazsa (yalnızca DIA SDK V 8.0 veya üzeri),|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` dönüştürücü sanal ise (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Bu dönüştürücü için yürütülebilir görüntü içinde konum.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Sanal tablodaki Bu dönüştürücü için fark (yalnızca DIA SDK V 8.0 veya üzeri).|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` dönüştürücü geçici olarak işaretlenmişse (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [THUNK_ORDINAL Numaralandırması](../../debugger/debug-interface-access/thunk-ordinal.md)
