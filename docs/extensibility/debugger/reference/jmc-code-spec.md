---
description: Bu yapı, bir modülün JustMyCode bilgilerini ayarlamak için kullanılır.
title: JMC_CODE_SPEC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca44db2c6e6c097cfe26845eb3f60303155257aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042848"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Bu yapı, bir modülün JustMyCode bilgilerini ayarlamak için kullanılır.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>Üyeler
`fIsUserCode`\
Modül kullanıcı kodu olarak kabul edilirse sıfır olmayan ( ), değilse sıfır ( ) ise modül dış kod olarak kabul edilir ve hata `TRUE` `FALSE` ayıklanmaz.

`bstrModuleName`\
Söz konusu modülün adı.

## <a name="remarks"></a>Açıklamalar
Bu yapı, bu tür yapıların listesi olarak [SetJustMyCodeState yöntemine](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
