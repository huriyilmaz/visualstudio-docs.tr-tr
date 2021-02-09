---
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
ms.openlocfilehash: 7723333547e0aeac7fe7a73c0dc40b36f4b6e071
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890038"
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
