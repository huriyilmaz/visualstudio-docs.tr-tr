---
title: Şablon Ilkesi ve Özellikler penceresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c67150c5a71a3d70df85669319795a405c60f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156019"
---
# <a name="template-policy-and-the-properties-window"></a>Şablon İlkesi ve Özellikler Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir proje kurumsal şablon projesinde yer aldığı zaman, bu kurumsal şablon proje ilkeyi uygulayabilir. Şablon İlkesi, özellikler için varsayılan değerleri ayarlamak, özellikleri gizlemek, özellik eklemek vb. için kullanılabilen bir kısıtlayan sistem haline gelir.  
  
 **Özellikler** penceresinde bilgilerin görüntülenmesini denetlemek için şablon İlkesi kullanmak, uygulama uygulamalarından farklıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> bileşen düzeyinde nesne özelliklerini işler, ancak şablon İlkesi çözüm veya proje düzeyindeki nesne özelliklerini kısıtlamak için kullanılabilir. Diğer bir deyişle  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Belirli nesneler Için **Özellikler** penceresinde neyin görüntülendiğini belirlemek için üzerinde yöntemleri uygulayın  
  
- Daha önce belirtilen nesneler için **Özellikler** penceresinde neyin görüntülendiğini belirlemek için çözüm ve proje düzeyinde şablon ilkesini kullanın  
  
  Belirli bir türdeki bir proje öğesi **Çözüm Gezgini** ' de seçildiğinde, **Özellikler** penceresindeki belirli özellikleri seçmeli olarak kısıtlamak için şablon İlkesi kullanmak, geliştirme ekibinin bir proje üzerinde çalıştığı tüm üyelerine faydalı olabilir. Örneğin, şablon ilkesini kullanarak, geliştiricileriniz için bir veritabanındaki tüm bağlantı dizesi bilgilerini ayarlayabilir ve bağlantı dizesini salt okunurdur hale getirebilirsiniz. Bu şekilde, her geliştiricinin veri erişimi için doğru yolu kullanmasını güvence altına almak için basit bir yol sağlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
