---
description: Bu programın barındırma işleminin başlığını, kolay adını veya dosya adını alır.
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b43d6c3edde39b137116dc5215745f066207e25d00c75e8a1dc351e8c1ccefc6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433222"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Bu programın barındırma işleminin başlığını, kolay adını veya dosya adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Parametreler
`dwType`\
[in] Bir değer [GETHOSTNAME_TYPE.](../../../extensibility/debugger/reference/gethostname-type.md)

`pbstrHostName`\
[out] Barındırma işleminin istenen adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin tipik bir uygulamasında parametresi `dwType` yoksayılır ve konak makinenin kolay adı döndürülür. Başka bir olası uygulama, adı `dwType` almak için [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) yöntemine bir çağrıya parametresini geçmektir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
