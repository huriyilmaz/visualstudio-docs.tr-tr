---
title: 'Nasıl yapılır: ClickOnce Çevrimdışı veya çevrimiçi yüklemesi modunu belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149756"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Nasıl yapılır: ClickOnce Çevrimdışı veya Çevrimiçi Yükleme Modunu Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Install Mode`Uygulama için, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmayacağını belirler. **Uygulama yalnızca çevrimiçi kullanılabilir**olduğunda, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı çalıştırmak için kullanıcının yayımlama konumuna (bir Web sayfası veya bir dosya paylaşımında) erişimi olması gerekir. **Uygulamanın çevrimdışı kullanılabilir olduğunu**seçtiğinizde, uygulama **Başlangıç** menüsüne ve **Program Ekle veya Kaldır** iletişim kutusuna giriş ekler; Kullanıcılar bağlı olmadıkları zaman uygulamayı çalıştırabilir.  
  
 , `Install Mode` **Proje Tasarımcısı**' nın **Yayımla** sayfasında ayarlanabilir.  
  
 **Göz önünde** , `Install Mode` Yayımlama Sihirbazı kullanılarak da ayarlanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce uygulamasını yalnızca çevrimiçi kullanılabilir hale getirmek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Install Mode and Settings** alanında, **uygulama yalnızca çevrimiçi kullanılabilir** seçenek düğmesine tıklayın.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>ClickOnce uygulamasını çevrimiçi veya çevrimdışı kullanılabilir hale getirmek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Yüklenecek mod ve ayarlar** alanında, uygulama ' da **çevrimdışı kullanılabilir** ' ı tıklatın.  
  
     Yüklendiğinde, uygulama **Başlangıç** menüsüne giriş ekler ve Denetim Masası 'Nda **Program Ekle/Kaldır** ' ı görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [ClickOnce Dağıtım Stratejisini Seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
