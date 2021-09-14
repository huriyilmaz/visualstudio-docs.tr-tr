---
description: bir işlevde hata ayıklamanın başlayacağı tanımlı bir nokta varsa, bu nokta SymTagFuncDebugStart etiketine sahip bir sembolle tanımlanır.
title: FuncDebugStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 816228f0eb5d52e037192f9ed29c64638ce13876
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630590"
---
# <a name="funcdebugstart"></a>FuncDebugStart
bir işlevde hata ayıklamanın başlayacağı tanımlı bir nokta varsa, bu nokta etiketli bir sembolle `SymTagFuncDebugStart` tanımlanır.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için geçerli olan özellikler gösterilir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun kaydırma bölümü; Ayrıntılar için bkz. [LocationType Numaralama.](../../debugger/debug-interface-access/locationtype.md)|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType Numaralama.](../../debugger/debug-interface-access/locationtype.md)|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` işlevi özel bir çağırma kuralı kullanıyorsa (yalnızca v8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` işlevi uzak bir dönüş gerçekleştirirse (yalnızca v8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` işlevi kesmeden dönüş içeriyorsa (yalnızca v8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` işlevi statik olarak işaretlenirse (yalnızca v8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan işlevin simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözcük üst simgesinin kimliği.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Başlangıç noktalarının statik konumları vardır; Ayrıntılar için bkz. [Sembol Konumları.](../../debugger/debug-interface-access/symbol-locations.md)|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` işlevi [noinline](/cpp/cpp/noinline) özniteliğiyle belirtilmişse (yalnızca v8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` işlevi [noreturn](/cpp/cpp/noreturn) özniteliğiyle belirtilmişse (yalnızca v8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` işlevi hiç çağrılmasa (yalnızca v8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Bellekte sembolün uzaklığı; Ayrıntılar için bkz. [LocationType Numaralama ,](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` .|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` kodda iyileştirilmiş kod için hata ayıklama bilgileri varsa (yalnızca DIA SDK v8.0 veya sonraki bir sonraki bir kodda).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|İşlevin bloğu içindeki göreli konumu.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Sembolün dizin kimliği.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagFuncDebugStart` [(SymTagEnum Numaralama değerlerinden](../../debugger/debug-interface-access/symtagenum.md) biri).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|İşlevin yürütülebilir dosya içindeki konumu.|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
