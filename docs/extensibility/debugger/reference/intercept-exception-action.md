---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
description: INTERCEPT_EXCEPTION_ACTION numaralandırması Visual Studio hata ayıklamada özel durumları kesintiye uğradığında gerçekleştirilecek eylemi belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fddfa37457a4783066a2319b081bf4372e7e06d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125393"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
Özel durumları kesintiye girilirken gerçekleştirilecek eylemleri belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
typedef DWORD INTERCEPT_EXCEPTION_ACTION;
```

```csharp
public enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
```

## <a name="parameters"></a>Parametreler

`IEA_INTERCEPT`\
Geçerli özel durumu kesintiye uğratan izin vermez. Bu, şu anda desteklenen tek değerdir ve belirtilmelidir.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [Yakatcurrentexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
