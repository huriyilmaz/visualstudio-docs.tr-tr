---
description: Bu olayı neden olan özel durumun ayrıntılı açıklamasını alır.
title: IDebugExceptionEvent2::GetException | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b181e91bf06538b09a12a394404926e30e00ca91
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725806"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Bu olayı neden olan özel durumun ayrıntılı açıklamasını alır.

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
[in, out] Özel [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) açıklamasıyla doldurulan bir özel durum yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar

 [yalnızca C++ ] Çağıran, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) [nesnesinin EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) serbest bırakmanın yanı sıra bu yapıda yer alan dizeleri serbest bırakmakla sorumludur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
