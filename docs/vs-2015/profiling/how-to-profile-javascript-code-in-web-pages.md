---
title: 'Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa504e961ed8e592f5e3df84ff7a688fa2398200
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688141"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Nasıl Yapılır: Web Sayfalarında JavaScript Kodunun Profilini Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profil Oluşturma Araçları [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , izleme profili oluşturma yöntemini kullanarak bir Web uygulamasında, rastgele bir Web sayfasında veya JavaScript uygulamasında yürütülen JavaScript kodu için performans verilerini toplayabilir.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Internet Explorer 8 veya üzeri.  
  
> [!WARNING]
> Windows Mağazası uygulamalarında JavaScript profili için aşağıdaki konulardan birine bakın:  
> 
> - Uzak cihazda [JavaScript Işlev zamanlaması](https://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [JavaScript işlev zamanlaması](https://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   - [JavaScript Işlev zamanlaması verilerini çözümle](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   - 
  
 Bir performans oturumu oluşturmak için profil oluşturma sihirbazını kullanabilirsiniz. İzleme yöntemini belirtin ve ardından performans oturumunun Özellikler iletişim kutusunun Araçlar sayfasında JavaScript profil oluşturma seçeneğini belirtin.  
  
 JavaScript profil oluşturmayı belirttiğinizde, hem tarayıcıda çalıştırılan JavaScript kodu hem de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sunucuda yürütülen kod profili oluşturulur.  
  
- Bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması için, hem tarayıcıda çalıştırılan JavaScript kodu hem de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sunucuda yürütülen kod için profil oluşturulur.  
  
- Rastgele bir Web sayfasında, tarayıcıda yürütülen JavaScript kodu profili oluşturulur.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Bir ASP.NET Web uygulaması projesindeki JavaScript 'ı profil oluşturma  
  
1. İçinde [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] , [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web projesini açın.  
  
2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı tıklatın.  
  
3. Performans sihirbazının ilk sayfasında, **izleme** profil oluşturma yöntemini belirtin ve ardından **İleri**' ye tıklayın.  
  
4. Sihirbazın ikinci sayfasında, geçerli projenin hedef listesinde seçili olduğundan emin olun ve ardından Ileri ' ye tıklayın **.**  
  
5. Sihirbazın üçüncü sayfasında **profil JavaScript** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.  
  
6. Sihirbazın dördüncü sayfasında, Web uygulamasını tarayıcıda başlatmak için **son** ' a tıklayın.  
  
7. Profil eklemek istediğiniz işlevselliği yapın.  
  
8. Profil oluşturma oturumunu sonlandırmak için tarayıcıyı kapatın.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Ayrı Web sayfalarında veya JavaScript uygulamalarında JavaScript profili oluşturma  
  
1. [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] dosyasını açın.  
  
2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı tıklatın.  
  
3. Performans sihirbazının ilk sayfasında, **izleme** profil oluşturma yöntemini belirtin ve ardından **İleri**' ye tıklayın.  
  
4. Sihirbazın ikinci sayfasında, bir ASP.NET veya JavaScript uygulamasına tıklayın ve sonra Ileri ' ye tıklayın **.**  
  
5. Sihirbazın üçüncü sayfasında:  
  
    1. Uygulamanızın URL 'sini **veya yolunu HANGI URL veya yolda çalıştıracağınızı** yazın.  
  
    2. **Profil JavaScript** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.  
  
6. Sihirbazın dördüncü sayfasında, Web sayfasını tarayıcıda başlatmak için **son** ' a tıklayın.  
  
7. Profil eklemek istediğiniz işlevselliği yapın.  
  
8. Profil oluşturma oturumunu sonlandırmak için tarayıcıyı kapatın.
