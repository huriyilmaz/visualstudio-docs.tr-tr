---
title: IEEVisualizerServiceProvider | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717892"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim, IDE için tür görselleştirici görevlerini işlemek için kullanılan bir görselleştirici hizmeti oluşturabilen bir yönteme erişim sağlar.

## <a name="syntax"></a>Sözdizimi

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio bu arabirimi, Visual Studio IDE'ye sınıf lı görselleştiriciler`CLSID`(ler) sağlamak için kullanılan bir görselleştirici hizmet nesnesi oluşturmak için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 İfade değerlendiricisi (EE), [geteeservice'i](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) bu arabirimi elde etmek için çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Görselleştirici hizmeti oluşturur|

## <a name="remarks"></a>Açıklamalar
 Arabirim `IEEVisualizerServiceProvider` [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)uygulaması sırasında elde edilir. Bu arabirimin oluşturduğu görselleştirici hizmeti, EE'nin uygulamaktan sorumlu olduğu bir [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimine işlevsellik sağlamak için kullanılır. EE ayrıca, tür görüntüleyicilerin bir özelliğin değerini görüntülemesine ve değiştirmesine olanak tanıyan bir [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimini uygulamaktan da sorumludur.

 Bu arabirimlerin nasıl etkileşimde olduğu yla ilgili ayrıntılar için [Verileri Görselleştirme ve Görüntüleme'ye](../../../extensibility/debugger/visualizing-and-viewing-data.md) bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
