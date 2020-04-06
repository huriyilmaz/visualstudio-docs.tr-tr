---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82f3214783a35e668bf3164c8659f60f863e9a43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720671"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Özel hata ayıklama altyapısı (DE) arabirimi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parametreler
`ppUnk`\
[çıkış] Debug `IUnknown` engine (DE) temsil eden ve de ile ilişkili diğer geçerli arabirim için sorgulanabilen bir nesneyi döndürür (örneğin [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) veya [IDebugEngineLaunch2).](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemden alınan arabirimler aracılığıyla arama yapılması oturum hata ayıklama yöneticisinin işlemini atlatdığından ve Hata ayıklama sırasında SDM'nin kötü bir duruma girmesine veya hata oluşturmasına neden olabileceğinden, ortaya çıkan arabirim dikkatli kullanılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
