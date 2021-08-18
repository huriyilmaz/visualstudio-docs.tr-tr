---
description: Bir IDebugField nesnesinden gerçekleştirilecek bilgi türlerini temsil eden geçerli değerleri sıralar ve kullanıcıya görüntüler.
title: DisplayKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f491751cb3ef14537ab4be112722c957ea0fc20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065039"
---
# <a name="displaykind"></a>DisplayKind
Bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesinden gerçekleştirilecek bilgi türlerini temsil eden geçerli değerleri sıralar ve kullanıcıya görüntüler.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

## <a name="fields"></a>Alanlar
`DisplayKind_Value`\
Alanın değeri.

`DisplayKind_Name`\
Alanın adı.

`DisplayKind_Type`\
Alan türü.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: ee. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
