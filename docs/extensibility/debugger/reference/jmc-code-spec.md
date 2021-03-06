---
description: Bu yapı, bir modül için Adatmycode bilgilerini ayarlamak için kullanılır.
title: JMC_CODE_SPEC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c862a2897b45d89f95963ce7adfe2da8d4d350f
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225571"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Bu yapı, bir modül için Adatmycode bilgilerini ayarlamak için kullanılır.

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
`TRUE`Modül Kullanıcı kodu olarak düşünülse sıfır olmayan (), aksi takdirde, `FALSE` Modül dış kod olarak değerlendirilip ayıklanamayacak kadar sıfır ().

`bstrModuleName`\
Söz konusu modülün adı.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [Setyatmycodestate](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) metoduna bu tür yapıların bir listesi olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
