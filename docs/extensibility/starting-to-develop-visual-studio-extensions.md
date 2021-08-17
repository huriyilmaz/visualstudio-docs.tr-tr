---
title: Visual Studio uzantıları geliştirmeye başlama | Microsoft Docs
description: Visual Studio uzantısını yazmaya ilk kez başladığınızda kullanabileceğiniz bazı yaygın sorulardan bazıları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 260ae4b71d7eb7bed3ac97faa3d0ccf90665f90a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049460"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio Uzantıları Geliştirmeye Başlama

daha önce hiç bir Visual Studio uzantısı yazmadıysanız büyük olasılıkla bazı sorularınız olabilir. En yaygın olanlardan bazılarını burada listeliyoruz. Aradığınız bilgileri görmüyorsanız, istediğiniz şeyi sormak için geri bildirim düğmelerini kullanın (ekranın sağ üst kısmında **Bu sayfa yardımcı** olur).

> [!NOTE]
> bu makale Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [genişletme Mac için Visual Studio](/visualstudio/mac/extending-visual-studio-mac). Visual Studio Code için, bkz. [Visual Studio Code uzantı apı 'si](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Visual Studio uzantıları geliştirmem gereken yazılımlar nelerdir?

Visual Studio uzantıları geliştirmek için Visual Studio ek olarak Visual Studio SDK yüklemeniz gerekir. Visual Studio SDK 'sını düzenli kurulum 'un bir parçası olarak yükleyebilir veya daha sonra yükleyebilirsiniz. Visual Studio sdk 'yı yükleme hakkında daha fazla bilgi için bkz. [Visual Studio sdk 'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Visual Studio uzantılarıyla ne tür şeyler yapabilirim?

sky, farklı Visual Studio uzantılarına sahip olduğunda bu sınır daha fazla. Kuşkusuz, çoğu uzantının kod yazmak için bir şey vardır, ancak böyle bir durum olması gerekmez. Oluşturabileceğiniz uzantı türlerine ilişkin bazı örnekler aşağıda verilmiştir:

- sözdizimi renklendirme, ıntellisense ve derleyici ve hata ayıklama desteğiyle Visual Studio dahil olmayan diller için destek

- Ek şablonlar, kod yeniden düzenleme, yeni iletişimler veya araç pencereleri ile temel IDE deneyimini genişleten üretkenlik araçları

- Veri tasarımı veya bulut desteği gibi senaryolar için etki alanına özgü tasarımcılar

uzantı örnekleri için [Visual Studio marketi](https://marketplace.visualstudio.com/vs)' ne göz atın. birçok uzantı açıktır ve market GitHub depoya bağlantılar içerir.

## <a name="which-visual-studio-features-can-i-extend"></a>hangi Visual Studio özellikleri genişletebilirim?

teorik olarak, Visual Studio: menülerin, araç çubuklarının, komutların, pencerelerin, çözümlerin, projelerin, düzenleyicilerin ve benzer herhangi bir bölümünü genişletebilirsiniz.

Uygulamada, en çok kişilerin genişletmek istediği özelliklerin komutlar, menüler ve araç çubukları, Windows, IntelliSense ve projeler olduğunu bulduk. İlgili bölümlerin bağlantıları aşağıda verilmiştir:

- [menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md): kendi öğelerinizi Visual Studio menülere ve araç çubuklarına ekleyin. bunları, yeni Visual Studio işlevselliği veya kendi dış yardımcı uygulamalarınızı başlatmak için kullanabilirsiniz. Menü öğeleriniz için özel kısayollar da sağlayabilirsiniz.

- [araç Windows genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md): var olan araç pencerelerini genişletin veya kendi araç pencerelerini oluşturun. Örneğin, **özelliklere** yeni özellikler ekleyebilir veya ek özellikler eklemek için yeni bir araç penceresi oluşturabilirsiniz.

- [düzenleyici ve dil hizmeti uzantıları](../extensibility/editor-and-language-service-extensions.md): Visual Studio dilleri için sunulan ıntellisense 'e kendi özelleştirmelerinizi ekleyin veya yeni programlama dilleri için destek oluşturun. Tamamlama, öneriler ve yeni hızlı bilgi araç ipuçları oluşturabilirsiniz. Hafif bulbs sayesinde, yeni programlama dillerini desteklemek için yeniden düzenleme önerileri ve kod düzeltmeleri ekleyebilirsiniz.

- [Projeleri Genişletme](../extensibility/extending-projects.md)

- [Kullanıcı Ayarlarını ve Seçeneklerini Genişletme](../extensibility/extending-user-settings-and-options.md)

- [Özellikleri ve Özellik Penceresini Genişletme](../extensibility/extending-properties-and-the-property-window.md)

- [Visual Studio’nun Diğer Bölümlerini Genişletme](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Yalıtılmış Kabuğu](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> VSSDK tarafından hangi proje şablonları sağlanmaktadır?
 İki ana uzantı türü VSPackages ve MEF uzantılarıdır. Genel olarak, VSPackage uzantıları, komutları, araç pencerelerini ve projeleri kullanan veya genişleten uzantılar için kullanılır. MEF uzantıları, Visual Studio düzenleyicisini genişletmek veya özelleştirmek için kullanılır.

 Visual C# ve Visual Basic uzantıları için, vssdk, menü komutları, araç pencereleri ve düzenleyici uzantıları oluşturan yeni öğe şablonlarıyla birlikte kullanabileceğiniz boş bir vsıx proje şablonu sağlar. Bu şablonu, diğer kullanıcılara dağıtmak üzere proje şablonlarını, kod parçacıklarını ve diğer yapıtları paketlemek için de kullanabilirsiniz.

 C++ için VSPackage Sihirbazı, menü komutları, araç pencereleri ve özel düzenleyiciler eklemek için kod sağlar.

 yalıtılmış kabuk şablonu, bir uzantıyı kendi marka ve dağıtabileceğiniz bir Visual Studio kabuğu sürümünde paketlemek için kullanılır. Aşağıdaki konularda her bir uzantı türüyle nasıl başlacağınız gösterilmektedir:

- Menü komutları: [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

- Araç pencereleri: [bir araç penceresi Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)

- Düzenleyici uzantıları: [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Temel VSPackages: [VSPackage Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

- vsıx proje şablonu: [vsıx Project şablonuyla çalışmaya](../extensibility/getting-started-with-the-vsix-project-template.md) başlama

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Nasıl yaparım? Visual Studio gibi görünmesi için Uzantımı al?
 [Visual Studio kullanıcı deneyimi yönergeleri](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)' nde uzantınızın kullanıcı arabirimini tasarlamak için harika ipuçları alın.

## <a name="where-can-i-find-examples-of-vssdk-code"></a>VSSDK kodu örneklerini nerede bulabilirim?
 Yukarıdaki bölümde listelenen bağlantıların her biri, belirli özelliklerin nasıl uygulanacağını gösteren adım adım izlenecek yollara sahiptir. ayrıca, [Visual Studio örneklerde](https://github.com/Microsoft/VSSDK-Extensibility-Samples)GitHub açık kaynak vssdk örnekleri de bulabilirsiniz.

## <a name="how-can-i-distribute-my-extension"></a>Uzantımı nasıl dağıtabilirim?
 Uzantınızı başka bir bilgisayara yükleyebilir veya bir. vsix dosyası olarak arkadaşlarınıza gönderebilirsiniz ve bu dosyayı çift tıklayarak yükleyebilirsiniz. [Visual Studio uzantılarında](../extensibility/shipping-visual-studio-extensions.md)vsıx paketleri hakkında daha fazla bilgi edinebilirsiniz.

 uzantınızı Visual Studio marketi üzerinde yayınlayabilirsiniz ve bu da çok sayıda Visual Studio müşterinin görünmesini sağlar. market 'e uzantı paketleme örneği için bkz. [izlenecek yol: Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Market 'te yayımlamak için yapmanız gerekenler hakkında daha fazla bilgi için, bkz. [Visual Studio ürünleri ve uzantıları](/azure/devops/extend/overview?view=vsts&preserve-view=true).

## <a name="see-also"></a>Ayrıca bkz.

- [Mac için Visual Studio’yu Genişletme](/visualstudio/mac/extending-visual-studio-mac)
- [Visual Studio Code genişletme](https://code.visualstudio.com/api)