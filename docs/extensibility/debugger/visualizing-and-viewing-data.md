---
title: Verileri Görselleştirme ve Görüntüleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712370"
---
# <a name="visualizing-and-viewing-data"></a>Verileri görselleştirme ve görüntüleme
Görselleştiriciler yazın ve özel görüntüleyenler verileri bir geliştirici için hızlı bir şekilde anlamlı bir şekilde sunar. İfade değerlendiricisi (EE), üçüncü taraf tür görselleştiricilerini desteklemenin yanı sıra kendi özel görüntüleyicileri de sağlayabilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)][GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) yöntemini arayarak nesnenin türüyle kaç tür görselleştiricinin ve özel görüntüleyenin ilişkili olduğunu belirler. En az bir tür görselleştirici veya özel görüntüleyici varsa, Visual Studio bu görüntüleyiciler ve görüntüleyenlerin bir listesini almak için [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemini çağırır (aslında, görüntüleyiciler ve görüntüleyenler uygulayan s listesi) ve bunları kullanıcıya sunar.

## <a name="supporting-type-visualizers"></a>Destekleyici tip görselleştiriciler
 EE'nin tür görselleştiricilerini desteklemek için uygulaması gereken bir dizi arabirim vardır. Bu arabirimler iki geniş kategoriye ayrılabilir: özellik verilerine erişen tür görselleştiricilerini ve arabirimleri listeleyen arabirimler.

### <a name="listing-type-visualizers"></a>Listeleme türü görselleştiricileri
 EE, uygulanmasında tip görüntüleyicilerin listelenmesi ve `IDebugProperty3::GetCustomViewerCount` `IDebugProperty3::GetCustomViewerList`. Bu yöntemler ilgili yöntemler [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)için arama geçmek.

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)arayarak elde edilir. Bu yöntem, [EvaluateSync'e](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)geçirilen IDebugBinder arabiriminden elde edilen [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) arabirimini gerektirir. [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) `IEEVisualizerServiceProvider::CreateVisualizerService`ayrıca [iDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) ve [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) arabirimleri, hangi `IDebugParsedExpression::EvaluateSync`geçirildi gerektirir. `IEEVisualizerService` Arabirimi oluşturmak için gereken son arayüz, [EE'nin uyguladığı IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimidir. Bu arabirim, görüntülenen özellikte değişiklikler yapılmasını sağlar. Tüm özellik verileri, EE tarafından da uygulanan bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) arabiriminde kapsüllenir.

### <a name="accessing-property-data"></a>Özellik verilerine erişim
 Özellik verilerine erişim [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimi üzerinden yapılır. Bu arabirimi elde etmek için Visual Studio, [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini almak için özellik nesnesi üzerinde [QueryInterface'i](/cpp/atl/queryinterface) arar [(IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) `IPropertyProxyEESide` arabirimini uygulayan aynı nesne üzerinde uygulanır) ve ardından arabirimi elde etmek için [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) yöntemini arar.

 `IPropertyProxyEESide` Arayüze giren ve çıkan tüm veriler [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) arabiriminde saklanır. Bu arabirim bir dizi baytı temsil eder ve hem Visual Studio hem de EE tarafından uygulanır. Bir özelliğin verileri değiştirilecek olduğunda, Visual Studio `IEEDataStorage` yeni verileri tutan bir nesne oluşturur ve özelliğin verilerini `IEEDataStorage` güncelleştirmek için [InPlaceUpdateObject'e](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) geçirilen yeni bir nesne elde etmek için bu veri nesnesiyle [CreateReplacement Object'i](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) çağırır. `IPropertyProxyEESide::CreateReplacementObject`EE'nin arabirimi uygulayan kendi sınıfını anlık `IEEDataStorage` olarak gerçekleştirmesini sağlar.

## <a name="supporting-custom-viewers"></a>Özel görüntüleyenleri destekleme
 Bayrak, `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` nesnenin `dwAttrib` onunla ilişkili özel bir görüntüleyicisi olduğunu belirtmek için [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) yapısının alanında [(GetPropertyInfo'ya](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)yapılan bir çağrıyla döndürülür) ayarlanır. Bu bayrak ayarlandığında, Visual Studio [QueryInterface](/cpp/atl/queryinterface)kullanarak [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty3.md) arabiriminden [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty2.md) arabirimini alır.

 Kullanıcı özel bir görüntüleyici seçerse, Visual Studio `CLSID` `IDebugProperty3::GetCustomViewerList` özel görüntüleyiciyi yöntemle sağlanan görüntüleyiciyi kullanarak anında kullanır. Visual Studio daha sonra kullanıcıya değeri göstermek için [DisplayValue'ı](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) çağırır.

 Normalde, `IDebugCustomViewer::DisplayValue` verilerin salt okunur görünümünü sunar. Verilerde değişikliklere izin vermek için, EE'nin bir özellik nesnesindeki verileri değiştirmeyi destekleyen özel bir arabirim uygulaması gerekir. Yöntem, `IDebugCustomViewer::DisplayValue` verileri değiştirmeyi desteklemek için bu özel arabirimi kullanır. Yöntem, `pDebugProperty` bağımsız değişken olarak `IDebugProperty2` geçirilen arabirimdeki özel arabirimi arar.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Hem tür görselleştiricilerini hem de özel görüntüleyenleri destekleme
 EE, [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemlerinde hem tür görüntüleyicileri hem de özel görüntüleyenleri destekleyebilir. İlk olarak, [EE, GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) yöntemi yle döndürülen değere sağladığı özel görüntüleyenlerin sayısını ekler. İkinci olarak, EE, `CLSID` [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemi yle döndürülen listeye kendi özel görüntüleyenlerinin s'lerini ekler.

## <a name="see-also"></a>Ayrıca bkz.
- [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md)
- [Görselleştirici ve özel görüntüleyici yazın](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
