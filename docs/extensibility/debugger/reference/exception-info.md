---
description: Hata ayıklamakta olan program tarafından oluşturulan bir özel durumu veya çalışma zamanı hatasını açıklar.
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ec97b56cc7fca8c2185d7180a8d34e87b084b11
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059476"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Hata ayıklamakta olan program tarafından oluşturulan bir özel durumu veya çalışma zamanı hatasını açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Üyeler
`pProgram`\
Özel durumun gerçekleştiği programı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`bstrProgramName`\
Özel durumun gerçekleştiği programın adı.

`bstrExceptionName`\
Özel durumun adı.

`dwCode`\
Özel durum veya çalışma zamanı hatası için kimlik kodu.

`dwState`\
Özel durumun durumunu tanımlayan [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Numaralandırmadaki bir değer.

`guidType`\
GUID dil tanımlayıcısı, ya da `guidLang` `guidEng` .

## <a name="remarks"></a>Açıklamalar
Bu yapı, [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) ve [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) yöntemlerine bir parametre olarak geçirilir. Bu yapı ayrıca doldurulacak [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) yöntemine geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
