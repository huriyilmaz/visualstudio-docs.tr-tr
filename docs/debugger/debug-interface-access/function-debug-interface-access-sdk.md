---
title: İşlev (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd901d1bb54f91042e0a8134f1f3cba6c29b396a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745134"
---
# <a name="function-debug-interface-access-sdk"></a>İşlev (Arabirim Erişimi SDK'sında Hata Ayıklama)
Her işlev bir `SymTagFunction` simgesiyle tanımlanır.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|`Data type`|Açıklama|
|--------------|-----------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|İşlev bir üye işlevise, [CV_access_e numaralandırmanın](../../debugger/debug-interface-access/cv-access-e.md)değerlerinden biri.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun konum parçası; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|İşlev bir üye işlevise, sınıfın simgesi.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Sınıf üst simgesinin KIMLIĞI.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|işlev bir sabit olarak işaretlenmişse `TRUE`.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|işlev özel bir çağırma kuralı (yalnızca DIA SDK V 8.0 veya üzeri) kullanıyorsa `TRUE`.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|işlev bir-Return (yalnızca DIA SDK V 8.0 veya üzeri) gerçekleştirdiğinde `TRUE`.|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|işlev ayrılmış bellek işlevini (yalnızca uınnder DIA SDK V 8.0 veya üzeri) kullanıyorsa `TRUE`.|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|işlev stil özel durum işleme C++(yalnızca DIA SDK v 8.0 veya üzeri) içeriyorsa `TRUE`.|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|işlev zaman uyumsuz özel durum işleme (yalnızca DIA SDK V 8.0 veya üzeri) içeriyorsa `TRUE`.|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|işlev satır içi derleme içeriyorsa (yalnızca DIA SDK V 8.0 veya üzeri) `TRUE`.|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|işlev bir [longjmp](/cpp/c-runtime-library/reference/longjmp) çağrısı (yalnızca DIA SDK v 8.0 veya üzeri) içeriyorsa `TRUE`.|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|işlev güvenlik denetimleri (yalnızca DIA SDK V 8.0 veya üzeri) içeriyorsa `TRUE`.|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|işlev Win32 stili yapılandırılmış özel durum işleme (yalnızca DIA SDK V 8.0 veya üzeri) içeriyorsa `TRUE`.|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|işlev bir [setjmp](/cpp/c-runtime-library/reference/setjmp) çağrısı (yalnızca DIA SDK v 8.0 veya üzeri) içeriyorsa `TRUE`.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|işlevin kesmede (yalnızca DIA SDK V 8.0 veya üzeri) bir dönüşü varsa `TRUE`.|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|bir işlev giriş sanal ise `TRUE`.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|işlev [satır içi, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp) özniteliklerinden biri ile işaretlenmişse `TRUE`.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|işlev [Naked](/cpp/cpp/naked-cpp) özniteliğiyle işaretlenmişse (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde) `TRUE`.|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|işlev statikse (yalnızca DIA SDK V 8.0 veya üzeri) `TRUE`.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Konumdan başlayarak işlev kodundaki bayt sayısı.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan compiland 'ın simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|İşlevler statik veya meta veri konumlarına sahip olabilir; Ayrıntılar için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|İşlevin adı.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|işlev bir satır içi işlev değilse `TRUE` (yalnızca n DIA SDK V 8.0 veya üzeri).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|işleve ulaşılamıyorsa `TRUE` (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|işlev bir değer döndürmezse (yalnızca DIA SDK V 8.0 veya üzeri) `TRUE`.|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|işlev arabellek güvenlik denetimleriyle derlenmişse, ancak yığın sıralaması yapılamadığını `TRUE`.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|kodun, iyileştirilmiş koda yönelik hata ayıklama bilgileri varsa `TRUE` (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|işlev saf sanal ise `TRUE`.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Bu işlevin modülünün içindeki göreli konumu.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|`SymTagFunction` döndürür ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|İşlev için meta veri belirteci.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|İşlev imzasının simgesi.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Tür sembolünün KIMLIĞI.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|işlev hizalanmamış ise `TRUE`.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|İşlev adının süslenmiş biçimi (yalnızca DIA SDK v 8.0 veya üzeri)|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|İşlev adının bir kısmı veya tamamı (yalnızca DIA SDK v 8.0 veya üzeri).|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|sanal bir işlev `TRUE`.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Bu işlevin yürütülebilir görüntü içinde konumu.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Sanal bir işlev ise, sanal işlev tablosundaki fark.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|işlev geçici olarak işaretlenmişse `TRUE`.|

## <a name="see-also"></a>Ayrıca bkz.
- [CV_access_e Numaralandırması](../../debugger/debug-interface-access/cv-access-e.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)