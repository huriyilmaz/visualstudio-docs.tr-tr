---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
description: Uygulama INTERCEPT_EXCEPTION_ACTION, hata ayıklama sırasında özel durumların araya geldiğinde hangi eylemin Visual Studio belirtir.
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
ms.openlocfilehash: 0b704e8f6379312eee25be7106f4d4db6c64bf626aee4e0dfe0b899a735fe9a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377255"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
Özel durumlara müdahale etmek için hangi eylemlerin gerçekleştirin olduğunu belirtir.

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
Geçerli özel durumun araya müdahalesini sağlar. Şu anda desteklenen tek değer bu ve belirtilmelidir.

## <a name="remarks"></a>Açıklamalar
Bu değerler [InterceptCurrentException yöntemine](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
