---
title: Dil hizmeti ve Düzenleyici uzantıları ile çalışmaya başlama
description: dil hizmeti özelliklerini herhangi bir içerik türüne eklemeyi ve Visual Studio düzenleyicisinin görünümünü ve davranışını özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6ec5af209d9dc5c28c1c741058502b5be1b44000
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087164"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Dil hizmeti ve Düzenleyici uzantıları ile çalışmaya başlama

Ana hat, küme ayracı eşleştirme, IntelliSense ve hafif bulbs gibi dil hizmeti özelliklerini kendi programlama dilinize veya herhangi bir içerik türüne eklemek için düzenleyici uzantılarını kullanabilirsiniz. ayrıca, Visual Studio düzenleyicisinin görünümünü ve davranışını, örneğin metin renklendirme, kenar boşlukları, donnments ve diğer görsel öğeleri de özelleştirebilirsiniz. Ayrıca kendi içerik türünü tanımlayabilir ve içeriğinizin göründüğü metin görünümlerinin görünümünü ve davranışını belirtebilirsiniz.

 düzenleyici uzantıları yazmaya başlamak için Visual Studio SDK 'sının bir parçası olarak yüklenen düzenleyici proje şablonlarını kullanın. Visual Studio SDK, vspackages veya Managed Extensibility Framework (MEF) kullanarak Visual Studio uzantıları geliştirmeyi kolaylaştıran indirilebilir bir araç kümesidir.

> [!NOTE]
> Visual Studio sdk hakkında daha fazla bilgi için bkz. [Visual Studio sdk](../extensibility/visual-studio-sdk.md).

 Kendi düzenleyici uzantılarınızı yazmadan önce aşağıdaki kavramlar ve teknolojiler hakkında bilgi edinmenizi öneririz.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) ve düzenleyici uzantıları

 Visual Studio düzenleyicisi kullanıcı arabirimi (uı), Windows Presentation Foundation (WPF) kullanılarak uygulanır. WPF, iş mantığındaki kodun görsel yönlerini ayıran zengin bir görsel deneyim ve tutarlı bir programlama modeli sağlar. Düzenleyici uzantıları oluştururken birçok WPF öğesi ve özelliği kullanabilirsiniz. daha fazla bilgi için bkz. [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) ve düzenleyici uzantıları

 Visual Studio düzenleyicisi, bileşenlerini ve uzantılarını yönetmek için Managed Extensibility Framework (MEF) kullanır. MEF, geliştiricilerin Visual Studio gibi bir ana bilgisayar uygulaması için daha kolay uzantılar oluşturmasını da sağlar. Bu çerçevede bir MEF sözleşmesine göre uzantı tanımlar ve bir MEF bileşeni parçası olarak dışarı aktarabilirsiniz. Konak uygulaması, bileşen parçalarını onları bularak, kaydederek ve doğru bağlama uygulandığından emin olarak yönetir.

> [!NOTE]
> düzenleyicide MEF hakkında daha fazla bilgi için, bkz. [düzenleyicide Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio düzenleyici uzantı noktaları ve uzantıları

 Düzenleyici uzantı noktaları, özelleştirebileceğiniz ve genişletebilen MEF bileşen bölümleridir. Bazı durumlarda, bir arabirim uygulayarak ve doğru meta verilerle birlikte dışarı aktararak uzantı noktasını genişletebilirsiniz. Diğer durumlarda, yalnızca bir uzantı bildirip belirli bir tür olarak dışarı aktardınız.

 Aşağıdaki temel tür Düzenleyici genişletmeler şunlardır:

- Kenar boşlukları ve kaydırma çubukları

- Etiketler

- Satırdaki kenarlıkları

- Seçenekler

- IntelliSense

  Düzenleyici uzantı noktaları hakkında daha fazla bilgi için bkz. [dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Düzenleyici uzantılarını dağıtma

 Visual Studio, çözüme *kaynak. extension. valtmanifest* adlı bir meta veri dosyası ekleyerek, çözümü oluşturarak ve sonra ikili dosyaların ve bildirimin bir kopyasını Visual Studio olarak bilinen bir klasöre ekleyerek düzenleyici uzantıları dağıtırsınız. Bildirim dosyası, uzantıyla ilgili temel gerçekleri tanımlar (örneğin, ad, yazar, sürüm ve içerik türü). vsıx bildirim dosyası ve uzantıların nasıl dağıtılacağı hakkında daha fazla bilgi için bkz. dağıtım [Visual Studio uzantıları](../extensibility/shipping-visual-studio-extensions.md).

 Bir bilgisayara uzantı yüklediğinizde, ikili dosyaları ve bildirimi Visual Studio bilinen klasörün bir alt klasörüne ekleyin.

> [!WARNING]
> Visual Studio eklenen düzenleyici genişletilebilirlik şablonlarından birini kullanıyorsanız, bildirimlerin ve dağıtım konumlarının ayrıntıları konusunda endişelenmeniz gerekmez. Şablonlar, bir uzantıyı kaydetmek ve dağıtmak için gereken her şeyi içerir.

## <a name="run-extensions-in-the-experimental-instance"></a>Deneysel örnekte uzantıları çalıştırma

 bir uzantıyı aşağıdaki deneysel klasöre dağıtarak (Windows Vista ve Windows 7) Visual Studio çalışma sürümünüzü yalıtınızı tahmin edebilirsiniz:

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {extensionID}*

 *% LocalAppData%* , oturum açmış kullanıcının adı, *Şirket* ise uzantının sahibi olan şirketin adı ve *extensionID* uzantısının kimliğidir.

 Deneysel konuma bir uzantı dağıttığınızda, hata ayıklama modunda çalışır. ikinci bir Visual Studio örneği başlatılır ve **Microsoft Visual Studio-deneysel örnek** olarak adlandırılır.

## <a name="manage-extensions"></a>Uzantıları yönetme

 Visual Studio uzantıları **uzantılar ve güncelleştirmeler** bölümünde ( **araçlar** menüsünde) listelenmiştir. Deneysel örnekteki bir uzantıyı test ediyorsanız, deneysel örnekteki **Uzantılar ve güncelleştirmeler** bölümünde listelenir, ancak geliştirme örneğinde listelenmez.

 daha fazla bilgi için bkz. [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Düzenleyici uzantıları oluşturmak için şablonları kullanma

 Sınıflandırıcı, donmanlar ve kenar boşluklarını özelleştiren MEF uzantıları oluşturmak için düzenleyici şablonlarını kullanabilirsiniz. hem C# hem de Visual Basic projelerine yönelik şablonlar vardır. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 uzantı oluşturmak için vsıx Project şablonunu da kullanabilirsiniz. Bu şablon yalnızca herhangi bir tür uzantıyı dağıtmak için gereken öğeleri sağlar ve *Source. Extension. valtmanifest* dosyasını, gerekli derleme başvurularını ve uzantıyı dağıtmanıza izin veren yapı görevlerini içeren bir proje dosyası içerir. Daha fazla bilgi için bkz. [VSIX proje şablonu](../extensibility/vsix-project-template.md).

 ayrıca, bir Visual Studio paket uzantısından düzenleyici MEF bileşenleri de oluşturabilirsiniz. Ayrıntılar için aşağıdaki izlenecek yollara bakın:

- [İzlenecek yol: bir düzenleyici uzantısıyla kabuk komutu kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [İzlenecek yol: bir düzenleyici uzantısıyla kısayol tuşu kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
