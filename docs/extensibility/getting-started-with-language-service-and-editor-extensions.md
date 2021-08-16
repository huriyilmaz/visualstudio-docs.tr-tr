---
title: Kullanmaya başlayın hizmeti ve düzenleyici uzantılarıyla birlikte
description: Herhangi bir içerik türüne dil hizmeti özellikleri ekleme ve uygulama düzenleyicisinin görünümünü ve davranışını Visual Studio öğrenin.
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
ms.openlocfilehash: b9518179b0096dcb7527ea5e9eba4e72cbc70727c7d6f73af4b59f6cb22d08cc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359981"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Kullanmaya başlayın hizmeti ve düzenleyici uzantılarıyla birlikte

Kendi programlama dilinize veya herhangi bir içerik türüne açıklama, ayraç eşleştirme, IntelliSense ve ampuller gibi dil hizmeti özellikleri eklemek için düzenleyici uzantılarını kullanabilirsiniz. Ayrıca, metin renklendirme, kenar boşlukları, donatma Visual Studio diğer görsel öğeler gibi bir düzenleyicinin görünümünü ve davranışını özelleştirebilirsiniz. Ayrıca kendi içerik türlerinizi tanımlayabilir ve içeriğinizin göründüğü metin görünümlerinin görünümünü ve davranışını belirtebilirsiniz.

 Düzenleyici uzantıları yazmaya başlamanız için, Visual Studio SDK'sı kapsamında yüklü olan düzenleyici proje şablonlarını kullanın. Visual Studio SDK, VSPackage'ları kullanarak veya Managed Extensibility Framework (MEF) kullanarak Visual Studio uzantıları geliştirmeyi kolaylaştıran indirilebilir Managed Extensibility Framework kümesidir.

> [!NOTE]
> Visual Studio SDK hakkında daha fazla bilgi için [bkz. Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

 Kendi düzenleyici uzantılarınızı yazmadan önce aşağıdaki kavramlar ve teknolojiler hakkında bilgi öğrenmenizi öneririz.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) ve düzenleyici uzantıları

 Visual Studio düzenleyicisi kullanıcı arabirimi (UI), Windows Presentation Foundation (WPF) kullanılarak uygulanır. WPF, zengin bir görsel deneyim ve kodun görsel yönlerini iş mantığından ayıran tutarlı bir programlama modeli sağlar. Düzenleyici uzantıları oluşturmada birçok WPF öğe ve özelliği kullanabilirsiniz. Daha fazla bilgi için [bkz. Windows Presentation Foundation.](/dotnet/framework/wpf/index)

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) ve düzenleyici uzantıları

 Uygulama Visual Studio, bileşenlerini ve Managed Extensibility Framework yönetmek için Managed Extensibility Framework (MEF) kullanır. MEF ayrıca geliştiricilerin bir konak uygulaması için uzantılar oluşturmalarını daha kolay bir şekilde Visual Studio. Bu çerçevede, bir MEF sözleşmesine göre bir uzantı tanımlar ve bir MEF bileşeni olarak dışarı aktarabilirsiniz. Konak uygulama bileşen parçalarını bularak, kaydederek ve doğru bağlama uygulandığından emin olarak yönetir.

> [!NOTE]
> Düzenleyicide MEF hakkında daha fazla bilgi için [düzenleyicide Managed Extensibility Framework bkz.](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio düzenleyicisi uzantı noktaları ve uzantıları

 Düzenleyici uzantısı noktaları, özelleştirebileceğiniz ve genişletebileceğiniz MEF bileşen parçalarıdır. Bazı durumlarda, bir arabirim uygulayarak ve doğru meta verilerle birlikte dışarı aktararak uzantı noktasını genişletebilirsiniz. Diğer durumlarda yalnızca bir uzantıyı bildirer ve belirli bir tür olarak dışarı aktarın.

 Aşağıda, temel türlerde düzenleyici uzantılarının bazıları ve aşağıda ve ardından ve hatta daha fazla düzenleyici uzantısı ve daha sonra yer almaktadır:

- Kenar boşlukları ve kaydırma çubuğu

- Etiketler

- Süsleme -leri

- Seçenekler

- IntelliSense

  Düzenleyici uzantı noktaları hakkında daha fazla bilgi için [bkz. Dil hizmeti ve düzenleyici uzantısı noktaları.](../extensibility/language-service-and-editor-extension-points.md)

## <a name="deploying-editor-extensions"></a>Düzenleyici uzantılarını dağıtma

 Visual Studio'de, *çözüme source.extension.vsixmanifest* adlı bir meta veri dosyası ekleyerek, çözümü oluşturarak ve ardından ikili dosyaların ve bildirimin bir kopyasını çözüm tarafından bilinen bir klasöre ekleyerek düzenleyici uzantılarını Visual Studio. Bildirim dosyası uzantıyla ilgili temel olguları tanımlar (örneğin, ad, yazar, sürüm ve içerik türü). VSIX bildirim dosyası ve uzantıları dağıtma hakkında daha fazla bilgi için bkz. [Visual Studio uzantıları gönder.](../extensibility/shipping-visual-studio-extensions.md)

 Bir bilgisayara uzantıyı yükleyiciyi, ikili dosyaları ve bildirimi, dosyaları ve bildirimi bilinen bir klasörün alt klasörüne Visual Studio.

> [!WARNING]
> Düzenleyicide bulunan düzenleyici genişletilebilirlik şablonlarından birini kullanıyorsanız bildirimlerin ve dağıtım konumlarının ayrıntıları konusunda endişelenmeniz Visual Studio. Şablonlar, bir uzantıyı kaydetmek ve dağıtmak için gereken her şeyi içerir.

## <a name="run-extensions-in-the-experimental-instance"></a>Deneysel örnekte uzantıları çalıştırma

 Uzantıyı aşağıdaki deneysel klasöre dağıtarak (Visual Studio Vista ve Windows 7 üzerinde) uzantıyı geliştirirken çalışma sürümü Windows bağımsız Windows edinebilirsiniz:

 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions \\ {Company} \\ {ExtensionID}*

 Burada *%LOCALAPPDATA%* oturum açan kullanıcının *adı,* Şirket uzantının sahibi olan şirketin adı ve *ExtensionID* ise uzantının kimliğidir.

 Deneysel konuma bir uzantı dağıtsanız, uzantı hata ayıklama modunda çalışır. İkinci bir Visual Studio örneği başlatıldı ve Microsoft Visual Studio **- Deneysel Örneği olarak adlandırılmış.**

## <a name="manage-extensions"></a>Uzantıları yönetme

 Bu Visual Studio Uzantılar ve **Güncelleştirmeler 'de** (Araçlar **menüsünde)** listelenir. Deneysel örnekte bir uzantıyı test ediyorsanız,  uzantı deneysel örnekteki Uzantılar ve Güncelleştirmeler'de listelenir, ancak geliştirme örneğinde listelenmiyor.

 Daha fazla bilgi için [bkz. Uzantılarını bulma Visual Studio kullanın.](../ide/finding-and-using-visual-studio-extensions.md)

## <a name="use-templates-to-create-editor-extensions"></a>Düzenleyici uzantıları oluşturmak için şablonları kullanma

 Sınıflandırıcıları, donatmaları ve kenar boşluklarını özelleştiren MEF uzantıları oluşturmak için düzenleyici şablonlarını kullanabilirsiniz. Hem C# hem de Visual Basic vardır. Daha fazla bilgi için [bkz. Düzenleyici öğesi şablonuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

 Uzantı oluşturmak için VSIX Project şablonunu da kullanabilirsiniz. Bu şablon yalnızca herhangi bir uzantıyı dağıtmak için gereken öğeleri sağlar ve *source.extension.vsixmanifest* dosyasını, gerekli derleme başvurularını ve uzantıyı dağıtmaya olanak sağlayan derleme görevlerini içeren bir proje dosyasını içerir. Daha fazla bilgi için bkz. [VSIX proje şablonu.](../extensibility/vsix-project-template.md)

 Ayrıca, bir paket uzantısından düzenleyici MEF Visual Studio oluşturabilirsiniz. Ayrıntılar için aşağıdaki izlenecek yollara bakın:

- [Adım adım kılavuz: Düzenleyici uzantısıyla kabuk komutu kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Adım adım kılavuz: Düzenleyici uzantısıyla kısayol tuşu kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve düzenleyici uzantısı noktaları](../extensibility/language-service-and-editor-extension-points.md)
