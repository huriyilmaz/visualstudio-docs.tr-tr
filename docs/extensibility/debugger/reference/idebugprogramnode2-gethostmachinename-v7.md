---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8c328c83ebe52f842b1990debe07aed3fd764c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722091"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Kaldırıl -mış. KULLANMAYıN.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Parametreler

`pbstrHostMachineName`\
[çıkış] Programın çalıştırıldığı makinenin adını verir.

## <a name="return-value"></a>Dönüş Değeri

Bir uygulama her `E_NOTIMPL`zaman dönmelidir.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> Visual Studio 2005 itibariyle, bu yöntem artık kullanılmaz ve her zaman geri dönmelidir. `E_NOTIMPL`

## <a name="see-also"></a>Ayrıca bkz.

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
