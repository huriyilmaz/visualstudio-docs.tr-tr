---
title: Dil hizmeti ve Düzenleyici uzantıları ile çalışmaya başlama
description: Her türlü içerik türüne dil hizmeti özellikleri eklemeyi ve Visual Studio düzenleyicisinin görünümünü ve davranışını özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 471acaef0145b3bf1a73925b42e17a6343439ea2
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994400"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Dil hizmeti ve Düzenleyici uzantıları ile çalışmaya başlama

Ana hat, küme ayracı eşleştirme, IntelliSense ve hafif bulbs gibi dil hizmeti özelliklerini kendi programlama dilinize veya herhangi bir içerik türüne eklemek için düzenleyici uzantılarını kullanabilirsiniz. Visual Studio düzenleyicisinin görünümünü ve davranışını, örneğin metin renklendirme, kenar boşlukları, donnments ve diğer görsel öğeleri de özelleştirebilirsiniz. Ayrıca kendi içerik türünü tanımlayabilir ve içeriğinizin göründüğü metin görünümlerinin görünümünü ve davranışını belirtebilirsiniz.

 Düzenleyici uzantıları yazmaya başlamak için, Visual Studio SDK 'nin bir parçası olarak yüklenen düzenleyici proje şablonlarını kullanın. Visual Studio SDK, VSPackages kullanarak ya da Managed Extensibility Framework (MEF) kullanarak Visual Studio uzantıları geliştirmeyi kolaylaştıran indirilebilir bir araç kümesidir.

> [!NOTE]
> Visual Studio SDK hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

 Kendi düzenleyici uzantılarınızı yazmadan önce aşağıdaki kavramlar ve teknolojiler hakkında bilgi edinmenizi öneririz.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) ve Düzenleyici uzantıları

 Visual Studio Düzenleyicisi Kullanıcı arabirimi (UI) Windows Presentation Foundation (WPF) kullanılarak uygulanır. WPF, iş mantığındaki kodun görsel yönlerini ayıran zengin bir görsel deneyim ve tutarlı bir programlama modeli sağlar. Düzenleyici uzantıları oluştururken birçok WPF öğesi ve özelliği kullanabilirsiniz. Daha fazla bilgi için bkz. [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) ve Düzenleyici uzantıları

 Visual Studio Düzenleyicisi, bileşenlerini ve uzantılarını yönetmek için Managed Extensibility Framework (MEF) kullanır. MEF, geliştiricilerin Visual Studio gibi bir ana bilgisayar uygulaması için daha kolay uzantı oluşturmasını da sağlar. Bu çerçevede bir MEF sözleşmesine göre uzantı tanımlar ve bir MEF bileşeni parçası olarak dışarı aktarabilirsiniz. Konak uygulaması, bileşen parçalarını onları bularak, kaydederek ve doğru bağlama uygulandığından emin olarak yönetir.

> [!NOTE]
> Düzenleyicide MEF hakkında daha fazla bilgi için, bkz. [düzenleyicide Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio Düzenleyicisi uzantı noktaları ve uzantıları

 Düzenleyici uzantı noktaları, özelleştirebileceğiniz ve genişletebilen MEF bileşen bölümleridir. Bazı durumlarda, bir arabirim uygulayarak ve doğru meta verilerle birlikte dışarı aktararak uzantı noktasını genişletebilirsiniz. Diğer durumlarda, yalnızca bir uzantı bildirip belirli bir tür olarak dışarı aktardınız.

 Aşağıdaki temel tür Düzenleyici genişletmeler şunlardır:

- Kenar boşlukları ve kaydırma çubukları

- Etiketler

- Satırdaki kenarlıkları

- Seçenekler

- IntelliSense

  Düzenleyici uzantı noktaları hakkında daha fazla bilgi için bkz. [dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Düzenleyici uzantılarını dağıtma

 Visual Studio 'da, çözüme *kaynak. Extension. valtmanifest* adlı bir meta veri dosyası ekleyerek, çözümü oluşturarak ve ardından ikili dosyaların ve bildirimin bir kopyasını Visual Studio 'nun bilinen bir klasöre ekleyerek Düzenleyici uzantıları dağıtırsınız. Bildirim dosyası, uzantıyla ilgili temel gerçekleri tanımlar (örneğin, ad, yazar, sürüm ve içerik türü). VSıX bildirim dosyası ve uzantıların nasıl dağıtılacağı hakkında daha fazla bilgi için bkz. [Visual Studio uzantılarını](../extensibility/shipping-visual-studio-extensions.md)gönderme.

 Bir bilgisayara uzantı yüklediğinizde, ikili dosyaları ve bildirimi Visual Studio 'nun bilinen klasörünün bir alt klasörüne ekleyin.

> [!WARNING]
> Visual Studio 'da bulunan düzenleyici genişletilebilirlik şablonlarından birini kullanıyorsanız, bildirimlerin ve dağıtım konumlarının ayrıntıları konusunda endişelenmeniz gerekmez. Şablonlar, bir uzantıyı kaydetmek ve dağıtmak için gereken her şeyi içerir.

## <a name="run-extensions-in-the-experimental-instance"></a>Deneysel örnekte uzantıları çalıştırma

 Visual Studio 'nun çalışma sürümünüzü yalıtarak, bir uzantıyı aşağıdaki deneysel klasöre dağıtarak (Windows Vista ve Windows 7 ' de) kullanabilirsiniz:

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {extensionID}*

 *% LocalAppData%* , oturum açmış kullanıcının adı, *Şirket* ise uzantının sahibi olan şirketin adı ve *extensionID* uzantısının kimliğidir.

 Deneysel konuma bir uzantı dağıttığınızda, hata ayıklama modunda çalışır. Visual Studio 'nun ikinci bir örneği başlatılır ve **Microsoft Visual Studio deneysel örnek** olarak adlandırılır.

## <a name="manage-extensions"></a>Uzantıları yönetme

 Uzantılar **ve güncelleştirmeler** bölümünde Visual Studio uzantıları listelenmiştir ( **Araçlar** menüsünde). Deneysel örnekteki bir uzantıyı test ediyorsanız, deneysel örnekteki **Uzantılar ve güncelleştirmeler** bölümünde listelenir, ancak geliştirme örneğinde listelenmez.

 Daha fazla bilgi için bkz. [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Düzenleyici uzantıları oluşturmak için şablonları kullanma

 Sınıflandırıcı, donmanlar ve kenar boşluklarını özelleştiren MEF uzantıları oluşturmak için düzenleyici şablonlarını kullanabilirsiniz. Hem C# hem de Visual Basic projelerine yönelik şablonlar vardır. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Uzantı oluşturmak için VSıX proje şablonunu da kullanabilirsiniz. Bu şablon yalnızca herhangi bir tür uzantıyı dağıtmak için gereken öğeleri sağlar ve *Source. Extension. valtmanifest* dosyasını, gerekli derleme başvurularını ve uzantıyı dağıtmanıza izin veren yapı görevlerini içeren bir proje dosyası içerir. Daha fazla bilgi için bkz. [VSIX proje şablonu](../extensibility/vsix-project-template.md).

 Ayrıca, Visual Studio paket uzantısından düzenleyici MEF bileşenleri de oluşturabilirsiniz. Ayrıntılar için aşağıdaki izlenecek yollara bakın:

- [İzlenecek yol: bir düzenleyici uzantısıyla kabuk komutu kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [İzlenecek yol: bir düzenleyici uzantısıyla kısayol tuşu kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
