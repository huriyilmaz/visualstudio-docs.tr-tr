---
title: URL seçici iletişim kutusu (SharePoint)
description: Kullanıcının projesinde veya yerel sunucuda bulunan dosyaları seçmesini sağlayan URL seçici iletişim kutusu hakkında bilgi SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 22f05833ca2937a44d5d731bdef06d8971a3e57d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156207"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL seçici iletişim kutusu (SharePoint geliştirme Visual Studio)
  URL seçici iletişim kutusunda, ana sayfa dosyaları veya projenizin içinde veya projenizin çalıştırıcısı olan yerel sunucuda bulunan görüntü dosyaları gibi dosyaları SharePoint.

 Özellik ayarlamak için bir dosya seçme seçeneğiniz olduğunda bu iletişim kutusu görüntülenir. Özellikler penceresinde çeşitli özelliklerin yanındaki üç nokta düğmesini (![ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")Mobil Tasarımcı üç nokta ) seçerek bu iletişim **kutusunu açabilirsiniz.** Tasarımcının Kaynak görünümünde belirli özniteliklere değer atadığınız zaman, üç nokta düğmesi bir IntelliSense **istemi** olarak da görünür.

## <a name="uielement-list"></a>UIElement listesi
 **Project klasörleri** Projede veya SharePoint çalıştıran yerel sunucuda tanımlanan klasörlerin listesini SharePoint. Alt klasörleri görüntülemek için genişletme düğmesini seçin.

 Projenizin **Project** seçmek için Project düğümünü genişletin. İletişim kutusunda seçilebilir olarak görünmesi için projenizin dosyaları aşağıdaki ölçütleri karşılamalı:

- Dosya, eşlenmiş bir klasörde yer alalır.

- Dosyanın çözüm paketine eklenmiş olması gerekir.

- Dosya başka bir projede bulunamaz.

  Bu ölçütleri karşılamayan dosyalara başvuru yapmak için dosyanın yolunu el ile girmeniz gerekir.

  sunucuyu  çalıştıran yerel sunucuda bulunan dosyaları seçmek için Sunucu düğümünü SharePoint. İletişim kutusunda seçilebilir olarak görünmesi için bu dosyaların aşağıdaki ölçütleri karşılaması gerekir:

- Dosya, şu eşlenen klasörlerden biri içinde bulunarak **görüntü,** **Düzen veya** **ControlTemplates .**

- Dosya, içerik veritabanında SharePoint bulunamaz.

  Bu ölçütleri karşılamayan dosyalara başvuru yapmak için dosyanın yolunu el ile girmeniz gerekir.

  **Klasörün içeriği** Seçilen klasördeki dosyaların listesini görüntüler. Bir dosya seçin ve ardından Tamam **düğmesini** seçen iletişim kutusunu kapatın ve seçiminizi çağıran işleme gönderin.

  **Türe göre dosyalar** Gerçekleştirmekte olduğu görev için uygun dosya listesinden seçim gerçekleştirmenizi sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint için web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
