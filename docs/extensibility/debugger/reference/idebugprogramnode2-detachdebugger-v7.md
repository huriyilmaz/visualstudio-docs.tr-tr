---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
description: Bu yöntem, Visual Studio 2005 ' den önce kullanılan ayırma yönteminin eski, Kullanımdan kaldırılmış bir biçimidir.
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16630be49dd884f8bcc82da2fead158eb3a25e5e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053561"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Kullanım dışı. KULLANMAYıN.

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

Bir uygulama her zaman döndürmelidir `E_NOTIMPL` .

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> Visual Studio 2005 itibariyle, bu yöntem artık kullanılmamaktadır ve her zaman döndürmelidir `E_NOTIMPL` .

Bu yöntem, hata ayıklayıcı beklenmedik bir şekilde çıktığında çağrılır. Bu yöntem çağrıldığında, Kullanıcı onu ayırmış olsa da programı sürdürmelidir. Daha fazla hata ayıklama olayı gönderilmemelidir. Program, hata ayıklayıcının başka bir örneğinden iliştirilebileceği bir durumda olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
