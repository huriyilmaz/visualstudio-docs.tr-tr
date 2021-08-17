---
title: CompilandDetails | Microsoft Docs
description: Hata ayıklama arabirimi erişim SDK'sı içinde CompilandDetails sembol türü (SymTagCompilandDetails) Visual Studio başvuru bilgilerini bulun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f2817e37d088f8d125b18b4e39051966b690c683
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059014"
---
# <a name="compilanddetails"></a>CompilandDetails
Compiland bilgileri, etiket (düşük `SymTagCompiland` ayrıntı) ve etiket (yüksek ayrıntı) ile `SymTagCompilandDetails` semboller arasında bölünüyor. `SymTagCompilandDetails` , bir sembolle mevcut olan compiland hakkında zengin bilgiler `SymTagCompiland` sağlar.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için geçerli olan özellikler gösterilir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Derleyicinin arka uç derleme numarası.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Derleyicinin arka uç ana sürüm numarası.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Derleyicinin arka uç ikincil sürüm numarası.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Bu derlemeyi üreten derleyicinin adı (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Düzenle ve Devam'ın derleme sırasında etkinleştirildiyse.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Derleyicinin ön uç derleme numarası.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Derleyicinin ön uç ana sürüm numarası.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Derleyicinin ön uç ikincil sürüm numarası.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Bu derlemede hata ayıklama bilgileri varsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Bu derleme yönetilen kod içeriyorsa (yalnızca v8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` derleme [/GS (Arabellek](/cpp/build/reference/gs-buffer-security-check) Güvenlik Denetimi) derleyici anahtarıyla derlenmişse (yalnızca V8.0 veya sonraki bir DIA SDK içinde).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` compiland, Ortak Ara Dil (CIL) kodundan yerel koda dönüştürülecekse.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` kullanıcı tanımlı türler (UDT) belirli bir bellek sınırına hizalanmışsa (yalnızca V8.0 veya DIA SDK içinde).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` compiland [/hotpatch (Hotpatchable Image Oluştur)](/cpp/build/reference/hotpatch-create-hotpatchable-image) derleyici anahtarıyla derlenmişse (yalnızca v8.0 veya sonraki bir DIA SDK içinde).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` derleme [/LTCG (Bağlantı](/cpp/build/reference/ltcg-link-time-code-generation) Zamanı Kod Oluşturma) derleyici anahtarıyla derlenmişse (yalnızca V8.0 veya sonraki bir DIA SDK içinde).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Compiland bir Microsoft Ara Dil (MSIL) modülü ise TRUE (yalnızca DIA SDK v8.0 veya sonraki bir sürümü için).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Kaynak kod dili.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Derlemenin simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözcük üst simgesinin kimliği.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Derlemenin derlenmiş olduğu platform (Enumeration CV_CPU_TYPE_e [biri).](../../debugger/debug-interface-access/cv-cpu-type-e.md)|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Sembolün dizin kimliği.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagCompilandDetails` [(SymTagEnum Numaralama değerlerinden](../../debugger/debug-interface-access/symtagenum.md) biri).|

## <a name="remarks"></a>Açıklamalar
 Derleyiciler genellikle iki geçişli derleyici olarak bilinen bir formda gelir; bazı derleyici sürümlerinde, her geçiş ayrı bir program tarafından işlenmiş. Bunlar sırasıyla ön uç ve arka uç derleyicileri olarak bilinir, dolayısıyla arka uç ve ön uç sürüm numaraları için sembol özellikleri.

## <a name="see-also"></a>Ayrıca bkz.
- [Compiland](../../debugger/debug-interface-access/compiland.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)