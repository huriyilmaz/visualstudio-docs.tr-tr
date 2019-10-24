---
title: CompilandDetails | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b72a5ae53c336877c68cc9b164cf787017dacbe2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745417"
---
# <a name="compilanddetails"></a>CompilandDetails
Compiland bilgileri, `SymTagCompiland` etiketi (düşük ayrıntı) ve `SymTagCompilandDetails` etiketi (yüksek ayrıntı) ile semboller arasında bölünür. `SymTagCompilandDetails` ek sembolleri yüklemeyi gerektirir. Ancak, `SymTagCompiland` simgesiyle kullanılamayan compiland hakkında çok fazla bilgi sağlar.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Derleyicinin arka uç derleme numarası.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Derleyicinin arka uç ana sürüm numarası.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Derleyicinin arka uç alt sürüm numarası.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Bu compiland üreten derleyicinin adı (yalnızca DIA SDK V 8.0 veya üzeri).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|derlemede Düzenle ve devam et etkinleştirildiyse `TRUE`.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Derleyicinin ön uç derleme numarası.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Derleyicinin ön uç büyük sürüm numarası.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Derleyicinin ön uç alt sürüm numarası.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|Bu compiland hata ayıklama bilgileri (yalnızca DIA SDK V 8.0 veya üzeri) varsa `TRUE`.|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|Bu compiland yönetilen kod (yalnızca DIA SDK v 8.0 veya üzeri) içeriyorsa `TRUE`.|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|compiland, [/GS (arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check) derleyici anahtarıyla derlenmişse (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde) `TRUE`.|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|compiland ortak ara dil (CıL) kodundan yerel koda dönüştürülmüşse `TRUE`.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|Kullanıcı tanımlı türler (UDT) belirtilen bellek sınırlarına (yalnızca DIA SDK V 8.0 veya üzeri) hizalanmışsa `TRUE`.|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|compiland, [/hotpatch (düzeltme eki uygulanabilir görüntü oluşturma)](/cpp/build/reference/hotpatch-create-hotpatchable-image) derleyici anahtarı (yalnızca DIA SDK v 8.0 veya üzeri) ile derlenmişse `TRUE`.|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|compiland, [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation) derleyicisi anahtarıyla derlenmişse (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde) `TRUE`.|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Compiland bir Microsoft ara dili (MSIL) modülüdür (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde) TRUE.|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Kaynak kodu dili.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Compiland sembolü.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Compiland 'nin derlendiği platform ( [CV_CPU_TYPE_e sabit listesi](../../debugger/debug-interface-access/cv-cpu-type-e.md) değerlerinden biri).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|`SymTagCompilandDetails` döndürür ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|

## <a name="remarks"></a>Açıklamalar
 Derleyiciler genellikle iki taramalı derleyici olarak bilinen bir biçimde gelir; bazı derleyici sürümlerinde her geçiş ayrı bir program tarafından işlenir. Bunlar sırasıyla ön uç ve arka uç derleyicileri olarak bilinir, bu nedenle arka uç ve ön uç sürüm numaraları için sembol özellikleri.

## <a name="see-also"></a>Ayrıca bkz.
- [Compiland](../../debugger/debug-interface-access/compiland.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)