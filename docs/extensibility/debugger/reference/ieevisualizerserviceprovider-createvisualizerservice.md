---
description: Bu yöntem bir Görselleştirici hizmeti oluşturur.
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
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
ms.openlocfilehash: 52d44367eaa4d3ea41dbb5fa906a923041d146f8eefaf78bed5d51e49bf1f184
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121291811"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Bu yöntem bir Görselleştirici hizmeti oluşturur.

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
'ndaki [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)öğesine geçirilen [ıdebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi.

`pSymProv`\
'ndaki [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi geçirildi `IDebugParsedExpression::EvaluateSync` .

`pAddress`\
'ndaki [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi geçirildi `IDebugParsedExression::EvaluateSync` .

`dataProvider`\
'ndaki [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimini uygulayan bir nesne (ifade değerlendiricisi tarafından sağlanır).

`ppService`\
dışı Oluşturulan hizmet.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `binder`, `pSymProv` Ve `pAddress` parametrelerinin hepsi `IDebugParsedExpression::EvaluateSync` yönteme geçildi. `CreateVisualizerService` , yalnızca `IDebugParsedExpression::EvaluateSync` tür Görselleştiriciler için bir ifade değerlendirici desteğinin bir parçası olarak çağrılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
