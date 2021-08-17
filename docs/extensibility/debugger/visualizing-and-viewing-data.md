---
title: Verileri görselleştirme ve görüntüleme | Microsoft Docs
description: Tür Görselleştiriciler ve özel görüntüleyiciler bir geliştiriciye veri sunma hakkında bilgi edinin. İfade değerlendirici, üçüncü taraf tür görselleştiricilerini destekler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bd0fa59cec59e27949bf9d8d209bc66221d3505d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095120"
---
# <a name="visualizing-and-viewing-data"></a>Verileri görselleştirme ve görüntüleme
Görselleştiriciler ve özel görüntüleyiciler, verileri bir geliştiriciye hızlı bir şekilde anlamlı olacak şekilde sunar. ifade değerlendirici (EE), üçüncü taraf tür görselleştiricilerini destekleyebilir ve kendi özel görüntüleyicilerini sağlayabilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)][GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) metodunu çağırarak, nesne türü için kaç tür Görselleştiriciler ve özel görüntüleyicilerin ilişkilendirildiğini belirler. en az bir tür görselleştiricisi veya özel görüntüleyici varsa Visual Studio, bu görselleştiricilerin ve görüntüleyicilerin bir listesini almak için [getcustomviewerlist](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemini çağırır (aslında görselleştiriciler ve görüntüleyiciler uygulayan bir listesi) ve bunları kullanıcıya gösterir.

## <a name="supporting-type-visualizers"></a>Destekleyici tür Görselleştiriciler
 tür görselleştiricileri desteklemek için EE uygulaması gereken birçok arabirim vardır. Bu arabirimler iki geniş kategoride ayrılabilir: tür Görselleştiriciler ve özellik verilerine erişen arabirimler listeleyin.

### <a name="listing-type-visualizers"></a>Tür Görselleştiriciler listeleme
 EE, ve uygulamalarında tür görselleştiricilerini listelemeyi destekler `IDebugProperty3::GetCustomViewerCount` `IDebugProperty3::GetCustomViewerList` . Bu yöntemler çağrıyı, [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)öğesine karşılık gelen yöntemlere iletir.

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) , [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)çağırarak elde edilir. Bu yöntem, [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)öğesine geçirilen [ıdebugciltçi](../../extensibility/debugger/reference/idebugbinder.md) arabiriminden elde edilen [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) arabirimini gerektirir. `IEEVisualizerServiceProvider::CreateVisualizerService` Ayrıca, öğesine geçirilen [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) ve [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) arabirimlerini gerektirir `IDebugParsedExpression::EvaluateSync` . arabirimi oluşturmak için gereken son arabirim, `IEEVisualizerService` EE uyguladığı [ıeevisualizerdataprovider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimidir. Bu arabirim, görselleştirilen özellikte değişiklik yapılmasına izin verir. Tüm özellik verileri bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) arabiriminde kapsüllenir, bu da ee tarafından da uygulanır.

### <a name="accessing-property-data"></a>Özellik verilerine erişme
 Özellik verilerine erişim, [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimi aracılığıyla yapılır. bu arabirimi elde etmek için Visual Studio, [ıpropertyproxyprovider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini ( [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) arabirimini uygulayan aynı nesneye uygulanan) almak için özellik nesnesinde [queryınterface](/cpp/atl/queryinterface) çağırır ve sonra arabirimi almak için [getpropertyproxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) yöntemini çağırır `IPropertyProxyEESide` .

 Arabirim içine ve dışına geçilen tüm veriler, `IPropertyProxyEESide` [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) arabiriminde kapsüllenir. bu arabirim bir bayt dizisini temsil eder ve hem Visual Studio hem de EE tarafından uygulanır. özelliğin verileri değiştirilebiliyorsa, Visual Studio `IEEDataStorage` yeni verileri tutan bir nesne oluşturur ve bu veri nesnesiyle birlikte [createreplacementobject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) ' i çağırarak `IEEDataStorage` özelliğin verilerini güncelleştirmek için [ınplaceupdateobject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) ' e geçirilir. `IPropertyProxyEESide::CreateReplacementObject`EE, arabirimini uygulayan kendi sınıfını örneketmesine izin verir `IEEDataStorage` .

## <a name="supporting-custom-viewers"></a>Özel görüntüleyiciler destekleme
 Bayrak, `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` `dwAttrib` nesnenin kendisiyle ilişkili özel bir görüntüleyiciye sahip olduğunu göstermek için [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) yapısı alanında ayarlanır [(GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)çağrısı tarafından döndürülen). bu bayrak ayarlandığında Visual Studio, [queryınterface](/cpp/atl/queryinterface)kullanarak [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabiriminden [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) arabirimini edinir.

 kullanıcı özel bir görüntüleyici seçerse, Visual Studio yöntemi tarafından sağlanan görüntüleyiciyi kullanarak özel görüntüleyici 'yi başlatır `CLSID` `IDebugProperty3::GetCustomViewerList` . Visual Studio sonra değeri kullanıcıya göstermek için [displayvalue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) öğesini çağırır.

 Normalde, `IDebugCustomViewer::DisplayValue` verilerin salt okunurdur görünümünü gösterir. verilerde değişikliklere izin vermek için EE, özellik nesnesindeki verileri değiştirmeyi destekleyen bir özel arabirim uygulamalıdır. `IDebugCustomViewer::DisplayValue`Yöntemi, verilerin değiştirilmesini desteklemek için bu özel arabirimi kullanır. Yöntemi, `IDebugProperty2` bağımsız değişken olarak geçirilen arabirimde özel arabirimi arar `pDebugProperty` .

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Her iki tür Görselleştiriciler ve özel görüntüleyiciler destekleme
 EE, [getcustomviewercount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) ve [getcustomviewerlist](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemlerinde hem tür görselleştiriciler hem de özel görüntüleyiciler destekleyebilir. ilk olarak EE, sağladığı özel görüntüleyicilerin sayısını [getcustomviewercount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) yöntemi tarafından döndürülen değere ekler. ikinci olarak EE, `CLSID` kendi özel görüntüleyicilerinin s öğesini [getcustomviewerlist](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemi tarafından döndürülen listeye ekler.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
- [Tür görselleştiricisi ve özel Görüntüleyici](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
