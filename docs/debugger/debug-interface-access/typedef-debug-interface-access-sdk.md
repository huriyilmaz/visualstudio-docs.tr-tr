---
description: SymTagTypedef etiketlerine sahip semboller, diğer türlerin adlarını içerir.
title: Typedef (Arabirim Erişimi SDK'sı Hata Ayıklama) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Typedef symbol [DIA SDK]
ms.assetid: 9ab441b9-cc72-47fa-83e2-87b3c2b891b4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9777111bf9b1474b783a62cf6e65a7a224e865ff
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626618"
---
# <a name="typedef-debug-interface-access-sdk"></a>Typedef (Arabirim Erişimi SDK'sında Hata Ayıklama)
Etiketlere `SymTagTypedef` sahip semboller, diğer türler için adlar sağlar.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda bu sembol türü için ek geçerli özellikler gösterilir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|[BasicType Enumeration değerlerinden](../../debugger/debug-interface-access/basictype.md) biri.|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Varsa, bu typedef'in sınıf üst öğesi.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Sınıf üst simgesinin kimliği.|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` bu typedef bir oluşturucuya sahipse.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` bu typedef sabit olarak işaretlenirse.|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` bu typedef bir atama işlecine sahipse.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE` Bu typedef bir tür tür yazma işlecine sahipse.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE` bu typedef iç içe geçmiş türlere sahipse.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Bu typedef'in bayt cinsinden uzunluğu.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan derlemenin simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözcük üst simgesinin kimliği.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Typedef'in adı.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` Bu tür tanımlaması sözcüksel bir kapsamda iç içe geçmişse.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` bu typedef aşırı yüklenmiş bir işleci varsa.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE` bu typedef paketli ise.|
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|`BOOL`|`TRUE` bu typedef bir başvuru ise.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` Bu typedef, küresel olmayan sözcüksel bir kapsamda ise.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Sembolün dizin kimliği.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagTypedef` [(SymTagEnum Numaralama değerlerinden](../../debugger/debug-interface-access/symtagenum.md) biri).|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Temel alınan türün simgesi.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Tür simgesinin kimliği.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|[UdtKind Enumeration değerlerinden](../../debugger/debug-interface-access/udtkind.md) biri.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` bu typedef hizalanmamışsa.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Sanal tablo şeklini açıklayan simge.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|Sanal tablo şekil simgesinin kimliği.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` bu typedef geçici olarak işaretlenirse.|

## <a name="remarks"></a>Açıklamalar
 Bir typedef bir sınıfı, işaretçiyi veya kullanıcı tanımlı türü (UDT) temsileye sahip olduğu için, typedef sembolü bu diğer sembol türlerinden biri ile aynı özellikleri paylaşıyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
