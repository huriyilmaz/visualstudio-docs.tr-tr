---
description: Ayrık akışın kapsamını belirtir.
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f33c8489746f857ebb7c9225af6dce73161edad5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073090"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Ayrık akışın kapsamını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Alanlar
`DSS_HUGE`\
Kod bağlamını parçalara ayırarak bir istemcinin genellikle tek bir çağrıda almak istemesi gerekenden daha fazla çıkış oluşturabileceklerini belirtir.

`DSS_FUNCTION`\
Kod bağlamının içerdiği işlevin birikerek biriktiri gerektiğini belirtir. Ayrık akışın [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) yöntemi tarafından döndürülen bir işlevi temsil ettiğini belirtir.

`DSS_MODULE`\
yöntemi tarafından `IDebugDisassemblyStream2::GetScope` döndürülen, ayrık akışın bir modülü temsil ettiğini belirtir.

`DSS_ALL`\
Adres alanı tamamının ayrımına göre belirtir.

## <a name="remarks"></a>Açıklamalar
[GetDisassemblyStream yöntemine bağımsız](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) değişken olarak geçirilir ve [GetScope yöntemi tarafından](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) döndürülür.

Bu değerler bitwise ile birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
