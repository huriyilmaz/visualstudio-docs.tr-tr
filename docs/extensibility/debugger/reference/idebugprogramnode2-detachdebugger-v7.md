---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722113"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Kaldırıl -mış. KULLANMAYıN.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Dönüş Değeri

Bir uygulama her `E_NOTIMPL`zaman dönmelidir.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> Visual Studio 2005 itibariyle, bu yöntem artık kullanılmaz ve her zaman geri dönmelidir. `E_NOTIMPL`

Hata ayıklama beklenmedik bir şekilde ayrıldığında bu yöntem çağrılır. Bu yöntem çağrıldığında, DE programı kullanıcı ondan ayrılmış gibi devam etmelidir. Başka hata ayıklama olayı gönderilmemelidir. Program hata ayıklama başka bir örnekten takılabilir bir durumda olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
