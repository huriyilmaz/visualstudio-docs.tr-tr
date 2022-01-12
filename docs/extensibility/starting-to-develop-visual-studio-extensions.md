---
title: Visual Studio Uzantıları Geliştirmeye | Microsoft Docs
description: İlk kez bir uzantıyı ilk kez yazmaya başiden sık sorulan bazı Visual Studio öğrenin.
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
ms.openlocfilehash: 2680cfd241f1b72a34b853eaef2763063a93793e
ms.sourcegitcommit: 3972b1af15930a73d79482e798154f0417a68593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "135649834"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio Uzantıları Geliştirmeye Başlama

Daha önce bir uzantı Visual Studio yazmadıysanız, büyük olasılıkla bazı sorularınız vardır. Burada en yaygın olanlardan bazıları listelenmiştir. Istediğiniz bilgileri görmüyorsanız geri bildirim düğmelerini (Bu sayfa yararlı **mı?** Ekranın sağ üst köşesindeki) kullanarak istediğiniz bilgileri sorabilirsiniz.

> [!NOTE]
> Bu makale, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/previous-versions/visualstudio/mac/extending-visual-studio-mac-walkthrough) Daha Visual Studio Code için [bkz. Visual Studio Code API'si.](https://code.visualstudio.com/api)

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Yeni uzantılar geliştirmek için hangi Visual Studio gerekir?

Yeni uzantılar geliştirmek için Visual Studio SDK'Visual Studio ek olarak Visual Studio gerekir. Visual Studio SDK'yı normal kurulumun bir parçası olarak yükleyebilir veya daha sonra yükleyebilirsiniz. Visual Studio SDK'yı yükleme hakkında daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Uzantılarla ne tür Visual Studio yapabilirim?

Farklı uzantılar hayal etmek söz konusu olduğunda Visual Studio. Elbette çoğu uzantının kod yazmakla bir ilgisi vardır ancak bu durum böyle olması gerek değildir. Aşağıda, bazı uzantı türlerine örnek olarak verilmiştir:

- Söz dizimi renklendirme, IntelliSense ve derleyici ve hata ayıklama desteğiyle Visual Studio'ye dahil olmayan diller için destek

- Ek şablonlar, kod yeniden düzenleme, yeni iletişim kutuları veya araç pencereleri ile çekirdek IDE deneyimini genişleten üretkenlik araçları

- Veri tasarımı veya bulut desteği gibi senaryolar için etki alanına özgü tasarımcılar

Uzantı örnekleri için Market'te [Visual Studio bakın.](https://marketplace.visualstudio.com/vs) Birçok uzantı açık kaynaklıdır ve Market, kendi kaynak kaynak GitHub içerir.

## <a name="which-visual-studio-features-can-i-extend"></a>Hangi Visual Studio hangi özellikleri genişlet bilmiyorum?

Teoride, menüler, araç Visual Studio, komutlar, pencereler, çözümler, projeler, düzenleyiciler ve diğer tüm öğeleri genişletebilirsiniz.

Uygulamada, çoğu kişinin genişletmek istediğiniz özelliklerin komutlar, menüler ve araç çubukları, pencereler, IntelliSense ve projeler olduğunu bulduk. İlgili bölümlerin bağlantıları şu şekildedir:

- [Menüleri ve Komutları Genişletme:](../extensibility/extending-menus-and-commands.md)Menülere ve araç çubuklarına Visual Studio öğelerinizi ekleyin. Bu işlevleri kullanarak yeni bir Visual Studio veya kendi dış yardımcı uygulamalarınızı başlatabilirsiniz. Menü öğeleriniz için özel kısayollar da sekleyebilirsiniz.

- [Aracı Genişletme ve Özelleştirme Windows:](../extensibility/extending-and-customizing-tool-windows.md)mevcut araç pencerelerini genişletme veya kendi araç pencerelerinizi oluşturma. Örneğin, Özellikler'e yeni özellikler **ekleyebilir** veya ek özellikler eklemek için yeni bir araç penceresi oluşturabilirsiniz.

- [Düzenleyici ve Dil Hizmeti Uzantıları:](../extensibility/editor-and-language-service-extensions.md)Kendi özelleştirmelerinizi, Visual Studio için sağlanan IntelliSense'e ekleyin veya yeni programlama dilleri için destek oluşturun. Yeni deyim tamamlamaları, öneriler ve yeni QuickInfo araç ipucu oluşturabilirsiniz. Ampullerle, yeni programlama dillerini desteklemek için yeniden düzenleme önerileri ve kod düzeltmeleri ebilirsiniz.

- [Projeleri Genişletme](../extensibility/extending-projects.md)

- [Kullanıcı Ayarlarını ve Seçeneklerini Genişletme](../extensibility/extending-user-settings-and-options.md)

- [Özellikleri ve Özellik Penceresini Genişletme](../extensibility/extending-properties-and-the-property-window.md)

- [Visual Studio’nun Diğer Bölümlerini Genişletme](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Yalıtılmış Kabuğu](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> VSSDK hangi proje şablonlarını sağlar?
 İki ana uzantı türü VSPackage'lar ve MEF uzantılarıdır. VsPackage uzantıları genel olarak komutları, araç pencerelerini ve projeleri kullanan veya genişleten uzantılar için kullanılır. MEF uzantıları, düzenleyiciyi genişletmek veya özelleştirmek Visual Studio kullanılır.

 Visual C# ve Visual Basic uzantıları için VSSDK, menü komutları, araç pencereleri ve düzenleyici uzantıları oluşturan yeni öğe şablonlarıyla birlikte kullanabileceğiniz boş bir VSIX proje şablonu sağlar. Bu şablonu ayrıca proje şablonlarını, kod parçacıklarını ve diğer kullanıcılara dağıtım için diğer yapıtları paketleyebilirsiniz.

 C++ için VSPackage sihirbazı menü komutları, araç pencereleri ve özel düzenleyiciler ekleme kodunu sağlar.

 Yalıtılmış Kabuk şablonu, bir uzantıyı Visual Studio olarak markalandırarak dağıtabilirsiniz. Aşağıdaki konularda, her tür uzantıyı nasıl başlatabilirsiniz?

- Menü komutları: [Menü Komutuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

- Araç pencereleri: [Araç Penceresi ile Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md)

- Düzenleyici uzantıları: [Düzenleyici Öğesi Şablonu ile Uzantı Oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Temel [VSPackage'lar: VSPackage ile Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX proje şablonu: [VSIX Başlarken Şablonu ile Project oluşturma](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Nasıl yaparım? gibi mi Visual Studio?
 kullanıcı deneyimi yönergelerinde uzantınız için kullanıcı arabirimini [tasarlamaya Visual Studio ipuçları elde edin.](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="where-can-i-find-examples-of-vssdk-code"></a>VSSDK kodu örneklerini nerede bulamıyorum?
 Önceki bölümde listelenen bağlantıların her biri, belirli özellikleri uygulama adım adım izlenecek yollara sahiptir. Açık kaynak VSSDK örneklerini GitHub Visual Studio [bulabilirsiniz.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="how-can-i-distribute-my-extension"></a>Uzantımı nasıl dağıt olabilirim?
 Uzantınızı başka bir bilgisayara yükleyebilir veya çift tıklayarak .vsix dosyası olarak arkadaşlarınıza gönderebilirsiniz. VSIX paketleri hakkında daha fazla bilgi için shipping [Visual Studio bulabilirsiniz.](../extensibility/shipping-visual-studio-extensions.md)

 Ayrıca uzantınızı Visual Studio Market'te yayımlayın. Bu sayede çok sayıda müşteri Visual Studio görünür hale gelir. Market'te bir uzantıyı paketleme örneği için bkz. Adım adım: Visual Studio [Yayımlama.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md) Market'te yayımlamak için neleri ihtiyacınız olduğu hakkında daha fazla bilgi için [bkz.](/azure/devops/extend/overview?view=vsts&preserve-view=true)Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.

- [Mac için Visual Studio’yu Genişletme](/previous-versions/visualstudio/mac/extending-visual-studio-mac-walkthrough)
- [Genişletme Visual Studio Code](https://code.visualstudio.com/api)
