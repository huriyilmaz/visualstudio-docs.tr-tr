---
description: Bu program için bir GUID alır.
title: 'IDebugProgram2:: GetProgramId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45721d4214c396f3366bd23c2bc48e74a1427ec8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168969"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Bu program için bir GUID alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Parametreler
`pguidProgramId`\
dışı `GUID` Bu program için döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir hata ayıklama altyapısı (DE), ilk olarak [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) veya [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemlerine geçirilen program tanımlayıcısını döndürmelidir. Bu, programın hata ayıklayıcı bileşenleri arasında tanımlanmasını sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
