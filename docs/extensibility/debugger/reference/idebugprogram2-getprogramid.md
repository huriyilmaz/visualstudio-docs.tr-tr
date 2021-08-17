---
description: Bu program için bir GUID alır.
title: IDebugProgram2::GetProgramId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: affe65f21cc9e9899349c87e237b49b1051210fc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030106"
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
[out] Bu program `GUID` için döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısının (DE), başlangıçta [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) veya Attach yöntemlerine geçirilen program [tanımlayıcısını geri](../../../extensibility/debugger/reference/idebugengine2-attach.md) getirebilirsiniz. Bu, hata ayıklayıcı bileşenleri arasında programın tanımlanmasına olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
