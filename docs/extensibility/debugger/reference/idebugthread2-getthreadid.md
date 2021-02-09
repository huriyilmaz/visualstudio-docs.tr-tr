---
title: 'IDebugThread2:: GetThreadId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e7dfb6714283fa2db1dc2fd8435a91a5c8dc56a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893821"
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
