---
title: 'Nasıl yapılır: son kullanıcıların yükleneceği konumu belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82181d906adc3454dfe77ef4fb21d8bdf99df16f
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557992"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Nasıl yapılır: Son Kullanıcıların Yükleme Yapacakları Konumu Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması yayımlarken, kullanıcıların uygulamayı indirmek ve yüklemek için gideceği konum, uygulamayı ilk olarak yayımladığınız konum değildir. Örneğin, bazı kuruluşlarda bir geliştirici bir uygulamayı hazırlama sunucusuna yayımlayabilir ve ardından Yönetici uygulamayı bir Web sunucusuna taşır.  
  
 Bu durumda, kullanıcıların uygulamayı indirmek için gideceleceği Web sunucusunu belirtmek için `Installation URL` özelliğini kullanabilirsiniz. Bu, uygulama bildiriminin güncelleştirmelerin nerede bakacağını bilmesini sağlamak için gereklidir.  
  
 `Installation URL` özelliği, **Proje Tasarımcısı**' nın **Yayımla** sayfasında ayarlanabilir.  
  
 **Göz önünde** `Installation URL` özelliği **publishwizard**kullanılarak da ayarlanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Yükleme URL 'SI belirtmek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. Yükleme URL 'SI alanında, biçim `https://www.contoso.com/ApplicationName`kullanarak tam URL 'YI kullanarak yükleme konumunu veya `\\Server\ApplicationName`biçimini kullanarak bir UNC yolunu girin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Visual Studio 'Nun dosyaları nereye kopyaladığını belirtme](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
