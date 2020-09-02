---
title: "Nasıl yapılır: CD yüklemeleri için AutoStart 'ı etkinleştirme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153779"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Nasıl yapılır: CD Yüklemeleri için AutoStart'ı Etkinleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulama, CD-ROM veya DVD-ROM gibi çıkarılabilir medya aracılığıyla dağıtıldığında, `AutoStart` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] medya takıldığında uygulamanın otomatik olarak başlatılmasını sağlayabilirsiniz.  
  
 `AutoStart`, **Proje Tasarımcısı**' nın **Yayımla** sayfasında etkinleştirilebilir.  
  
### <a name="to-enable-autostart"></a>AutoStart 'ı etkinleştirmek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Seçenekler** düğmesine tıklayın.  
  
     **Yayımlama seçenekleri** iletişim kutusu görüntülenir.  
  
4. **Dağıtım**' ye tıklayın.  
  
5. CD **takıldığında kurulumu otomatik olarak Başlat** onay kutusunu seçin.  
  
     Uygulama yayımlandığında bir Autorun. inf dosyası yayımlama konumuna kopyalanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
