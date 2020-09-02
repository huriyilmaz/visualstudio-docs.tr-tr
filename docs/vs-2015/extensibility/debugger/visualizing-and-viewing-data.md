---
title: Verileri görselleştirme ve görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 719a2b3d073d90ff3977496c7f98ebecb1ab48a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696307"
---
# <a name="visualizing-and-viewing-data"></a>Verileri Görselleştirme ve Görüntüleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Görselleştiriciler ve özel görüntüleyiciler, verileri bir geliştiriciye hızlı bir şekilde anlamlı olacak şekilde sunar. İfade değerlendirici (EE), üçüncü taraf tür görselleştiricilerini destekleyebilir ve kendi özel görüntüleyicilerini sağlayabilir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)][GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) metodunu çağırarak, nesne türü için kaç tür Görselleştiriciler ve özel görüntüleyicilerin ilişkilendirildiğini belirler. En az bir tür görselleştiricisi veya özel Görüntüleyici varsa, Visual Studio bu Görselleştirici ve görüntüleyicilerin bir listesini (aslında Görselleştiriciler ve görüntüleyiciler uygulayan bir listesi) almak için [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemini çağırır `CLSID` ve bunları kullanıcıya sunar.  
  
## <a name="supporting-type-visualizers"></a>Destekleyici tür Görselleştiriciler  
 Tür görselleştiricilerini desteklemek için EE 'ın uygulaması gereken birçok arabirim vardır. Bu arabirimler iki geniş kategoride ayrılabilir: tür görselleştiricileri ve özellik verilerine erişen bunları listeler.  
  
### <a name="listing-type-visualizers"></a>Tür Görselleştiriciler listeleme  
 EE, ve uygulamalarında tür görselleştiricilerini listelemeyi destekler `IDebugProperty3::GetCustomViewerCount` `IDebugProperty3::GetCustomViewerList` . Bu yöntemler çağrıyı, [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)öğesine karşılık gelen yöntemlere iletir.  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) , [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)çağırarak elde edilir. Bu yöntem, [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)öğesine geçirilen [ıdebugciltçi](../../extensibility/debugger/reference/idebugbinder.md) arabiriminden elde edilen [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) arabirimini gerektirir. `IEEVisualizerServiceProvider::CreateVisualizerService` Ayrıca, öğesine geçirilen [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) ve [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) arabirimlerini gerektirir `IDebugParsedExpression::EvaluateSync` . Arabirimi oluşturmak için gereken son arabirim, `IEEVisualizerService` Ee 'ın uyguladığı [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) arabirimidir. Bu arabirim, görselleştirilen özellikte değişiklik yapılmasına izin verir. Tüm özellik verileri bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) arabiriminde kapsüllenir ve bu da ee tarafından da uygulanır.  
  
### <a name="accessing-property-data"></a>Özellik verilerine erişme  
 Özellik verilerine erişim, [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimi aracılığıyla yapılır. Bu arabirimi almak için, Visual Studio, [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimini ( [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) arabirimini uygulayan aynı nesneye uygulanan) almak için özellik nesnesinde [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 'i çağırır ve sonra arabirimi almak için [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metodunu çağırır `IPropertyProxyEESide` .  
  
 Arabirim içine ve dışına geçilen tüm veriler, `IPropertyProxyEESide` [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) arabiriminde kapsüllenir. Bu arabirim bir bayt dizisini temsil eder ve hem Visual Studio hem de EE tarafından uygulanır. Özelliğin verileri değiştirilebiliyorsa, Visual Studio yeni verileri tutan bir nesne oluşturur ve buna karşılık olarak, `IEEDataStorage` özelliğin verilerini güncelleştirmek Için InPlaceUpdateObject ' e geçirilmiş yeni bir nesne almak için bu veri nesnesiyle birlikte [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) ' i çağırır `IEEDataStorage` . [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) `IPropertyProxyEESide::CreateReplacementObject` EE 'ın arabirimi uygulayan kendi sınıfını örneketmesine izin verir `IEEDataStorage` .  
  
## <a name="supporting-custom-viewers"></a>Özel görüntüleyiciler destekleme  
 Bayrak, `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` `dwAttrib` nesnenin kendisiyle ilişkili özel bir görüntüleyiciye sahip olduğunu göstermek için [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) yapısı alanında ayarlanır [(GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)çağrısı tarafından döndürülen). Bu bayrak ayarlandığında, Visual Studio [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) arabirimini [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)kullanarak [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabiriminden edinir.  
  
 Kullanıcı özel bir Görüntüleyici seçerse, Visual Studio, yöntemi tarafından sağlanan Görüntüleyici 'yi kullanarak özel Görüntüleyici 'yi başlatır `CLSID` `IDebugProperty3::GetCustomViewerList` . Ardından, Visual Studio, değeri kullanıcıya göstermek için [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) öğesini çağırır.  
  
 Normalde, `IDebugCustomViewer::DisplayValue` verilerin salt okunurdur görünümünü gösterir. Veride değişikliklere izin vermek için, EE bir özellik nesnesi üzerinde veri değiştirmeyi destekleyen bir özel arabirim uygulamalıdır. `IDebugCustomViewer::DisplayValue`Yöntemi, verilerin değiştirilmesini desteklemek için bu özel arabirimi kullanır. Yöntemi, `IDebugProperty2` bağımsız değişken olarak geçirilen arabirimde özel arabirimi arar `pDebugProperty` .  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Her Iki tür Görselleştiriciler ve özel görüntüleyiciler destekleme  
 Bir EE, [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemlerinde hem tür Görselleştiriciler hem de özel görüntüleyiciler destekleyebilir. İlk olarak, EE, bulduğu özel görüntüleyenlerin sayısını [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) yönteminin döndürdüğü değere ekler. İkincisi, EE `CLSID` kendi özel görüntüleyicilerinin s öğesini [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemi tarafından döndürülen listeye ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)   
 [Tür Görselleştiricisi ve Özel Görüntüleyici](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
