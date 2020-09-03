---
title: Tür Görselleştiriciler ve özel görüntüleyiciler uygulama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738498"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Tür Görselleştiriciler ve özel görüntüleyiciler uygulama
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Tür Görselleştiriciler ve özel görüntüleyiciler, bir kullanıcının belirli bir türdeki verileri, sayıların basit bir onaltılı dökümünden daha anlamlı olacak şekilde görüntülemesine olanak tanır. Bir ifade değerlendirici (EE) özel görüntüleyicilerin belirli veri türleri veya değişkenleri ile ilişkilendirebileceği. Bu özel görüntüleyiciler EE tarafından uygulanır. EE, başka bir üçüncü taraf satıcıdan veya hatta son kullanıcıdan gelmiş olabilecek harici tür görselleştiricileri de destekleyebilir.

## <a name="discussion"></a>Tartışma

### <a name="type-visualizers"></a>Tür Görselleştiriciler
 Visual Studio, bir izleme penceresinde görüntülenmek üzere her nesnenin tür görselleştiricileri ve özel görüntüleyicilerinin bir listesini ister. Bir ifade değerlendirici (EE), tür Görselleştiriciler ve özel görüntüleyiciler desteklemek istediği her tür için böyle bir liste sağlar. [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) çağrıları, tür Görselleştiriciler ve özel görüntüleyicilere erişme sürecini başlatır (çağrı dizisi hakkındaki ayrıntılar Için bkz. [verileri görselleştirme ve görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md) ).

### <a name="custom-viewers"></a>Özel görüntüleyiciler
 Özel görüntüleyiciler, belirli bir veri türü için EE 'de uygulanır ve [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) arabirimi tarafından temsil edilir. Özel bir görüntüleyici, yalnızca söz konusu özel görüntüleyiciyi uygulayan EE 'ın yürütüldüğü için bir tür görselleştiricisi olarak esnek değildir. Özel bir Görüntüleyici uygulamak, tür Görselleştiriciler için destek uygulamaktan daha basittir. Ancak, destekleyici tür Görselleştiriciler, son kullanıcıya verilerini görselleştirmede en yüksek esnekliği sağlar. Bu tartışmanın geri kalanı yalnızca tür Görselleştiriciler ile ilgilidir.

## <a name="interfaces"></a>Arabirimler
 EE, Visual Studio tarafından tüketilen tür görselleştiricilerini desteklemek için aşağıdaki arayüzleri uygular:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE, tür görselleştiricilerini desteklemek için aşağıdaki arabirimleri kullanır:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Verileri görselleştirme ve görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
