---
title: FuncDebugStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 339ee81dee59ae57e456fe0f38f1098783390259
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745151"
---
# <a name="funcdebugstart"></a>FuncDebugStart
Bir işlevde hata ayıklamanın başlayacağı tanımlı bir nokta varsa, bu nokta `SymTagFuncDebugStart` etiketiyle bir sembol tarafından tanımlanır.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun konum parçası; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|işlev özel bir çağırma kuralı (yalnızca DIA SDK v 8.0 veya üzeri) kullanıyorsa `TRUE`.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` işlevi bir far return gerçekleştirdiğinde (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` işlevi kesmede (yalnızca DIA SDK v 8.0 veya üzeri) bir dönüş içeriyorsa.|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|işlev statik olarak işaretlenmişse `TRUE` (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan işlevin simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Başlangıç noktaları statik konumlara sahiptir; Ayrıntılar için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|işlev [noinline](/cpp/cpp/noinline) özniteliğiyle belirtilmişse (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde) `TRUE`.|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|işlev [noreturn](/cpp/cpp/noreturn) özniteliğiyle belirtilmişse (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde) `TRUE`.|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|işlev hiçbir şekilde çağrılmadıysa `TRUE` (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde).|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Simgenin bellekteki boşluğu; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|kodun, iyileştirilmiş koda yönelik hata ayıklama bilgileri varsa `TRUE` (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|İşlevin bloğu içindeki göreli konumu.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|@No__t_0 döndürür ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|İşlevin yürütülebilir içindeki konumu.|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)