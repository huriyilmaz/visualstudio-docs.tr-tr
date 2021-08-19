---
title: Visual Studio SDK | Microsoft Docs
description: Visual Studio SDK, özellikleri genişletmenize veya Visual Studio yeni özellikler eklemenize yardımcı olur. Visual Studio genişletebilmeniz için bazı yollarla ilgili bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f61ad24a7a94827720de388ed957f1c33dc7bc8c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078615"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK Visual Studio özelliklerini genişletmenize veya yeni özellikleri Visual Studio tümleştirmenize yardımcı olur. uzantılarınızı diğer kullanıcılara ve Visual Studio marketi ' ne dağıtabilirsiniz. Aşağıda Visual Studio genişletebilmeniz gereken bazı yollar verilmiştir:

- IDE 'ye komutlar, düğmeler, menüler ve diğer kullanıcı arabirimi öğeleri ekleme

- Yeni işlevsellik için araç pencerelerini ekleyin

- Belirli bir dil için IntelliSense 'i genişletin veya yeni programlama dilleri için IntelliSense sağlayın

- Geliştiricilerin daha iyi kod yazmasına yardımcı olacak ipuçları ve öneriler sağlamak için hafif bulbs kullanın

- Yeni dil desteğini etkinleştir

- Özel proje türü Ekle

- Visual Studio marketi aracılığıyla milyonlarca geliştiriciye ulaşın

  daha önce hiç bir Visual Studio uzantısı yazmadıysanız, bu özellikler hakkında daha fazla bilgi ve [Visual Studio uzantıları geliştirmeye başlarken](../extensibility/starting-to-develop-visual-studio-extensions.md)hakkında daha fazla bilgi bulmanız gerekir.

## <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme
 Visual Studio SDK Visual Studio kurulum 'da isteğe bağlı bir özelliktir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-sdk"></a>Visual Studio SDK 'daki yenilikler
 Visual Studio SDK, zaman uyumlu olarak yüklenen uzantılar uyarısı ve vsıx v3 biçiminin yanı sıra uzantınızı güncelleştirmenizi gerektirebilecek değişiklikler gibi bazı yeni özelliklere sahiptir. daha fazla bilgi için, bkz. [Visual Studio 2019 sdk 'daki](../extensibility/whats-new-visual-studio-2019-sdk.md) yenilikler ve [Visual Studio 2017 sdk 'daki](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)yenilikler.

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio kullanıcı deneyimi yönergeleri
 [Visual Studio kullanıcı deneyimi yönergeleri](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)' nde uzantınızın kullanıcı arabirimini tasarlamak için harika ipuçları alın.

 Ayrıca, uzantınızın, [Adres DPI sorunları](../extensibility/addressing-dpi-issues2.md) MAKALESINDE yüksek DPI cihazlarda harika görünmesini nasıl sağlayabileceğinizi de öğrenebilirsiniz.

 Harika görüntü yönetimi ve yüksek DPı ve tema desteği için [görüntü hizmetinden ve katalogdan](../extensibility/image-service-and-catalog.md) yararlanın.

## <a name="find-and-install-existing-visual-studio-extensions"></a>mevcut Visual Studio uzantılarını bul ve kur
 **araçlar** menüsünde **uzantılar ve güncelleştirmeler** iletişim kutusunda Visual Studio uzantıları bulabilirsiniz. daha fazla bilgi için bkz. [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md). [Visual Studio marketi](https://marketplace.visualstudio.com/) 'nde de uzantıları bulabilirsiniz

## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK başvurusu
 Visual Studio sdk apı başvurusunu [Visual Studio sdk başvurusunda](../extensibility/visual-studio-sdk-reference.md)bulabilirsiniz.

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK örnekleri
 GitHub vs SDK uzantılarının açık kaynak örneklerini [Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples)örneklerde bulabilirsiniz. bu GitHub deposu, Visual Studio çeşitli genişletilebilir özellikleri gösteren örnekler içerir.

## <a name="other-visual-studio-sdk-resources"></a>diğer Visual Studio SDK kaynakları
 vssdk hakkında sorularınız varsa veya deneyim geliştirme uzantılarınızı paylaşmak istiyorsanız, [Visual Studio genişletilebilirlik forumu](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) veya [extendvs Gitter Chatroom](https://gitter.im/Microsoft/extendvs)kullanabilirsiniz.

 [VSX Arcana bloguna](/archive/blogs/vsx/) daha fazla bilgi ve Microsoft MVP 'leri tarafından yazılmış çok sayıda blog bulabilirsiniz:

- [sık kullanılan Visual Studio uzantıları](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Visual Studio genişletilebilirliği](http://www.visualstudioextensibility.com/overview/vs/)

- [Visual Studio genişletme](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Ayrıca bkz.

- [Menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)
- [nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017 'ye geçirme](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [SSS: eklentileri VSPackage uzantılarına dönüştürme](/previous-versions/visualstudio/visual-studio-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions?preserve-view=true&view=vs-2015)
- [Yönetilen kodda birden çok iş parçacığını yönetme](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Menüleri ve komutları Genişlet](../extensibility/extending-menus-and-commands.md)
- [Araç çubuklarına komut ekleme](../extensibility/adding-commands-to-toolbars.md)
- [Araç pencerelerini genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)
- [Düzenleyici ve dil hizmeti uzantıları](../extensibility/editor-and-language-service-extensions.md)
- [Projeleri genişletme](../extensibility/extending-projects.md)
- [Kullanıcı ayarlarını ve seçeneklerini genişletme](../extensibility/extending-user-settings-and-options.md)
- [Özel proje ve öğe şablonları oluşturma](../extensibility/creating-custom-project-and-item-templates.md)
- [Özellikleri ve özellik penceresini genişletme](../extensibility/extending-properties-and-the-property-window.md)
- [Visual Studio diğer kısımlarını uzat](../extensibility/extending-other-parts-of-visual-studio.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
- [VSPackage’ları Yönetme](../extensibility/managing-vspackages.md)
- [yalıtılmış Visual Studio kabuğu](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Visual Studio uzantılarını gönder](../extensibility/shipping-visual-studio-extensions.md)
- [Visual Studio SDK’nın İçinde](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Visual Studio SDK Desteği](../extensibility/support-for-the-visual-studio-sdk.md)
- [Visual Studio SDK başvurusu](../extensibility/visual-studio-sdk-reference.md)