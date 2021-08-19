---
description: Kullanıcı tanımlı türün (UDT) çeşitliliğini açıklar.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a8f9a065ceb5fce06f01c1e64c6d5acf48959539
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052175"
---
# <a name="udtkind"></a>UdtKind
Kullanıcı tanımlı türün (UDT) çeşitliliğini açıklar.

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

UdtUnion UDT bir birlikteliktir.

UdtInterface UDT bir arabirimdir.

## <a name="remarks"></a>Açıklamalar
Bu numaralamada yer alan değerler [IDiaSymbol::get_udtKind yöntemi tarafından](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
