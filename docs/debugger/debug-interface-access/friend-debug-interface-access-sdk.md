---
description: Arkadaş sınıfları ve arkadaş işlevleri SymTagFriend sembolleriyle tanımlanır.
title: Arkadaş (Arabirim Erişimi SDK'sı Hata Ayıklama) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- friend functions [DIA SDK]
- friend classes [DIA SDK]
- Friend symbol
ms.assetid: 5147a170-41ce-4727-8ace-c318e8d11647
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8bf377f4a7e8602f037f35de15bf330484f869be
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134772"
---
# <a name="friend-debug-interface-access-sdk"></a>Arkadaş (Arabirim Erişimi SDK'sında Hata Ayıklama)
Arkadaş sınıfları ve arkadaş işlevleri sembollerle `SymTagFriend` tanımlanır. Bunlar, üst kullanıcı tanımlı türlerin (UDT) alt öğesidir ve [IDiaSymbol::get_classParent özelliğine](../../debugger/debug-interface-access/idiasymbol-get-classparent.md) sahip olur.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için ek geçerli özellikler gösterilir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|UDT üst öğesi simgesi.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Sınıf üst simgesinin kimliği.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Sınıf veya işlevin adı.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Sembolün dizin kimliği.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagFriend` [(SymTagEnum Numaralama değerlerinden](../../debugger/debug-interface-access/symtagenum.md) biri).|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Sınıf veya işlevin simgesi.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Tür simgesinin kimliği.|

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
