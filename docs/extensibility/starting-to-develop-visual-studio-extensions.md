---
title: Visual Studio uzantıları geliştirmeye başlama | Microsoft Docs
description: Visual Studio uzantısı yazmaya ilk kez başladığınızda kullanabileceğiniz bazı yaygın sorulardan bazıları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: da8bd850413d32e5453b7dc312e863832e5f5218
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715268"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio Uzantıları Geliştirmeye Başlama

Daha önce hiç bir Visual Studio uzantısı yazmadıysanız büyük olasılıkla bazı sorularınız olabilir. En yaygın olanlardan bazılarını burada listeliyoruz. Aradığınız bilgileri görmüyorsanız, istediğiniz şeyi sormak için geri bildirim düğmelerini kullanın (ekranın sağ üst kısmında **Bu sayfa yardımcı** olur).

> [!NOTE]
> Bu makale Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [genişletme Mac için Visual Studio](/visualstudio/mac/extending-visual-studio-mac). Visual Studio Code için, bkz. [Visual Studio Code uzantı API 'si](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Visual Studio uzantıları geliştirmem gereken yazılımlar nelerdir?

Visual Studio uzantıları geliştirmek için Visual Studio 'nun yanı sıra Visual Studio SDK 'sını yüklemeniz gerekir. Visual Studio SDK 'sını düzenli kurulum 'un bir parçası olarak yükleyebilir veya daha sonra yükleyebilirsiniz. Visual Studio SDK 'yı yükleme hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Visual Studio uzantılarıyla ne tür şeyler yapabilirim?

Çatka, farklı Visual Studio uzantıları görüntüsü oluşturma sırasında olduğu zaman sınırlıdır. Kuşkusuz, çoğu uzantının kod yazmak için bir şey vardır, ancak böyle bir durum olması gerekmez. Oluşturabileceğiniz uzantı türlerine ilişkin bazı örnekler aşağıda verilmiştir:

- Visual Studio 'da bulunmayan ve sözdizimi renklendirme, IntelliSense ve derleyici ve hata ayıklama desteği içeren diller için destek

- Ek şablonlar, kod yeniden düzenleme, yeni iletişimler veya araç pencereleri ile temel IDE deneyimini genişleten üretkenlik araçları

- Veri tasarımı veya bulut desteği gibi senaryolar için etki alanına özgü tasarımcılar

Uzantı örnekleri için [Visual Studio Market](https://marketplace.visualstudio.com/vs)inceleyin. Birçok uzantı açık kaynak olarak açıktır ve Market, GitHub depolarına bağlantılar içerir.

## <a name="which-visual-studio-features-can-i-extend"></a>Hangi Visual Studio özelliklerini genişletebilirim?

Teorik olarak, yalnızca Visual Studio 'nun herhangi bir bölümünü genişletebilirsiniz: menüler, araç çubukları, komutlar, pencereler, çözümler, projeler, düzenleyiciler vb.

Uygulamada, en çok kişilerin genişletmek istediği özelliklerin komutlar, menüler ve araç çubukları, Windows, IntelliSense ve projeler olduğunu bulduk. İlgili bölümlerin bağlantıları aşağıda verilmiştir:

- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md): Visual Studio menülerine ve araç çubuklarına kendi öğelerinizi ekleyin. Bunları, yeni Visual Studio işlevselliği veya kendi dış yardımcı uygulamalarınızı başlatmak için kullanabilirsiniz. Menü öğeleriniz için özel kısayollar da sağlayabilirsiniz.

- [Araç pencerelerini genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md): var olan araç pencerelerini genişletme veya kendi araç pencerelerini oluşturma. Örneğin, **özelliklere** yeni özellikler ekleyebilir veya ek özellikler eklemek için yeni bir araç penceresi oluşturabilirsiniz.

- [Düzenleyici ve dil hizmeti uzantıları](../extensibility/editor-and-language-service-extensions.md): Visual Studio dilleri Için sunulan IntelliSense 'e kendi özelleştirmelerinizi ekleyin veya yeni programlama dilleri için destek oluşturun. Tamamlama, öneriler ve yeni hızlı bilgi araç ipuçları oluşturabilirsiniz. Hafif bulbs sayesinde, yeni programlama dillerini desteklemek için yeniden düzenleme önerileri ve kod düzeltmeleri ekleyebilirsiniz.

- [Projeleri Genişletme](../extensibility/extending-projects.md)

- [Kullanıcı Ayarlarını ve Seçeneklerini Genişletme](../extensibility/extending-user-settings-and-options.md)

- [Özellikleri ve Özellik Penceresini Genişletme](../extensibility/extending-properties-and-the-property-window.md)

- [Visual Studio’nun Diğer Bölümlerini Genişletme](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Yalıtılmış Kabuğu](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> VSSDK tarafından hangi proje şablonları sağlanmaktadır?
 İki ana uzantı türü VSPackages ve MEF uzantılarıdır. Genel olarak, VSPackage uzantıları, komutları, araç pencerelerini ve projeleri kullanan veya genişleten uzantılar için kullanılır. MEF uzantıları, Visual Studio Düzenleyicisi 'ni genişletmek veya özelleştirmek için kullanılır.

 Visual C# ve Visual Basic uzantıları için, VSSDK, menü komutları, araç pencereleri ve Düzenleyici uzantıları oluşturan yeni öğe şablonlarıyla birlikte kullanabileceğiniz boş bir VSıX proje şablonu sağlar. Bu şablonu, diğer kullanıcılara dağıtmak üzere proje şablonlarını, kod parçacıklarını ve diğer yapıtları paketlemek için de kullanabilirsiniz.

 C++ için VSPackage Sihirbazı, menü komutları, araç pencereleri ve özel düzenleyiciler eklemek için kod sağlar.

 Yalıtılmış Kabuk şablonu, Visual Studio Kabuğu 'nun kendi marka ve dağıtabileceğiniz bir sürümünde bir uzantıyı paketlemek için kullanılır. Aşağıdaki konularda her bir uzantı türüyle nasıl başlacağınız gösterilmektedir:

- Menü komutları: [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

- Araç pencereleri: [bir araç penceresi Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)

- Düzenleyici uzantıları: [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Temel VSPackages: [VSPackage Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSıX proje şablonu: [VSIX proje şablonu Ile çalışmaya](../extensibility/getting-started-with-the-vsix-project-template.md) başlama

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Nasıl yaparım? uzantısı Visual Studio gibi görünüyor.
 [Visual Studio Kullanıcı deneyimi kılavuzlarından](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)UZANTıNıZıN Kullanıcı arabirimini tasarlamak için harika ipuçları alın.

## <a name="where-can-i-find-examples-of-vssdk-code"></a>VSSDK kodu örneklerini nerede bulabilirim?
 Yukarıdaki bölümde listelenen bağlantıların her biri, belirli özelliklerin nasıl uygulanacağını gösteren adım adım izlenecek yollara sahiptir. Ayrıca, [Visual Studio örneklerinde](https://github.com/Microsoft/VSSDK-Extensibility-Samples)GitHub üzerinde açık kaynak VSSDK örnekleri bulabilirsiniz.

## <a name="how-can-i-distribute-my-extension"></a>Uzantımı nasıl dağıtabilirim?
 Uzantınızı başka bir bilgisayara yükleyebilir veya bir. vsix dosyası olarak arkadaşlarınıza gönderebilirsiniz ve bu dosyayı çift tıklayarak yükleyebilirsiniz. VSıX paketleri hakkında daha fazla bilgi edinmek için bkz. [Visual Studio uzantılarını aktarma](../extensibility/shipping-visual-studio-extensions.md).

 Uzantınızı Visual Studio Market de yayımlayabilirsiniz. Bu, çok sayıda Visual Studio müşterilerinin görünmesini sağlar. Market 'e uzantı paketleme örneği için bkz. [Izlenecek yol: Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Market 'te yayımlamak için yapmanız gerekenler hakkında daha fazla bilgi için bkz. [Visual Studio Için ürünler ve uzantılar](/azure/devops/extend/overview?view=vsts&preserve-view=true).

## <a name="see-also"></a>Ayrıca bkz.

- [Mac için Visual Studio’yu Genişletme](/visualstudio/mac/extending-visual-studio-mac)
- [Visual Studio Code genişletme](https://code.visualstudio.com/api)