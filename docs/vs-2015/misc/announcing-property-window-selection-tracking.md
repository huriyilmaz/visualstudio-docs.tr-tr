---
title: Özellik penceresi seçim Izleme duyurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002447"
---
# <a name="announcing-property-window-selection-tracking"></a>Özellik penceresi seçim Izleme duyurusu
**Özellikler** penceresi veya **özellik** sayfaları ile çalışmak istiyorsanız (örneğin, özelliklerini görmek istediğiniz bir form, metin veya seçim), seçimi nasıl koordine ettiğiniz hakkında bilgi sahibi olmanız gerekir. Örneğin, tek seçim mi yoksa birden çok seçim mi olduğunu bilmeniz gerekir. Ardından, arabirimini kullanarak seçim türünü (tek veya birden çok) IDE 'ye duyurmak gerekir <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> . Bu arabirim **Özellikler** penceresi için gereken bilgileri sağlar.  
  
### <a name="to-announce-selection-to-the-environment"></a>Seçimi ortama duyurmak için  
  
1. `QueryInterface`İçin çağrısı <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. Bunu yapmak için, oluşturulduğunda görünüme geçirilen site işaretçisini kullanın.  
  
    2. `QueryService`Hizmetin görünümünden çağrı yapın `SID_STrackSelection` .  
  
         Bu, için bir işaretçi döndürür <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>Seçiminize her değişiklik yaptığınızda yöntemi çağırın ve öğesini uygulayan bir nesneye bir işaretçi geçirin <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     Seçim kapsayıcısı nesnesi, tek veya birden çok seçim kullanabilir ve bir nesnedeki seçim bilgilerini içerir `IDispatch` . Yöntemi çağırmak, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> seçimin değiştiğini **Özellikler** penceresine bildirir. Daha sonra **Özellikler** penceresi, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> tek veya birden çok seçimlerin oluşup oluşmadığını ve gerçek nesne seçimlerinin ne olduğunu belirlemek için üzerinde nesneleri kullanır.  
  
     Birden çok seçim belirtirseniz, **Özellikler** penceresi nesneler için ortak özellikler arasındaki kesişimini bulur. Tek bir nesne seçimi belirtirseniz, **Özellikler** penceresi bir nesne için tüm özellikleri görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri genişletme](../extensibility/internals/extending-properties.md)   
 [Özellik Sayfaları](../extensibility/internals/property-pages.md)