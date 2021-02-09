---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
description: INTERCEPT_EXCEPTION_ACTION numaralandırması, Visual Studio Hata ayıklamasında özel durumları kesintiye uğratan gerçekleştirilecek eylemi belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5e1038ac2515198d5eb20b66f346f7a6798c25a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852809"
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
