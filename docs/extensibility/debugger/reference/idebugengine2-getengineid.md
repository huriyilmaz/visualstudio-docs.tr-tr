---
description: Hata ayıklama altyapısının (DE) GUID 'INI alır.
title: 'IDebugEngine2:: Getengineıd | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 079e3b0316bb06edb383dc74ed0e71f157d29a00
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064337"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Hata ayıklama altyapısının (DE) GUID 'INI alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>Parametreler
`pguidEngine`\
dışı DE öğesinin GUID 'sini döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Tipik GUID 'lerin bazı örnekleri `guidScriptEng` , `guidNativeEng` , veya `guidSQLEng` . Yeni hata ayıklama motorları, tanımlama için kendi GUID değerlerini oluşturacaktır.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CEngine` [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
