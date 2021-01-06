---
title: Şablon Ilkesi ve Özellikler penceresi | Microsoft Docs
description: Özellikler için varsayılan değerleri ayarlamak için şablon İlkesi kullanma, özellikleri gizleme ve Özellikler penceresi özellikler ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 105a90699689ff6eab6ea5bdfa3d4037e700ecb5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877721"
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
