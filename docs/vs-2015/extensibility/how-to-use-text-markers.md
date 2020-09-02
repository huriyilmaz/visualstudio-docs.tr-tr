---
title: 'Nasıl yapılır: metin Işaretleyicileri kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64800725"
---
# <a name="how-to-use-text-markers"></a>Nasıl Yapılır: Metin İşaretçileri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin işaretçileri, bir nesneyi düzenlemek için uygulanabilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-apply-text-markers"></a>Metin işaretçileri uygulamak için  
  
1. Sınıfının bir örneğini edinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> .  
  
    > [!NOTE]
    > Çekirdek Düzenleyici, düzenleme yaptığı herhangi bir belgeye standart metin işaretleyicileri otomatik olarak uygular ve standart metin işaretleyicilerini açıkça uygulamak gerekli değildir.  
  
2. Üzerinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> `GUID` çalışmak istediğiniz metin işaretleyicisi ile yöntemini çağırarak ilgilendiğiniz işaretin Işaret türü kimliğini edinin.  
  
    > [!NOTE]
    > `GUID`Metin işaretçisini sağlayan VSPackage veya hizmetin kullanmayın.  
  
3. Yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> çağırmak için bir parametre olarak yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> veya <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> belirli bir metin bölgesine metin işaretçisi uygulamak için yöntemini çağırarak elde EDILEN işaret türü kimliğini kullanın.  
  
#### <a name="to-add-features-to-text-markers"></a>Metin işaretçilerine özellikler eklemek için  
  
1. Araç ipuçları, özel bağlam menüsü veya özel koşullara yönelik işleyici gibi bir metin işaretine ek özellikler eklemek istenebilir. Bunun için:  
  
2. Arabirimini uygulayan bir nesne oluşturun <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
3. Ek işlevsellik isteniyorsa, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> arabirimini uygulayan aynı nesne üzerinde arabirimleri uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>Oluşturduğunuz arayüzü, yöntemine yapılan çağrıya <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> veya metin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> işaretçisini belirli bir metin bölgesine uygulamak için kullanılan yönteme geçirin.  
  
5. Bir metin işaretçisi bölgesine bağlam menüsü desteği eklendiğinde, menüyü oluşturmak için gereklidir.  
  
     Bağlam menüsü oluşturma hakkında daha fazla bilgi için bkz. [Bağlam menüleri](../extensibility/context-menus.md).  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ortam, yöntemi gibi sağlanan arabirimlerin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> veya <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> gerektiğinde yöntemin yöntemlerini çağırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API ile metin Işaretleyicileri kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Nasıl yapılır: standart metin Işaretçileri ekleme](../extensibility/how-to-add-standard-text-markers.md)   
 [Nasıl yapılır: özel metin Işaretçileri oluşturma](../extensibility/how-to-create-custom-text-markers.md)   
 [Nasıl Yapılır: Hata İşaretçilerini Uygulama](../extensibility/how-to-implement-error-markers.md)
