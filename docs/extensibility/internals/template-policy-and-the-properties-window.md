---
title: Şablon Ilkesi ve Özellikler penceresi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704660"
---
# <a name="template-policy-and-the-properties-window"></a>Şablon İlkesi ve Özellikler Penceresi
Bir proje kurumsal şablon projesinde yer aldığı zaman, bu kurumsal şablon proje ilkeyi uygulayabilir. Şablon İlkesi, özellikler için varsayılan değerleri ayarlamak, özellikleri gizlemek, özellik eklemek vb. için kullanılabilen bir kısıtlayan sistem haline gelir.

 **Özellikler** penceresinde bilgilerin görüntülenmesini denetlemek için şablon İlkesi kullanmak, uygulama uygulamalarından farklıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> bileşen düzeyinde nesne özelliklerini işler, ancak şablon İlkesi çözüm veya proje düzeyindeki nesne özelliklerini kısıtlamak için kullanılabilir. Diğer bir deyişle

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Belirli nesneler Için **Özellikler** penceresinde neyin görüntülendiğini belirlemek için üzerinde yöntemleri uygulayın

- Daha önce belirtilen nesneler için **Özellikler** penceresinde neyin görüntülendiğini belirlemek için çözüm ve proje düzeyinde şablon ilkesini kullanın

  Belirli bir türdeki bir proje öğesi **Çözüm Gezgini** ' de seçildiğinde, **Özellikler** penceresindeki belirli özellikleri seçmeli olarak kısıtlamak için şablon İlkesi kullanmak, geliştirme ekibinin bir proje üzerinde çalıştığı tüm üyelerine faydalı olabilir. Örneğin, şablon ilkesini kullanarak, geliştiricileriniz için bir veritabanındaki tüm bağlantı dizesi bilgilerini ayarlayabilir ve bağlantı dizesini salt okunurdur hale getirebilirsiniz. Bu şekilde, her geliştiricinin veri erişimi için doğru yolu kullanmasını güvence altına almak için basit bir yol sağlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
