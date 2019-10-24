---
title: UsingNameSpace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UsingNamespace symbol tag
ms.assetid: e8e1beb5-7cb9-43b4-9ff4-760d5f91ea2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d078e8af5f579556fb865a4d92084220afecc83
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738431"
---
# <a name="usingnamespace"></a>UsingNameSpace
Bazı semboller ad alanı tarafından adlandırılabilir ve daha sonra bir `SymTagUsingNameSpace` etiketiyle tanımlanır.

> [!NOTE]
> UsingNamespace sembol etiketi yalnızca yönetilen kodda görünür.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan compiland, Block veya Function için simge.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Ad alanı adı.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|@No__t_0 döndürür ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)