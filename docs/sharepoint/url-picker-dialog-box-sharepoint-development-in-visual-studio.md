---
title: URL Seçici iletişim kutusu (SharePoint geliştirme)
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 991693c3379e008a2a907efd3127290c7e804c22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66261939"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL Seçici iletişim kutusu (Visual Studio 'da SharePoint geliştirme)
  URL Seçici iletişim kutusunda, projenizde veya SharePoint çalıştıran yerel sunucuda bulunan ana sayfa dosyaları veya görüntü dosyaları gibi dosyaları seçebilirsiniz.

 Bu iletişim kutusu, bir özelliği ayarlamak için bir dosya seçme seçeneğine sahip olduğunuzda görüntülenir. **Özellikler** penceresinde çeşitli Özellikler ' in yanındaki üç nokta düğmesini (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) seçerek bu iletişim kutusunu açabilirsiniz. Üç nokta düğmesi, tasarımcı **kaynak** görünümündeki belirli özniteliklere değer atarken bir IntelliSense istemi olarak da görünür.

## <a name="uielement-list"></a>UIElement listesi
 **Proje klasörleri** Projede veya SharePoint çalıştıran yerel sunucuda tanımlanan klasörlerin listesini görüntüler. Alt klasörleri göstermek için genişletme düğmesini seçin.

 Projenizdeki dosyaları seçmek için **Proje** düğümünü genişletin. İletişim kutusunda seçilebilir olarak görünmesi için, projenizdeki dosyaların aşağıdaki ölçütlere uyması gerekir:

- Dosya eşlenmiş bir klasörde bulunmalıdır.

- Dosyanın çözüm paketine eklenmesi gerekir.

- Dosya başka bir projede bulunamıyor.

  Bu ölçütlere uymayan dosyalara başvurmak isterseniz, dosyanın yolunu el ile girmeniz gerekir.

  SharePoint çalıştıran yerel sunucuda bulunan dosyaları seçmek için **sunucu** düğümünü genişletin. İletişim kutusunda seçilebilir olarak görünmesi için, bu dosyaların aşağıdaki ölçütlere uyması gerekir:

- Dosya şu eşlenmiş klasörlerden birinde bulunmalıdır: **resimler**, **düzenler**veya **ControlTemplates**.

- Dosya, SharePoint içerik veritabanında bulunamıyor.

  Bu ölçütlere uymayan dosyalara başvurmak isterseniz, dosyanın yolunu el ile girmeniz gerekir.

  **Klasörün içeriği** Seçili klasördeki dosyaların listesini görüntüler. Bir dosya seçin ve ardından iletişim kutusunu kapatmak ve seçiminizi çağıran işleme göndermek için **Tamam** düğmesini seçin.

  **Dosya türü** Gerçekleştirdiğiniz görev için uygun olan dosya listesinden seçim yapmanıza olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
