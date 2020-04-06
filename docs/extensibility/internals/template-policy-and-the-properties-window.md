---
title: Şablon İlkesi ve Özellikler Penceresi | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704660"
---
# <a name="template-policy-and-the-properties-window"></a>Şablon İlkesi ve Özellikler Penceresi
Bir proje bir kuruluş şablonu projesinin içinde bulunduğunda, bu kurumsal şablon projesi ilke yi zorlayabilir. Şablon ilkesi, özellikler için varsayılan değerleri ayarlamak, özellikleri gizlemek, özellikler eklemek ve benzerleri için kullanılabilecek kısıtlayıcı bir sistem haline gelir.

 **Özellikler** penceresindeki bilgilerin görüntülenmesini denetlemek için şablon ilkesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>kullanmak, uygulamadan farklıdır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>bileşen düzeyinde nesne özelliklerini işler, şablon ilkesi çözüm veya proje düzeyinde nesne özelliklerini kısıtlamak için kullanılabilir. Başka bir deyişle

- Belirli nesneler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> için **Özellikler** penceresinde görüntülenen leri belirlemek için yöntemleri uygulayın

- Daha önce belirtilen nesneler için **Özellikler** penceresinde nelerin görüntüleneceğini belirlemek için çözüm ve proje düzeyinde şablon ilkesini kullanma

  Çözüm Gezgini'nde belirli bir türde bir proje öğesi seçildiğinde **Özellikler** **Solution Explorer** penceresindeki belirli özellikleri seçici olarak kısıtlamak için şablon ilkesinin kullanılması, proje üzerinde çalışan geliştirme ekibinin tüm üyeleri için yararlı olabilir. Örneğin, şablon ilkesini kullanarak, geliştiricileriniz için bir veritabanındaki tüm bağlantı dize bilgilerini ayarlayabilir ve bağlantı dizesini salt okunur hale getirebilirsiniz. Bu şekilde, her geliştiricinin veri erişimi için doğru yolu kullandığından emin olmak için basit bir yol sağlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
