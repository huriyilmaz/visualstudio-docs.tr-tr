---
title: Uygulamaları, hizmetleri ve bileşenleri dağıtma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ca4d6a4097848021073bb77323fd0456f3dddc1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74289820"
---
# <a name="deploying-applications-services-and-components"></a>Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir uygulamayı, hizmeti ya da bileşeni dağıtarak bunu diğer bilgisayarlardaki, cihazlardaki, sunuculardaki ya da buluttaki yükleme için dağıtmış olursunuz. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz.  
  
 Aşağıdaki tabloda, farklı dağıtım senaryolarının açıklamalarını ve bu senaryoları başarıyla tamamlama hakkında daha fazla bilgi sunan bağlantıları bulabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Dağıtım Senaryosu|Destekleyici İçerik|  
|-------------------------|------------------------|  
|**Buluta yayımlayın:** Microsoft Azure dağıtmak için Visual Studio kullanarak uygulamaları, hizmetleri ve verileri her yerden kullanılabilir hale getirebilirsiniz.|[Uygulamaları Microsoft Azure yayımlama](/visualstudio/deployment/quickstart-deploy-to-azure)|  
|**Windows Mağazası uygulaması yayımlama:** Uygulamalarınızı Windows Mağazası 'ndan dünyanın dört bir yanındaki müşterilere kolayca oluşturabilir, gönderebilir ve satabilirsiniz.|[Windows Mağazası uygulamalarını paketleme, dağıtma ve sorgulama](https://msdn.microsoft.com/library/hh446593\(v=vs.85\).aspx)|  
|**Windows Phone uygulaması yayımlama:** Windows Phone geliştirme merkezi 'nde sertifika için mevcut bir uygulamaya yeni bir uygulama veya güncelleştirme gönderebilirsiniz.|[Windows Phone uygulaması yayımlama](https://developer.microsoft.com/)|  
|**Bir ASP.NET uygulamasını veya hizmetini dağıtın:** ASP.NET uygulamalarını ve hizmetlerini çeşitli yollarla dağıtabilirsiniz.|[ASP.NET Web uygulamaları ve Hizmetleri 'ni dağıtma](https://docs.microsoft.com/aspnet/mvc/overview/deployment/)|  
|**LightSwitch uygulaması veya hizmeti dağıtma:** LightSwitch kullanarak uygulamaları ve OData hizmetlerini oluşturduktan sonra, bunları bir Web sunucusuna veya Microsoft Azure dağıtabilirsiniz.|[LightSwitch uygulamalarını dağıtma](https://msdn.microsoft.com/library/4818d933-295c-4ecc-9148-7ad9ca28dcdb)|  
|**SharePoint için bir uygulama yayımlama:** SharePoint için bir uygulamayı Office Mağazası 'na veya dahili bir kuruluşun uygulama kataloğuna yayımlayabilirsiniz.|[Visual Studio kullanarak SharePoint için bir uygulama yayımlama](https://msdn.microsoft.com/library/office/jj220044\(v=office.15\).aspx)|  
|**Office için bir uygulama yayımlama:** Office için bir uygulamayı Office Mağazası 'na veya dahili bir kuruluşun uygulama kataloğuna yayımlayabilirsiniz.|[Office için uygulamanızı yayımlama](https://msdn.microsoft.com/library/office/fp123515.aspx)|  
|{1&gt;Bir WCF hizmetini dağıtma:&lt;1} Diğer uygulamalar, bir web sunucusuna dağıttığınız WCF RIA hizmetlerini kullanabilir.|[WCF RıA Hizmetleri çözümlerini dağıtma](https://msdn.microsoft.com/library/ff426912\(v=vs.91\).aspx)|  
|{1&gt;Bir OData hizmetini dağıtma:&lt;1} Diğer uygulamalar, bir web sunucusuna dağıttığınız OData hizmetlerini kullanabilir.|[OData hizmeti dağıtma](https://msdn.microsoft.com/library/hh973447.aspx)|  
|**Masaüstü uygulaması dağıtma:** ClickOnce dağıtımını kullanarak bir masaüstü uygulamasını bir Web sunucusuna veya ağ dosya paylaşımında yayımlayabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir.|[ClickOnce Güvenliği ve Dağıtımı](../deployment/clickonce-security-and-deployment.md)|  
|{1&gt;Bir kurulum programı oluşturma:&lt;1} Bir kurulum programını, ücretsiz olan InstallShield Limited Edition kullanarak oluşturabilirsiniz.|[InstallShield Limited Edition](../deployment/installshield-limited-edition.md)|  
|**Mevcut bir kurulum programını koruyun:** Visual Studio Yükleyicisi projeleri uzantısını yükleyerek Visual Studio 'nun önceki bir sürümünde oluşturulmuş bir kurulum programını kullanmaya devam edin.|[Visual Studio Yükleyicisi projeleri uzantısı](https://devblogs.microsoft.com/visualstudio/visual-studio-installer-projects-extension/)<br /><br /> Yükleyici projelerine yönelik belgeler şurada bulunabilir: [Visual Studio yükleyicisi dağıtım](https://msdn.microsoft.com/library/2kt85ked\(v=vs.100\).aspx)|  
|**Görsel C++ uygulama dağıtma:** merkezi dağıtım, yerel dağıtım veya C++ statik bağlama kullanarak Visual çalışma zamanını bir uygulamayla dağıtabilirsiniz.|[Yerleşik Masaüstü Uygulamalarını Dağıtma (Visual C++)](/cpp/windows/deploying-native-desktop-applications-visual-cpp)|  
|**Bir uygulamayı test Için dağıtma:** Uygulamalarınızı sanal ortamlara dağıtarak daha gelişmiş geliştirme ve test olanağı sağlayabilirsiniz.|[Laboratuvar ortamında test etme](https://msdn.microsoft.com/library/14ba54c8-a158-4a6e-b00a-b00ae960feb8)|  
|{1&gt;Ön koşulları yükleme:&lt;1} Masaüstü uygulamaları için ön koşulları, bir önyükleyici olarak bilinen genel bir yükleyici yapılandırarak yükleyebilirsiniz.|[Uygulama Dağıtımının Önkoşulları](../deployment/application-deployment-prerequisites.md)|
