---
title: BaseType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BaseType symbol [DIA SDK]
ms.assetid: 2f9e22e6-8360-496a-ac6b-17a5a56b0c46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d49969f1897529de770063be1a7acc0f035e5ef9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462290"
---
# <a name="basetype"></a>BaseType
Temel türler semboller tarafından tanımlanır `SymTagBaseType` .

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için ek geçerli özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|[BasicType numaralandırması](../../debugger/debug-interface-access/basictype.md)değerlerinden biri.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` temel tür const olarak işaretlenmişse.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Taban türünün bayt cinsinden boyutu.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan [compiland](../../debugger/debug-interface-access/compiland.md)'ın simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagBaseType` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` temel tür hizalanmamış ise.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` temel tür geçici olarak işaretlenmişse.|

## <a name="see-also"></a>Ayrıca bkz.
- [BasicType Numaralandırması](../../debugger/debug-interface-access/basictype.md)
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)