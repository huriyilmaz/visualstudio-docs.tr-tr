---
description: Sistem iş parçacığı tanımlayıcısını alır.
title: 'IDebugThread2:: GetThreadId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e8ac54a27ca799f263e156d79bee057fcb90c3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153101"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Sistem iş parçacığı tanımlayıcısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>Parametreler
`pdwThreadId`\
dışı Sistem iş parçacığı tanımlayıcısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
İş parçacığı KIMLIĞI, bir işlemdeki diğer tüm iş parçacıkları arasında iş parçacığı tanımlamak için kullanılır.

## <a name="example"></a>Örnek
Aşağıdaki örnek, `CProgram` [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
