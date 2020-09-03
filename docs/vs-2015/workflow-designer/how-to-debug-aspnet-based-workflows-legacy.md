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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668664"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Nasıl Yapılır: ASP.NET Tabanlı İş Akışlarında Hata Ayıklama (Eski)
Bu konu, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] [!INCLUDE[wf](../includes/wf-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] eski sürümünde veya öğesini hedefleyen hata ayıklama tabanlı uygulamaların nasıl yapılacağını açıklar [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] [!INCLUDE[wfd1](../includes/wfd1-md.md)] .

 İş akışının barındırıldığı işleme ekleyerek, Web hizmeti olarak yayınlanan ASP.NET veya eski iş akışlarında başlatılan eski iş akışlarında hata ayıklayabilirsiniz.

### <a name="to-debug-an-aspnet-based-workflow"></a>ASP.NET tabanlı bir iş akışında hata ayıklamak için

1. web.config dosyasında **Debug = true** ayarlayarak ASP.NET uygulaması için hata ayıklamayı etkinleştirin.

2. İş akışı kitaplığını başlangıç projesi olarak ayarlayın ve iş akışında kesme noktaları ayarlayın.

3. İş akışı proje özellikleri **hata ayıklama** seçeneği **tarayıcıyı dış URL ile Başlat** metin kutusu ' na varsayılan Web sayfasının URL 'sini girin.

4. **Hata Ayıkla** menüsünde **İşleme İliştir** ' i seçin.

5. **Kullanılabilir işlemler** listesinden iliştirilecek işlemi seçin.

     İş akışının barındırıldığı w3wp.exe, webdev. webserver veya aspnet_wp işlemine iliştirin.

6. **Ekle** metin kutusunun yanındaki **Seç** ' e tıklayın.

     **Kod türünü seç** iletişim kutusu görüntülenir.

7. **Bu kod türlerini hata ayıkla** ' yı seçin ve **iş akışını**seçin.

8. **Tamam**’a tıklayın.

9. **Ekle**' ye tıklayın.

10. Varsayılan Web sayfasını bir tarayıcıda açın ve iş akışını başlatın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Windows Workflow Foundation Için Visual Studio hata ayıklayıcısını çağırma (eski)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [nasıl yapılır: Iş akışlarında kesme noktaları ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [eski iş akışlarının hatalarını ayıklama](../workflow-designer/debugging-legacy-workflows.md)