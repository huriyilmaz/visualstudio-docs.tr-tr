---
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ed8327690c42f54a33209b2f0acfa45a138ec51c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155089"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem bir Görselleştirici hizmeti oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `binder`  
 'ndaki [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)öğesine geçirilen [ıdebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi.  
  
 `pSymProv`  
 'ndaki [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi geçirildi `IDebugParsedExpression::EvaluateSync` .  
  
 `pAddress`  
 'ndaki [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi geçirildi `IDebugParsedExression::EvaluateSync` .  
  
 `dataProvider`  
 'ndaki [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimini uygulayan bir nesne (ifade değerlendiricisi tarafından sağlanır).  
  
 `ppService`  
 dışı Oluşturulan hizmet.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 `binder`, `pSymProv` Ve `pAddress` parametrelerinin hepsi `IDebugParsedExpression::EvaluateSync` yönteme geçildi. `CreateVisualizerService` , yalnızca `IDebugParsedExpression::EvaluateSync` tür Görselleştiriciler için bir ifade değerlendirici desteğinin bir parçası olarak çağrılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
