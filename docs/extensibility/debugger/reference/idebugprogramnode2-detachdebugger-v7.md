---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
description: Bu yöntem, 2005'te kullanılmadan önce kullanılan ayırma yönteminin eski Visual Studio biçimidir.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47ad13cc0f3f01665535e6b9d8168af79eb299f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029989"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Kaldırıl -mış. KULLANMAYIN.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Dönüş Değeri

Bir uygulama her zaman `E_NOTIMPL` dönüşletir.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> 2005 Visual Studio, bu yöntem artık kullanılmaz ve her zaman ifadesinin olması `E_NOTIMPL` gerekir.

Bu yöntem, hata ayıklayıcı beklenmedik şekilde kapanıyor olduğunda çağrılır. Bu yöntem çağrıldı sıra, DE programı kullanıcıdan ayrılmış gibi sürdürebilir. Başka hata ayıklama olayları gönderilmez. Program, hata ayıklayıcının başka bir örneğinden eklenebilir durumda olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
