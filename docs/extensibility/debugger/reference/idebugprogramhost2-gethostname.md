---
title: IDebugProgramHost2::GetHostName | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722225"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Bu programın barındırma işleminin başlığını, dostu adını veya dosya adını alır.

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
[içinde] [numaralandırma GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) bir değer.

`pbstrHostName`\
[çıkış] Barındırma işleminin istenen adını verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin tipik bir `dwType` uygulamasında, parametre yoksayılır ve ana makinenin dostu bir adı döndürülür. Başka bir olası uygulama `dwType` adını almak için [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) yöntemine bir çağrı için parametre geçmektir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
