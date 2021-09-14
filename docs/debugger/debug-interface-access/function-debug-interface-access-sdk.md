---
description: Her işlev bir SymTagFunction simgesiyle tanımlanır.
title: İşlev (Arabirim Erişimi SDK'sı Hata Ayıklama) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 90a1e73ad968875a12531ccb620543484c26333e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630585"
---
# <a name="function-debug-interface-access-sdk"></a>İşlev (Arabirim Erişimi SDK'sında Hata Ayıklama)
Her işlev bir sembolle `SymTagFunction` tanımlanır.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için geçerli olan özellikler gösterilir.

|Özellik|Veri türü|Açıklama|
|--------------|-----------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|İşlev üye bir [işlevse CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)için enumeration değerlerini kullanın.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun kaydırma bölümü; Ayrıntılar için bkz. [LocationType Numaralama.](../../debugger/debug-interface-access/locationtype.md)|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType Numaralama.](../../debugger/debug-interface-access/locationtype.md)|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|İşlev bir üye işlevi ise sınıfının simgesi.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Sınıf üst simgesinin kimliği.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` işlevi sabit olarak işaretlenirse.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` işlevi özel bir çağırma kuralı kullanıyorsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` işlevi uzak bir dönüş gerçekleştirirse (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` işlevi ayrılmış bellek işlevi kullanıyorsa (yalnızca uinnder DIA SDK V8.0 veya sonraki bir sonraki bir 1.|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` işlevi C++stili özel durum işleme içeriyorsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` işlevi zaman uyumsuz özel durum işleme içeriyorsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` işlevi satır içi derleme içeriyorsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` işlevi bir [longjmp çağrısı](/cpp/c-runtime-library/reference/longjmp) içeriyorsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` işlevi güvenlik denetimleri içeriyorsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` işlevi Win32 stili yapılandırılmış özel durum işleme içeriyorsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` işlevi bir [setjmp](/cpp/c-runtime-library/reference/setjmp) çağrısı içeriyorsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` işlevin kesmeden dönüş (yalnızca V8.0 veya DIA SDK) dönüş varsa.|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` bir işlev sanala giriş ise.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` İşlev satır içi, __inline ve [_forceinline \_ ](/cpp/cpp/inline-functions-cpp) işaretlendi.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` işlevi çıplak özniteliğiyle [işaretlenirse](/cpp/cpp/naked-cpp) (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` statikse (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Konumdan başlayarak işlev kodunun bayt sayısı.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan derlemenin simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözcük üst simgesinin kimliği.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|İşlevlerin statik veya meta veri konumları olabilir; Ayrıntılar için bkz. [Sembol Konumları.](../../debugger/debug-interface-access/symbol-locations.md)|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|İşlevin adı.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` işlevi bir satır içi işlev (V8.0 veya DIA SDK değil) ise.|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` işlevine ulaşılamazsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` işlevi bir değer (yalnızca V8.0 veya DIA SDK içinde) dönse.|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` işlevi arabellek güvenlik denetimleriyle derlenmiş ancak yığın sıralaması yapılamayabilirsiniz.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Kodda iyileştirilmiş kod için hata ayıklama bilgileri varsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` işlevi saf sanal ise.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Bu işlevin modülü içindeki göreli konumu.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Sembolün dizin kimliği.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagFunction` [(SymTagEnum Numaralama değerlerinden](../../debugger/debug-interface-access/symtagenum.md) biri).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|İşlev için meta veri belirteci.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|İşlev imzasının simgesi.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Tür simgesinin kimliği.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` işlevi hizalanmamışsa.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|İşlev adının düzeltlanmamış biçimi (yalnızca v8.0 veya DIA SDK içinde)|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|İşlev adının (yalnızca v8.0 veya sonraki bir DIA SDK veya sonrası) bir bölümü veya hepsi.|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` sanal bir işlevse.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Bu işlevin yürütülebilir görüntü içindeki konumu.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Bir sanal işlev ise, sanal işlev tablosunda uzaklığı.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` İşlev geçici olarak işaretlenirse.|

## <a name="see-also"></a>Ayrıca bkz.
- [CV_access_e Numaralandırması](../../debugger/debug-interface-access/cv-access-e.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType Numaralandırması](../../debugger/debug-interface-access/locationtype.md)
- [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
