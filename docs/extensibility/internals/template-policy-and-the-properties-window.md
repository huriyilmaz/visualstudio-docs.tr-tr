---
title: Şablon İlkesi ve Özellikler Penceresi | Microsoft Docs
description: Şablon ilkesi kullanarak özellikler için varsayılan değerleri ayarlama, özellikleri gizleme ve özellikler ekleme hakkında bilgi Özellikler penceresi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 84f08740ac47701506f37e3e3aababa329f1ef61
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158807"
---
# <a name="template-policy-and-the-properties-window"></a>Şablon İlkesi ve Özellikler Penceresi
Bir proje bir kurumsal şablon projesinin içinde olduğunda, bu kurumsal şablon projesi ilkeyi zorlar. Şablon ilkesi, özellikler için varsayılan değerleri ayarlamak, özellikleri gizlemek, özellik eklemek ve daha pek çok işlem yapmak için kullanılmaktadır.

 Özellikler penceresindeki bilgilerin display'ini kontrol etmek **için** şablon ilkesi kullanmak, uygulamaktan <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> farklıdır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> nesne özelliklerini bileşen düzeyinde, şablon ilkesi ise nesne özelliklerini çözüm veya proje düzeyinde sınırlamak için kullanılabilir. Başka bir deyişle

- Belirli nesneler için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Özellikler penceresinde nelerin görüntülendiğinden **belirlemek için** yöntemleri uygulama

- Daha önce belirtilen nesneler için Özellikler penceresinde nelerin görüntülendiğinden belirlemek için çözüm ve **proje** düzeyinde şablon ilkesi kullanın

  Çözüm Gezgini'de belirtilen türde bir proje  öğesi seçildiğinde Özellikler penceresinde belirli özellikleri seçmeli  olarak sınırlamak için şablon ilkesi kullanmak, bir proje üzerinde çalışan geliştirme ekibinin tüm üyeleri için yararlı olabilir. Örneğin, şablon ilkesi kullanarak, bir veritabanında geliştiricileriniz için tüm bağlantı dizesi bilgilerini oluşturabilir ve bağlantı dizesini salt okunur hale babilirsiniz. Bu şekilde, her geliştiricinin veri erişimi için doğru yolu kullandığından emin olmak için basit bir yol sebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
