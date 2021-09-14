---
title: Veri Verilerini Görselleştirme ve Görüntüleme | Microsoft Docs
description: Tür görselleştiricileri ve özel görüntüleyicilerin bir geliştiriciye nasıl veri sun olduğunu öğrenin. İfade değerlendiricisi üçüncü taraf tür görselleştiricileri destekler.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626325"
---
# <a name="visualizing-and-viewing-data"></a>Verileri görselleştirme ve görüntüleme
Tür görselleştiricileri ve özel görüntüleyiciler, verileri bir geliştirici için hızlı bir şekilde anlamlı bir şekilde sağlar. İfade değerlendiricisi (EE), üçüncü taraf tür görselleştiricileri destekleyenin yanı sıra kendi özel görüntüleyicilerini de temin ediyor olabilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)][GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) yöntemini çağırarak nesne türüyle kaç tür görselleştiricisi ve özel görüntüleyicinin ilişkilendirileceklerini belirler. Kullanılabilir en az bir tür görselleştirici veya özel görüntüleyici varsa Visual Studio, bu görselleştiricilerin ve görüntüleyicilerin (aslında görselleştiricileri ve görüntüleyicileri uygulayanların listesi) listesini almak için [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemini çağırarak bunları kullanıcıya sunar.

## <a name="supporting-type-visualizers"></a>Tür görselleştiricileri destekleme
 Türü görselleştiricileri desteklemek için EE gereken bir dizi arabirim vardır. Bu arabirimler iki geniş kategoriye ayrılır: tür görselleştiricilerini ve özellik verilerine erişen arabirimleri listeleye arabirimler.

### <a name="listing-type-visualizers"></a>Listeleme türü görselleştiricileri
 Bu EE, ve uygulamasında tür görselleştiricilerinin listelenemini `IDebugProperty3::GetCustomViewerCount` `IDebugProperty3::GetCustomViewerList` destekler. Bu yöntemler çağrıyı ilgili [GetCustomViewerCount ve GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) [yöntemlerine iletir.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

 [IEEVisualizerService,](../../extensibility/debugger/reference/ieevisualizerservice.md) [CreateVisualizerService çağrılarak elde edilir.](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) Bu yöntem, EvaluateSync'e geçirilen IDebugBinder arabiriminden alınan [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) [arabirimini gerektirir.](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) [](../../extensibility/debugger/reference/idebugbinder.md) `IEEVisualizerServiceProvider::CreateVisualizerService` ayrıca, ['ye geçirilen IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) ve [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) arabirimlerini `IDebugParsedExpression::EvaluateSync` gerektirir. Arabirimi oluşturmak için gereken son `IEEVisualizerService` arabirim, [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimidir ve EE uygulanır. Bu arabirim, görselleştirilen özellikte değişikliklere izin verir. Tüm özellik verileri, uygulama tarafından da uygulanan [bir IDebugObject](../../extensibility/debugger/reference/idebugobject.md) arabiriminde kapsül EE.

### <a name="accessing-property-data"></a>Özellik verilerine erişme
 Özellik verilerine erişim [IPropertyProxyEESide arabirimi aracılığıyla](../../extensibility/debugger/reference/ipropertyproxyeeside.md) yapılır. Bu arabirimi almak için Visual Studio, [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini [(IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) arabirimini uygulayan aynı nesnede uygulanır) almak için özellik nesnesinde [QueryInterface'i](/cpp/atl/queryinterface) ve ardından arabirimi almak için [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) yöntemini `IPropertyProxyEESide` çağırmaktadır.

 Arabirime geçirilen ve arabirimden geçirilen tüm veriler `IPropertyProxyEESide` [IEEDataStorage arabiriminde kapsüller.](../../extensibility/debugger/reference/ieedatastorage.md) Bu arabirim bir bayt dizisini temsil eder ve hem Visual Studio hem de EE. Bir özelliğin verileri değiştirilsin mi, Visual Studio yeni verileri tutan bir nesne oluşturur ve özelliğin verilerini güncelleştirmek için InPlaceUpdateObject'e geçirilen yeni bir nesne elde etmek için bu veri nesnesiyle `IEEDataStorage` [Birlikte CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) `IEEDataStorage` nesnesini çağırmaktadır. [](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) `IPropertyProxyEESide::CreateReplacementObject`uygulamanın EE uygulayan kendi sınıfını örneğini uygulamasına olanak `IEEDataStorage` sağlar.

## <a name="supporting-custom-viewers"></a>Özel görüntüleyicileri destekleme
 bayrağı, nesneyle ilişkilendirilmiş özel bir görüntüleyiciye sahip olduğunu belirtmek için DEBUG_PROPERTY_INFO yapısının `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` `dwAttrib` alanında [(GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)çağrısı tarafından döndürülür) ayarlanır. [](../../extensibility/debugger/reference/debug-property-info.md) Bu bayrak ayarlanırsa, Visual Studio QueryInterface kullanarak [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty3.md) arabiriminden [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty2.md) [arabirimini edinir.](/cpp/atl/queryinterface)

 Kullanıcı bir özel görüntüleyici seçerse, Visual Studio tarafından sağlanan görüntüleyiciyi kullanarak özel `CLSID` görüntüleyicinin örneğini `IDebugProperty3::GetCustomViewerList` oluşturabilir. Visual Studio kullanıcıya [göstermek için DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) çağrısında bulunuyor.

 Normalde verilerin `IDebugCustomViewer::DisplayValue` salt okunur bir görünümünü sunar. Verilerde değişikliklere izin vermek için EE nesnede veri değiştirmeyi destekleyen özel bir arabirim uygulaması gerekir. yöntemi, `IDebugCustomViewer::DisplayValue` verileri değiştirmeyi desteklemek için bu özel arabirimi kullanır. yöntemi, bağımsız değişken olarak geçirilen `IDebugProperty2` arabirimde özel `pDebugProperty` arabirimini aratır.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Hem tür görselleştiricileri hem de özel görüntüleyicileri destekleme
 Bir EE [GetCustomViewerCount ve GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) yöntemlerinde hem tür görselleştiricileri hem de özel [görüntüleyicileri](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) destekleyebilirsiniz. İlk olarak [EE, GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) yöntemi tarafından döndürülen değere sağlamakta olduğu özel görüntüleyici sayısını ekler. İkincisi, EE kendi özel görüntüleyicilerininlerini `CLSID` [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemi tarafından döndürülen listeye ekler.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
- [Tür görselleştiricisi ve özel görüntüleyici](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
