---
title: 'Nasıl yapılır: ASP.NET tabanlı Iş akışlarında hata ayıklama (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668664"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Nasıl yapılır: ASP.NET tabanlı Iş akışlarında hata ayıklama (eski)
Bu konuda, eski [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedefleyen [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tabanlı [!INCLUDE[wf](../includes/wf-md.md)] uygulamalarının hatalarını ayıklama işlemini açıklar.

 İş akışının barındırıldığı işleme ekleyerek, Web hizmeti olarak yayınlanan ASP.NET veya eski iş akışlarında başlatılan eski iş akışlarında hata ayıklayabilirsiniz.

### <a name="to-debug-an-aspnet-based-workflow"></a>ASP.NET tabanlı bir iş akışında hata ayıklamak için

1. Web. config dosyasında **Debug = true** ayarlayarak ASP.NET uygulaması için hata ayıklamayı etkinleştirin.

2. İş akışı kitaplığını başlangıç projesi olarak ayarlayın ve iş akışında kesme noktaları ayarlayın.

3. İş akışı proje özellikleri **hata ayıklama** seçeneği **tarayıcıyı dış URL ile Başlat** metin kutusu ' na varsayılan Web sayfasının URL 'sini girin.

4. **Hata Ayıkla** menüsünde **İşleme İliştir** ' i seçin.

5. **Kullanılabilir işlemler** listesinden iliştirilecek işlemi seçin.

     İş akışının barındırıldığı W3wp. exe, webdev. webserver veya aspnet_wp işlemine iliştirin.

6. **Ekle** metin kutusunun yanındaki **Seç** ' e tıklayın.

     **Kod türünü seç** iletişim kutusu görüntülenir.

7. **Bu kod türlerini hata ayıkla** ' yı seçin ve **iş akışını**seçin.

8. **Tamam**'a tıklayın.

9. **Ekle**' ye tıklayın.

10. Varsayılan Web sayfasını bir tarayıcıda açın ve iş akışını başlatın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Windows Workflow Foundation Için Visual Studio hata ayıklayıcısını çağırma (eski)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [nasıl yapılır: Iş akışlarında kesme noktaları ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [eski iş akışlarının hatalarını ayıklama](../workflow-designer/debugging-legacy-workflows.md)