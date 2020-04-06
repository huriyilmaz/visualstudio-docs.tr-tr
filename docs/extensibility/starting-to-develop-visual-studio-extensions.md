---
title: Visual Studio Uzantıları Geliştirmeye Başlarken | Microsoft Dokümanlar
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699734"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio Uzantıları Geliştirmeye Başlama

Daha önce hiç Visual Studio uzantısı yazmadıysanız, muhtemelen bazı sorularınız vardır. Burada en yaygın olanları listeledik. Aradığınız bilgileri görmüyorsanız, ne istediğinizi sormak için geri bildirim düğmelerini **(bu sayfa yararlı oldu mu?** ekranın alt kısmında) kullanın.

> [!NOTE]
> Bu makale, Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Genişletme Visual Studio'ya](/visualstudio/mac/extending-visual-studio-mac)bakın. Visual Studio Code için [Visual Studio Code Extension API'ye](https://code.visualstudio.com/api)bakın.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Visual Studio uzantılarını geliştirmek için hangi yazılıma ihtiyacım var?

Visual Studio uzantıları nı geliştirmek için Visual Studio'ya ek olarak Visual Studio SDK'yı da yüklemeniz gerekir. Visual Studio SDK'yı düzenli kurulumun bir parçası olarak yükleyebilir veya daha sonra yükleyebilirsiniz. Visual Studio SDK yükleme hakkında daha fazla bilgi için Visual [Studio SDK](../extensibility/visual-studio-sdk.md)bakın.

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Visual Studio uzantılarıyla ne tür şeyler yapabilirim?

Farklı Visual Studio uzantıları hayal söz konusu olduğunda gökyüzü sınırıdır. Tabii ki, en uzantıları kod yazma ile ilgili bir şey var, ama bu durumda olmak zorunda değildir. Oluşturabileceğiniz uzantı türlerine bazı örnekler aşağıda verilmiştir:

- Sözdizimi boyama, IntelliSense ve derleyici ve hata ayıklama desteği ile Visual Studio'da yer almayan diller için destek

- Ek şablonlar, kod yeniden düzenleme, yeni iletişim kutuları veya araç pencereleri ile çekirdek IDE deneyimini genişleten üretkenlik araçları

- Veri tasarımı veya bulut desteği gibi senaryolar için etki alanına özel tasarımcılar

Uzantı örnekleri için Visual [Studio Marketplace'e](https://marketplace.visualstudio.com/vs)göz atın. Birçok uzantıları açık kaynaklı ve Market onların GitHub repo bağlantılar içerir.

## <a name="which-visual-studio-features-can-i-extend"></a>Hangi Visual Studio özelliklerini genişletebilirim?

Teorik olarak, Visual Studio'nun hemen hemen her bölümünü genişletebilirsiniz: menüler, araç çubukları, komutlar, pencereler, çözümler, projeler, editörler ve benzeri.

Uygulamada, çoğu insanın genişletmek istediği özelliklerin komutlar, menüler ve araç çubukları, pencereler, IntelliSense ve projeler olduğunu gördük. Burada ilgili bölümlere bağlantılar şunlardır:

- [Menüleri ve Komutları Genişletme](../extensibility/extending-menus-and-commands.md): Visual Studio menülerine ve araç çubuklarına kendi öğelerinizi ekleyin. Bunları yeni Visual Studio işlevselliğini veya kendi harici yardımcı uygulamalarınızı başlatmak için kullanabilirsiniz. Menü öğeleriniz için özel kısayollar da sağlayabilirsiniz.

- [Araç Windows'u Genişletme ve Özelleştirme](../extensibility/extending-and-customizing-tool-windows.md): varolan araç pencerelerini genişletin veya kendi araç pencerelerinizi oluşturun. Örneğin, **Özellikler'e**yeni özellikler ekleyebilir veya ek özellikler eklemek için yeni bir araç penceresi oluşturabilirsiniz.

- [Editör ve Dil Hizmeti Uzantıları](../extensibility/editor-and-language-service-extensions.md): Visual Studio dilleri için sağlanan IntelliSense'e kendi özelleştirmelerinizi ekleyin veya yeni programlama dilleri için destek oluşturun. Yeni ekstre tamamlamaları, öneriler ve yeni QuickInfo araç ipuçları oluşturabilirsiniz. Ampullerle, yeni programlama dillerini desteklemek için yeniden düzenleme önerileri ve kod düzeltmeleri ekleyebilirsiniz.

- [Projeleri Genişletme](../extensibility/extending-projects.md)

- [Kullanıcı Ayarlarını ve Seçeneklerini Genişletme](../extensibility/extending-user-settings-and-options.md)

- [Özellikleri ve Özellik Penceresini Genişletme](../extensibility/extending-properties-and-the-property-window.md)

- [Visual Studio’nun Diğer Bölümlerini Genişletme](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Yalıtılmış Kabuğu](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>VSSDK tarafından hangi proje şablonları sağlanır?
 İki ana uzantı türü VSPackages ve MEF uzantılarıdır. Genel olarak, VSPackage uzantıları komutları, araç pencerelerini ve projeleri kullanan veya genişleten uzantılar için kullanılır. MEF uzantıları Visual Studio düzenleyicisini genişletmek veya özelleştirmek için kullanılır.

 Visual C# ve Visual Basic uzantıları için VSSDK, menü komutları, araç pencereleri ve düzenleyici uzantıları oluşturan yeni öğe şablonlarıyla birlikte kullanabileceğiniz boş bir VSIX proje şablonu sağlar. Proje şablonlarını, kod parçacıklarını ve diğer yapıları diğer kullanıcılara dağıtış için paketlemek için de bu şablonu kullanabilirsiniz.

 C++'da VSPackage sihirbazı menü komutları, araç pencereleri ve özel düzenleyiciler eklemek için kodu sağlar.

 İzole Kabuk şablonu, Visual Studio kabuğunun kendi sürümünüz olarak markalandırabileceğiniz ve dağıtabileceğiniz bir uzantısı paketlemek için kullanılır. Aşağıdaki konular, her tür uzantıyla nasıl başlaşabileceğinizi gösterir:

- Menü komutları: [Menü Komutu ile Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

- Araç pencereleri: [Araç Penceresi ile Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)

- Düzenleyici uzantıları: [Düzenleyici Öğe Şablonu yla Uzantı Oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Temel VSPackages: [VSPackage ile Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX proje şablonu: [VSIX Proje Şablonu ile Başlarken](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Uzantımın Visual Studio'ya benzemesini nasıl alabilirim?
 [Visual Studio Kullanıcı Deneyimi Yönergeleri'ndeki](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)uzantınız için kullanıcı arabirimi tasarımı için harika ipuçları alın.

## <a name="where-can-i-find-examples-of-vssdk-code"></a>VSSDK kodu örneklerini nerede bulabilirim?
 Önceki bölümde listelenen bağlantıların her birinde, belirli özellikleri nasıl uygulayacağınızı gösteren adım adım gözden geçirmeler vardır. Ayrıca [Görsel Stüdyo Örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples)github açık kaynak VSSDK örnekleri bulabilirsiniz.

## <a name="how-can-i-distribute-my-extension"></a>Uzantımı nasıl dağıtabilirim?
 Uzantınızı başka bir bilgisayara yükleyebilir veya çift tıklatarak yüklediğiniz .vsix dosyası olarak arkadaşlarınıza gönderebilirsiniz. [Sen Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md)vsix paketleri hakkında daha fazla bilgi edinebilirsiniz.

 Uzantınızı Visual Studio Marketplace'te de yayınlayabilirsiniz, bu da onu çok sayıda Visual Studio müşterisi tarafından görülebilir hale getirir. Marketin bir uzantısını paketleme kınağı örneği için Bkz. [Walkthrough: Visual Studio Extension Yayımlama.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) Markette yayınlamak için ne yapmanız gerektiği hakkında daha fazla bilgi için [Visual Studio için Ürünler ve Uzantılar'a](/azure/devops/extend/overview?view=vsts)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Mac için Visual Studio’yu Genişletme](/visualstudio/mac/extending-visual-studio-mac)
- [Görsel Stüdyo Kodunu Genişletme](https://code.visualstudio.com/api)
