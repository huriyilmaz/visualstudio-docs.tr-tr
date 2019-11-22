---
title: Visual Studio SDK 'Sı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59ef6ae6b042b1616997821febe156ef5cac3b7f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299705"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK, Visual Studio özelliklerini genişletmenize veya yeni özellikleri Visual Studio 'da tümleştirmenize yardımcı olur. Uzantılarınızı diğer kullanıcılara ve ayrıca Visual Studio Galerisine dağıtabilirsiniz. Aşağıda, Visual Studio 'Yu genişletebilmeniz için bazı yollar verilmiştir:  
  
- IDE 'ye komutlar, düğmeler, menüler ve diğer kullanıcı arabirimi öğeleri ekleme  
  
- Yeni işlevsellik için araç pencerelerini ekleyin  
  
- Belirli bir dil için IntelliSense 'i genişletin veya yeni programlama dilleri için IntelliSense sağlayın  
  
- Geliştiricilerin daha iyi kod yazmasına yardımcı olacak ipuçları ve öneriler sağlamak için hafif bulbs kullanın  
  
- Yeni dil desteğini etkinleştir  
  
- Özel proje türü Ekle  
  
- Visual Studio Market aracılığıyla milyonlarca geliştiriciye ulaşın  
  
  Daha önce hiç bir Visual Studio uzantısı yazmadıysanız, bu özellikler hakkında daha fazla bilgi ve [Visual Studio uzantıları geliştirmeye Başlarken](../extensibility/starting-to-develop-visual-studio-extensions.md)hakkında daha fazla bilgi bulmanız gerekir.  
  
## <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK 'daki yenilikler  
 Visual Studio SDK, bir VSıX paketi kullanarak menü komutları, araç pencereleri ve Düzenleyici uzantıları oluşturmanıza imkan tanıyan açık bulbs ve yeni proje öğeleri dahil bazı yeni özelliklere sahiptir. Daha fazla bilgi için [Visual Studio 2015 SDK'sındaki yenilikler](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio Kullanıcı Deneyimi Yönergeleri  
 Uzantı için kullanıcı arabirimini tasarlamaya yönelik harika ipuçları alın [Visual Studio kullanıcı deneyimi yönergeleri](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Ayrıca, [Adres DPI sorunları](../extensibility/addressing-dpi-issues2.md) konusundaki UZANTıNıZıN yüksek DPI cihazlarda harika görünmesini sağlama hakkında bilgi edinebilirsiniz.  
  
 Harika görüntü yönetimi ve yüksek DPı ve tema desteği için [görüntü hizmetinden ve katalogdan](../extensibility/image-service-and-catalog.md) yararlanın.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Mevcut Visual Studio uzantılarını bulma ve yükleme  
 Visual Studio uzantılarını **Araçlar** menüsündeki **Uzantılar ve güncelleştirmeler** iletişim kutusunda bulabilirsiniz. Daha fazla bilgi için [bulma ve Visual Studio uzantılarını kullanarak](../ide/finding-and-using-visual-studio-extensions.md). Uzantıları [Visual Studio Market](https://marketplace.visualstudio.com/) de bulabilirsiniz  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK Başvurusu  
 Visual Studio SDK API başvurusunu [Visual STUDIO SDK başvurusunda](../extensibility/visual-studio-sdk-reference.md)bulabilirsiniz.  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK örnekleri  
 [Visual Studio örneklerinde](https://aka.ms/vs2015sdksamples)GITHUB 'DA vs SDK uzantılarının açık kaynak örneklerini bulabilirsiniz. Bu GitHub deposu, Visual Studio 'daki çeşitli Genişletilebilir özellikleri gösteren örnekler içerir.  
  
## <a name="other-visual-studio-sdk-resources"></a>Diğer Visual Studio SDK kaynakları  
 VSSDK hakkında sorularınız varsa veya deneyimlerini geliştirme ve genişletmelerini paylaşmak istiyorsanız, [Visual Studio genişletilebilirlik Forumu](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) veya [extendvs grup sohbetini](https://gitter.im/Microsoft/extendvs)kullanabilirsiniz.  
  
 [VSX Arcana bloguna](https://blogs.msdn.microsoft.com/vsx/) daha fazla bilgi ve Microsoft MVP 'leri tarafından yazılmış çok sayıda blog bulabilirsiniz:  
  
- [Sık kullanılan Visual Studio uzantıları](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)  
  
- [Visual Studio genişletilebilirliği](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Visual Studio 'Yu genişletme](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2015 'ye geçirme](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [SSS: eklentileri VSPackage uzantılarına dönüştürme](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Yönetilen kodda birden çok Iş parçacığını yönetme](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)   
 [Araç çubuklarına komut ekleme](../extensibility/adding-commands-to-toolbars.md)   
 [Araç Windows  genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)  
 [Düzenleyici ve dil hizmeti uzantıları](../extensibility/editor-and-language-service-extensions.md)   
 [Projeleri genişletme](../extensibility/extending-projects.md)   
 [Kullanıcı ayarlarını ve seçeneklerini genişletme](../extensibility/extending-user-settings-and-options.md)   
 [Özel proje ve öğe şablonları oluşturma](../extensibility/creating-custom-project-and-item-templates.md)   
 [Özellikleri ve özellik penceresini genişletme](../extensibility/extending-properties-and-the-property-window.md)   
 [Visual Studio 'Nun diğer kısımlarını genişletme](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)   
 [Bağlı hizmetleri genişletme](../extensibility/extending-connected-services.md)   
 [VSPackages  yönetme](../extensibility/managing-vspackages.md)  
 [Visual Studio yalıtılmış kabuğu](../extensibility/visual-studio-isolated-shell.md)   
 [Visual Studio uzantılarını gönderme](../extensibility/shipping-visual-studio-extensions.md)   
 [Visual STUDIO SDK içinde](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual STUDIO SDK  desteği](../extensibility/support-for-the-visual-studio-sdk.md)  
 [Arşiv](../extensibility/archive.md)   
 [Visual Studio SDK Başvurusu](../extensibility/visual-studio-sdk-reference.md)
