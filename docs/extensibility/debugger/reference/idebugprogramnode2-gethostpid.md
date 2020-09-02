---
title: 'IDebugProgramNode2:: GetHostPid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostPid
helpviewer_keywords:
- IDebugProgramNode2::GetHostPid
ms.assetid: e65b4b15-46d8-4ca7-9456-2b4c078f7cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1257bda23bcdfaceb58d1d087ae2848be8f969b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722029"
---
# <a name="idebugprogramnode2gethostpid"></a>IDebugProgramNode2::GetHostPid
Programı barındıran işlem için sistem işlem tanımlayıcısını alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetHostPid ( 
   AD_PROCESS_ID * pdwHostPid
);
```

```csharp
int GetHostPid ( 
   out AD_PROCESS_ID pdwHostPid
);
```

## <a name="parameters"></a>Parametreler
`pdwHostPid`\
dışı Barındırma işlemi için sistem işlem tanımlayıcısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `CProgram` [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CProgram::GetHostPid(AD_PROCESS_ID* pdwHostPid) {
   // Check for valid argument.
   if (pdwHostPid == NULL)
     return E_INVALIDARG;

   // Get the process identifier of the calling process.
   pdwHostPid->ProcessIdType = AD_PROCESS_ID_SYSTEM;
   pdwHostPid->ProcessId.dwProcessId = GetCurrentProcessId();
   return S_OK;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
