---
title: Tür Görselleştiricileri ve Özel Görüntüleyiciler | Microsoft Docs
description: Kullanıcının verileri sayı dökümünden daha anlamlı bir şekilde görüntülemesine izin vermenizi sağlarken tür görselleştiricileri ve özel görüntüleyicileri uygulama hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b42afdc165540360d8d8c1c458e1c044dbcbcddd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138763"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Tür görselleştiricileri ve özel görüntüleyicileri uygulama
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Tür görselleştiricileri ve özel görüntüleyiciler, bir kullanıcının belirli bir türe göre verileri sayıların onaltılık dökümden daha anlamlı bir şekilde görüntülemesine izin verir. Bir ifade değerlendirici (EE) özel görüntüleyicileri belirli veri veya değişken türleriyle ilişkilendirilebilirsiniz. Bu özel görüntüleyiciler, EE. Bu EE, başka bir üçüncü taraf satıcıdan, hatta son kullanıcıdan gelen dış tür görselleştiricileri de destekleyene bir uygulamadır.

## <a name="discussion"></a>Tartışma

### <a name="type-visualizers"></a>Tür görselleştiricileri
 Visual Studio, her nesnenin bir izleme penceresinde görüntülenebilir olması için tür görselleştiricilerinin ve özel görüntüleyicilerin listesini sorar. İfade değerlendiricisi (EE), tür görselleştiricileri ve özel görüntüleyicileri desteklemek istediği her tür için böyle bir liste sağlar. [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) çağrıları, tür görselleştiricilerine ve özel [](../../extensibility/debugger/visualizing-and-viewing-data.md) görüntüleyicilere erişme işleminin tamamını başlatıyor (arama dizisiyle ilgili ayrıntılar için bkz. Verileri Görselleştirme ve Görüntüleme).

### <a name="custom-viewers"></a>Özel görüntüleyiciler
 Özel görüntüleyiciler, belirli bir EE türü için özel görüntüleyiciler uygulamalı olarak uygulanır ve [IDebugCustomViewer arabirimiyle](../../extensibility/debugger/reference/idebugcustomviewer.md) temsil ediliyor. Özel görüntüleyici bir tür görselleştirici kadar esnek değildir çünkü yalnızca ilgili özel görüntüleyiciyi uygulayan EE yürüttükleri zaman kullanılabilir. Özel görüntüleyici uygulamak, tür görselleştiriciler için destek uygulamaya göre daha basittir. Ancak, tür görselleştiricilerini desteklemek, son kullanıcıya verilerini görselleştirme konusunda maksimum esneklik sağlar. Bu tartışmanın geri kalan kısmında yalnızca tür görselleştiricileri ile ilgili bir konu vardır.

## <a name="interfaces"></a>Arabirimler
 Aşağıdaki EE, tür görselleştiricileri desteklemek için aşağıdaki arabirimleri Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  Aşağıdaki EE, tür görselleştiricilerini desteklemek için aşağıdaki arabirimleri tüketir:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Verileri görselleştirme ve görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
