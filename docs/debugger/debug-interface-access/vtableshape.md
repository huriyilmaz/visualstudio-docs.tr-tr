---
description: VTable) simgesi, SymTagVTableShape etiketiyle tanımlanan bir sınıf alt simgesine sahip.
title: VTableShape | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- VTableShape symbol
- SymTagVTableShape tag
ms.assetid: dd97f4c3-115d-46a9-b506-2531e30a0d8f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6e9fce98005db2d6c34e1b76c6ced71535c3cc2b550b453dacd04f159fd3afd0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404613"
---
# <a name="vtableshape"></a>VTableShape
[VTable sembolü,](../../debugger/debug-interface-access/vtable.md) etiketiyle tanımlanan bir sınıf alt `SymTagVTableShape` simgesine sahip.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için ek geçerli özellikler gösterilir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` VTable'ın sınıfı sabit olarak işaretlenmişse.|
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|VTable'daki girdilerin sayısı.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan derlemenin simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözcük üst simgesinin kimliği.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Sembolün dizin kimliği.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagVTableShape` [(SymTagEnum Numaralama değerlerinden](../../debugger/debug-interface-access/symtagenum.md) biri).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` VTable'ın sınıfı hizalanmamışsa.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` VTable'ın sınıfı geçici olarak işaretlenirse.|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [VTable](../../debugger/debug-interface-access/vtable.md)
