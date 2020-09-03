---
title: 'Nasıl yapılır: standart metin Işaretçileri ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780707"
---
# <a name="how-to-add-standard-text-markers"></a>Nasıl Yapılır: Standart Metin İşaretçileri Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çekirdek düzenleyiciyle birlikte sunulan varsayılan metin işaretçisi türlerinden birini oluşturmak için aşağıdaki yordamı kullanın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="to-create-a-text-marker"></a>Metin işaretçisi oluşturmak için  
  
1. Bir veya iki boyutlu koordinat sistemi kullanıp kullandığınıza bağlı olarak, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> Yeni bir metin işaretleyicisi oluşturmak için yöntemini veya yöntemini çağırın.  
  
     Bu yöntem çağrısında bir işaret türü, işaretçiyi üzerinde işaret oluşturmak için bir metin aralığı ve bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> arabirim belirtin. Bu yöntem daha sonra yeni oluşturulan metin işaretleyicisine bir işaretçi döndürür. İşaret türleri <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> numaralandırmasından alınır. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>İşaret olaylarının bilgilendirilmek istiyorsanız bir arabirim belirtin.  
  
    > [!NOTE]
    > Yalnızca ana kullanıcı arabirimi iş parçacığında metin işaretleyicileri oluşturun. Çekirdek Düzenleyici, metin işaretçilerinin oluşturulması için metin arabelleğinin içeriğine bağımlıdır ve metin arabelleği iş parçacığı güvenli değildir.  
  
## <a name="adding-a-custom-command"></a>Özel komut ekleme  
 Arabirimi uygulamak `IVsTextMarkerClient` ve işaretçiden buna bir işaretçi sağlamak, işaret davranışını birkaç şekilde geliştirir. İlk olarak, bu, markmeniz ve komutları yürütmek için ipuçları sağlamanıza olanak tanır. Bu Ayrıca, ayrı işaretçiler için olay bildirimleri almanızı ve işaret üzerinde özel bağlam menüsü oluşturmayı sağlar. İşaretleyici bağlam menüsüne özel bir komut eklemek için aşağıdaki yordamı kullanın.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Bağlam menüsüne özel bir komut eklemek için  
  
1. Bağlam menüsü görüntülenmeden önce, ortam <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> yöntemini çağırır ve etkilenen metin işaretçisi için bir işaretçi ve bağlam menüsündeki komut öğesi numarasını geçirir.  
  
     Örneğin, bağlam menüsündeki kesme noktasına özgü komutlar, aşağıdaki ekran görüntüsünde gösterildiği gibi **Yeni kesme**noktası aracılığıyla **kesme noktasını kaldır** ' ı içerir.  
  
     ![İşaret bağlam menüsü](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. Özel komutun adını belirten bir metin geri geçirin. Örneğin, ortam zaten sağlamıyorsa, **kesme noktasını kaldır** özel bir komut olabilir. Ayrıca komutun desteklenip desteklenmediğini, kullanılabildiğini ve etkin olduğunu ve/veya bir açık geçiş seçeneğini de geri geçirirsiniz. Ortam bu bilgileri, bağlam menüsündeki özel komutu doğru şekilde göstermek için kullanır.  
  
3. Komutu yürütmek için, ortam <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> yöntemini çağırarak metin işaretine bir işaretçi ve bağlam menüsünden seçilen komutun numarasını geçer.  
  
     Bu çağrıdan özel komutunuz metin işaretçisinin herhangi bir eylemini yürütmek için bu çağrıdan bu bilgileri kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API ile metin Işaretleyicileri kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Nasıl yapılır: hata Işaretleyicileri uygulama](../extensibility/how-to-implement-error-markers.md)   
 [Nasıl yapılır: özel metin Işaretçileri oluşturma](../extensibility/how-to-create-custom-text-markers.md)   
 [Nasıl Yapılır: Metin İşaretçileri Kullanma](../extensibility/how-to-use-text-markers.md)
