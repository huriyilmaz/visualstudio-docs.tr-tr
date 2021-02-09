---
title: 'IDebugProgramHost2:: GetHostName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f801b6fd4b030866886f86b8cd01916645c2219c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898788"
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
