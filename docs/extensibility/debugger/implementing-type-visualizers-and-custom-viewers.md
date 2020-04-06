---
title: Tür Görüntüleyiciler ve Özel Görüntüleyenler Uygulama | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738498"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Tür görselleştiricilerini ve özel görüntüleyicileri uygulama
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Yazı görüntüleyiciler ve özel görüntüleyiciler, bir kullanıcının belirli bir türdeki verileri basit bir altıdedecimal sayı dökümünden daha anlamlı bir şekilde görüntülemesine izin verin. Bir ifade değerlendiricisi (EE), özel görüntüleyenleri belirli veri türleri veya değişkenlerle ilişkilendirebilir. Bu özel görüntüleyenler EE tarafından uygulanır. EE, başka bir üçüncü taraf satıcıdan ve hatta son kullanıcıdan gelebilecek harici tür görselleştiricilerini de destekleyebilir.

## <a name="discussion"></a>Tartışma

### <a name="type-visualizers"></a>Yazı görselleştiricileri
 Visual Studio, saat penceresinde görüntülenecek her nesne için tür görüntüleyicilerin ve özel görüntüleyenlerin listesini ister. Bir ifade değerlendiricisi (EE), tür görselleştiricilerini ve özel görüntüleyicileri desteklemek istediği her tür için böyle bir liste sağlar. [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) çağrıları tür görselleştiricilerine ve özel görüntüleyenlere erişme işlemini başlatın (arama sırası yla ilgili ayrıntılar için [Verileri Görselleştirme ve Görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md) bölümüne bakın).

### <a name="custom-viewers"></a>Özel görüntüleyenler
 Özel görüntüleyenler belirli bir veri türü için EE'de uygulanır ve [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) arabirimi tarafından temsil edilir. Özel görüntüleyici, yalnızca belirli özel görüntüleyiciyi uygulayan EE yürütüldüğünde kullanılabilir olduğundan, bir tür görselleştiricisi kadar esnek değildir. Özel görüntüleyici uygulamak, tür görüntüleyiciler için destek uygulamaktan daha kolaydır. Ancak, destekleyici tür görüntüleyiciler verilerini görselleştirmek için son kullanıcıya maksimum esneklik sağlar. Bu tartışmanın geri kalanı yalnızca yazı görselleştiricileri ile ilgilidir.

## <a name="interfaces"></a>Arabirimler
 EE, Visual Studio tarafından tüketilecek tip görselleştiricilerini desteklemek için aşağıdaki arabirimleri uygular:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE, tür görselleştiricilerini desteklemek için aşağıdaki arabirimleri tüketir:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Verileri görselleştirme ve görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
