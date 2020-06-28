---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 746ff69de6f58f85d16982522c6ac13dcbf4ce6a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460974"
---
# <a name="udtkind"></a>UdtKind
Kullanıcı tanımlı farklı tür (UDT) açıklanmaktadır.

## <a name="syntax"></a>Syntax

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Öğeler
UdtStruct UDT bir yapıdır.

UdtClass UDT bir sınıftır.

Udtuniyon UDT bir birleşimdir.

Udtınterface UDT bir arabirimdir.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler [IDiaSymbol:: get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) yöntemi tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
