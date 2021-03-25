---
description: Bu programın barındırma sürecinin başlığını, kolay adını veya dosya adını alır.
title: 'IDebugProgramHost2:: GetHostName | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53b4d69be1ea24f5c240b6247539f499c9fb00fb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084018"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Bu programın barındırma sürecinin başlığını, kolay adını veya dosya adını alır.

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
'ndaki [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) numaralandırmasından bir değer.

`pbstrHostName`\
dışı Barındırma işleminin istenen adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin tipik bir uygulamasında `dwType` parametresi yok sayılır ve konak makinenin kolay adı döndürülür. Başka bir olası uygulama, `dwType` adı almak için, parametreyi [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) yöntemine yapılan çağrıya geçirmektir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
