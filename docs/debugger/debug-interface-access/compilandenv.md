---
title: CompilandEnv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandEnv symbol
ms.assetid: 808404bb-ece1-47f1-b9ea-c76d4d86ddd9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94a27ada5f56d4525824335faebf1e19426241ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462248"
---
# <a name="compilandenv"></a>CompilandEnv
Derleyici, simgelere sahip ek ortam değişkenleri içerebilir. `SymTagCompilandEnv`Bu değişkenlerin her biri için bir sembol vardır.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Üst compiland sembolü.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Değişkenin adı.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagCompilandEnv` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Değişkenin dize değerli içerikleri ( `VT_BSTR` ).|

## <a name="see-also"></a>Ayrıca bkz.
- [Compiland](../../debugger/debug-interface-access/compiland.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)