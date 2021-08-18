---
description: Bu yöntem bir görselleştirici hizmeti oluşturur.
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fafee34b1ce4a9050a7bf666bce77b1c2b921ec9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070775"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Bu yöntem bir görselleştirici hizmeti oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Parametreler
`binder`\
[in] [EvaluateSync'e geçirilen IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) [nesnesi.](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)

`pSymProv`\
[in] 'a [geçirilen IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) `IDebugParsedExpression::EvaluateSync` nesnesi.

`pAddress`\
[in] 'a [geçirilen IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) `IDebugParsedExression::EvaluateSync` nesnesi.

`dataProvider`\
[in] [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimini uygulayan nesne (ifade değerlendiricisi tarafından sağlanır).

`ppService`\
[out] Oluşturulan hizmet.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `binder`, `pSymProv` ve `pAddress` parametrelerinin hepsi yöntemine `IDebugParsedExpression::EvaluateSync` geçirildi. `CreateVisualizerService` , bir ifade `IDebugParsedExpression::EvaluateSync` değerlendiricinin tür görselleştirici desteğinin bir parçası olarak yalnızca 'den çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
