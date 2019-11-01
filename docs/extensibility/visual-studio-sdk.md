---
title: Visual Studio SDK 'Sı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 662b64f69b278c4cc815a742c5cba26592e000bd
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189091"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK, Visual Studio özelliklerini genişletmenize veya yeni özellikleri Visual Studio 'da tümleştirmenize yardımcı olur. Uzantılarınızın yanı sıra Visual Studio Market diğer kullanıcılara da dağıtabilirsiniz. Aşağıda, Visual Studio 'Yu genişletebilmeniz için bazı yollar verilmiştir:

- IDE 'ye komutlar, düğmeler, menüler ve diğer kullanıcı arabirimi öğeleri ekleme

- Yeni işlevsellik için araç pencerelerini ekleyin

- Belirli bir dil için IntelliSense 'i genişletin veya yeni programlama dilleri için IntelliSense sağlayın

- Geliştiricilerin daha iyi kod yazmasına yardımcı olacak ipuçları ve öneriler sağlamak için hafif bulbs kullanın

- Yeni dil desteğini etkinleştir

- Özel proje türü Ekle

- Visual Studio Market aracılığıyla milyonlarca geliştiriciye ulaşın

  Daha önce hiç bir Visual Studio uzantısı yazmadıysanız, bu özellikler hakkında daha fazla bilgi ve [Visual Studio uzantıları geliştirmeye Başlarken](../extensibility/starting-to-develop-visual-studio-extensions.md)hakkında daha fazla bilgi bulmanız gerekir.

## <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme
 Visual Studio SDK, Visual Studio kurulumunda isteğe bağlı bir özelliktir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Visual Studio 2017 SDK 'daki yenilikler
 Visual Studio SDK, VSıX v3 biçimi gibi bazı yeni özelliklerin yanı sıra uzantınızı güncelleştirmenizi gerektirebilecek büyük değişiklikler içerir. Daha fazla bilgi için bkz. [Visual Studio 2017 SDK 'daki](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)yenilikler.

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio Kullanıcı deneyimi yönergeleri
 [Visual Studio Kullanıcı deneyimi kılavuzlarından](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)UZANTıNıZıN Kullanıcı arabirimini tasarlamak için harika ipuçları alın.

 Ayrıca, uzantınızın, [Adres DPI sorunları](../extensibility/addressing-dpi-issues2.md) MAKALESINDE yüksek DPI cihazlarda harika görünmesini nasıl sağlayabileceğinizi de öğrenebilirsiniz.

 Harika görüntü yönetimi ve yüksek DPı ve tema desteği için [görüntü hizmetinden ve katalogdan](../extensibility/image-service-and-catalog.md) yararlanın.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Mevcut Visual Studio uzantılarını bul ve Kur
 Visual Studio uzantılarını **Araçlar** menüsündeki **Uzantılar ve güncelleştirmeler** iletişim kutusunda bulabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md). Uzantıları [Visual Studio Market](https://marketplace.visualstudio.com/) de bulabilirsiniz

## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK başvurusu
 Visual Studio SDK API başvurusunu [Visual STUDIO SDK başvurusunda](../extensibility/visual-studio-sdk-reference.md)bulabilirsiniz.

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK örnekleri
 [Visual Studio örneklerinde](https://aka.ms/vs2015sdksamples)GITHUB 'DA vs SDK uzantılarının açık kaynak örneklerini bulabilirsiniz. Bu GitHub deposu, Visual Studio 'daki çeşitli Genişletilebilir özellikleri gösteren örnekler içerir.

## <a name="other-visual-studio-sdk-resources"></a>Diğer Visual Studio SDK kaynakları
 VSSDK hakkında sorularınız varsa veya deneyimlerini geliştirme ve genişletmelerini paylaşmak istiyorsanız, [Visual Studio genişletilebilirlik Forumu](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) veya [extendvs Gitter Chatroom](https://gitter.im/Microsoft/extendvs)kullanabilirsiniz.

 [VSX Arcana bloguna](https://blogs.msdn.microsoft.com/vsx/) daha fazla bilgi ve Microsoft MVP 'leri tarafından yazılmış çok sayıda blog bulabilirsiniz:

- [Sık kullanılan Visual Studio uzantıları](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Visual Studio genişletilebilirliği](http://www.visualstudioextensibility.com/overview/vs/)

- [Visual Studio 'Yu genişletme](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Ayrıca bkz.

- [Menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017 'ye geçirme](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [SSS: eklentileri VSPackage uzantılarına dönüştürme](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)
- [Yönetilen kodda birden çok iş parçacığını yönetme](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Menüleri ve komutları Genişlet](../extensibility/extending-menus-and-commands.md)
- [Araç çubuklarına komut ekleme](../extensibility/adding-commands-to-toolbars.md)
- [Araç pencerelerini genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)
- [Düzenleyici ve dil hizmeti uzantıları](../extensibility/editor-and-language-service-extensions.md)
- [Projeleri genişletme](../extensibility/extending-projects.md)
- [Kullanıcı ayarlarını ve seçeneklerini genişletme](../extensibility/extending-user-settings-and-options.md)
- [Özel proje ve öğe şablonları oluşturma](../extensibility/creating-custom-project-and-item-templates.md)
- [Özellikleri ve özellik penceresini genişletme](../extensibility/extending-properties-and-the-property-window.md)
- [Visual Studio 'nun diğer kısımlarını genişletme](../extensibility/extending-other-parts-of-visual-studio.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
- [VSPackages 'leri Yönet](../extensibility/managing-vspackages.md)
- [Visual Studio yalıtılmış Kabuğu](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Visual Studio uzantılarını gönder](../extensibility/shipping-visual-studio-extensions.md)
- [Visual Studio SDK’nın İçinde](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Visual Studio SDK Desteği](../extensibility/support-for-the-visual-studio-sdk.md)
- [Visual Studio SDK başvurusu](../extensibility/visual-studio-sdk-reference.md)
