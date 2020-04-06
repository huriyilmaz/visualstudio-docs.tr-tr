---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717913"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Bu yöntem bir görselleştirici hizmeti oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Parametreler
`binder`\
[içinde] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi [EvaluateSync'e](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)geçti.

`pSymProv`\
[içinde] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi `IDebugParsedExpression::EvaluateSync`' ye geçti.

`pAddress`\
[içinde] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi `IDebugParsedExression::EvaluateSync`' ye geçti.

`dataProvider`\
[içinde] [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimini uygulayan bir nesne (ifade değerlendiricisi tarafından sağlanır).

`ppService`\
[çıkış] Oluşturulan hizmet.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 , `binder` `pSymProv`, `pAddress` ve parametrelerin tümü `IDebugParsedExpression::EvaluateSync` yönteme geçirildi. `CreateVisualizerService`yalnızca bir ifade `IDebugParsedExpression::EvaluateSync` değerlendiricinin tip görselleştiricileri için desteğinin bir parçası olarak çağrılması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
