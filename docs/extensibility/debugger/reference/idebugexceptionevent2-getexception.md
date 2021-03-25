---
description: Bu olayı tetikleyen özel durumun ayrıntılı bir açıklamasını alır.
title: 'IDebugExceptionEvent2:: GetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72457b1b8931d028f555e7f9354f34b133fa79bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084785"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Bu olayı tetikleyen özel durumun ayrıntılı bir açıklamasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>Parametreler
`pExceptionInfo`\
[in, out] Özel durumun açıklamasıyla doldurulmuş bir [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

 [Yalnızca C++] Çağıran, [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısındaki dizeleri boşaltmaktan ve [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesinin yapıda serbest bırakılmasından sorumludur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
