---
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f1149e9522803a199034395697e5c88bd988840
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842204"
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
