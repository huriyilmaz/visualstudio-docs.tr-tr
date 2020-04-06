---
title: Görsel Stüdyo SDK | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698069"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK, Visual Studio özelliklerini genişletmenize veya yeni özellikleri Visual Studio'ya entegre edinmenize yardımcı olur. Uzantılarınızı diğer kullanıcılara ve Visual Studio Marketplace'e dağıtabilirsiniz. Visual Studio'yu genişletme yollarından bazıları şunlardır:

- IDE'ye komutlar, düğmeler, menüler ve diğer UI öğeleri ekleme

- Yeni işlevler için araç pencereleri ekleme

- Belirli bir dil için IntelliSense'i genişletin veya yeni programlama dilleri için IntelliSense sağlayın

- Geliştiricilerin daha iyi kod yazmalarına yardımcı olacak ipuçları ve öneriler sağlamak için ampulleri kullanın

- Yeni bir dil için desteği etkinleştirme

- Özel proje türü ekleme

- Visual Studio Marketplace aracılığıyla milyonlarca geliştiriciye ulaşın

  Daha önce hiç Visual Studio uzantısı yazmadıysanız, bu özellikler hakkında daha fazla bilgi edinmeli ve [Visual Studio uzantılarını geliştirmeye başlarsınız.](../extensibility/starting-to-develop-visual-studio-extensions.md)

## <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme
 Visual Studio SDK, Visual Studio kurulumunda isteğe bağlı bir özelliktir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Visual Studio 2017 SDK'daki yenilikler
 Visual Studio SDK, VSIX v3 formatı gibi bazı yeni özelliklere ve uzantınızı güncellemenizi gerektirebilecek değişiklikleri kırmaya sahiptir. Daha fazla bilgi için [Visual Studio 2017 SDK'daki yeniliklere](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)bakın.

## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio kullanıcı deneyimi yönergeleri
 [Visual Studio kullanıcı deneyimi yönergeleriniz](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)için kullanıcı arabirimi tasarımı için harika ipuçları alın.

 [Ayrıca, Adres DPI sorunları](../extensibility/addressing-dpi-issues2.md) makalesi yle uzantınızın yüksek DPI aygıtlarında nasıl harika görünebileceğini de öğrenebilirsiniz.

 Yüksek DPI ve temalı için mükemmel görüntü yönetimi ve destek için Görüntü hizmeti ve [kataloğundan](../extensibility/image-service-and-catalog.md) yararlanın.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Varolan Visual Studio uzantılarını bulma ve yükleme
 **Araçlar** menüsünde **Uzantılar ve Güncelleştirmeler** iletişim kutusunda Visual Studio uzantılarını bulabilirsiniz. Daha fazla bilgi için [Visual Studio Uzantılarını Bul ve Kullan'](../ide/finding-and-using-visual-studio-extensions.md)a bakın. Ayrıca [Visual Studio Marketplace](https://marketplace.visualstudio.com/) uzantıları bulabilirsiniz

## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK referans
 Visual Studio SDK API referansını [Visual Studio SDK Reference](../extensibility/visual-studio-sdk-reference.md)adresinde bulabilirsiniz.

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK örnekleri
 GitHub'da VS SDK uzantılarının açık kaynak örneklerini [Visual Studio Samples'te](https://github.com/Microsoft/VSSDK-Extensibility-Samples)bulabilirsiniz. Bu GitHub repo Visual Studio çeşitli genişletilebilir özellikleri göstermek örnekleri içerir.

## <a name="other-visual-studio-sdk-resources"></a>Diğer Visual Studio SDK kaynakları
 VSSDK hakkında sorularınız varsa veya uzantılar geliştiren deneyimlerinizi paylaşmak istiyorsanız, [Visual Studio Genişletilebilirlik Forumu'nu](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) veya [ExtendVS Gitter Sohbet Odası'nı](https://gitter.im/Microsoft/extendvs)kullanabilirsiniz.

 [Sen VSX Arcana blog](https://blogs.msdn.microsoft.com/vsx/) ve Microsoft MVPs tarafından yazılmış bloglar bir dizi daha fazla bilgi bulabilirsiniz:

- [Favori Visual Studio uzantıları](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Visual Studio genişletilebilirlik](http://www.visualstudioextensibility.com/overview/vs/)

- [Görsel Stüdyogenişletme](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Ayrıca bkz.

- [Menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Nasıl Yapılır: Genişletilebilirlik projelerini Visual Studio 2017'ye geçirin](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [SSS: Eklentileri VSPackage uzantılarına dönüştürme](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Yönetilen kodda birden çok iş parçacığı yönetme](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [Araç çubuklarına komut ekleme](../extensibility/adding-commands-to-toolbars.md)
- [Araç pencerelerini genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)
- [Editör ve dil hizmeti uzantıları](../extensibility/editor-and-language-service-extensions.md)
- [Projeleri genişletme](../extensibility/extending-projects.md)
- [Kullanıcı ayarlarını ve seçeneklerini genişletme](../extensibility/extending-user-settings-and-options.md)
- [Özel proje ve öğe şablonları oluşturma](../extensibility/creating-custom-project-and-item-templates.md)
- [Özellikleri ve özellik penceresini genişletme](../extensibility/extending-properties-and-the-property-window.md)
- [Visual Studio'nun diğer bölümlerini genişletin](../extensibility/extending-other-parts-of-visual-studio.md)
- [Kullanım ve hizmet sağlama](../extensibility/using-and-providing-services.md)
- [VSPackage’ları Yönetme](../extensibility/managing-vspackages.md)
- [Visual Studio izole kabuk](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Gemi Görsel Stüdyo uzantıları](../extensibility/shipping-visual-studio-extensions.md)
- [Visual Studio SDK’nın İçinde](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Visual Studio SDK Desteği](../extensibility/support-for-the-visual-studio-sdk.md)
- [Visual Studio SDK referans](../extensibility/visual-studio-sdk-reference.md)
