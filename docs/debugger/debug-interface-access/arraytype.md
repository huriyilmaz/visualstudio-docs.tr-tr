---
title: ArrayType | Microsoft Docs
description: Visual Studio hata ayıklama arabirimi erişim SDK 'sında ArrayType sembol türü (symtagarray) hakkında başvuru bilgileri bulun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ArrayType symbol
ms.assetid: 1d973a3a-2bde-46df-8625-85d519bb3cc9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1419ce27f775b99424427b474ef8b94f5ff5a016154d011cb2127e48616f520a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121326704"
---
# <a name="arraytype"></a>ArrayType
Bir dizi bir sembol tarafından tanımlanır `SymTagArray` .

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için ek geçerli özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|`IDiaSymbol*`|Dizi dizini türü için simge.|
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|`DWORD`|Dizi dizini türü sembolünün KIMLIĞI.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` dizi const olarak işaretlenmişse.|
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|Dizideki öğe sayısı.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Bu dizinin bayt cinsinden boyutu.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan compiland 'ın simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|`DWORD`|Bir FORTRAN çok boyutlu dizisinin sıralaması.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagArray` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Dizi öğesi türü için simge.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Dizi öğesi türü sembolünün KIMLIĞI.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` dizi hizalanmamış ise|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` dizi geçici olarak işaretlenmişse.|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [Boyut](../../debugger/debug-interface-access/dimension.md)