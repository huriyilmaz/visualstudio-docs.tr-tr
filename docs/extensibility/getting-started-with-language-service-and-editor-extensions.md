---
title: Dil Hizmeti ve Editör Uzantıları ile Başlarken | Microsoft Dokümanlar
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
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711304"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Dil hizmeti ve editör uzantıları ile başlayın
Anahat oluşturma, ayraç eşleştirme, IntelliSense ve ampuller gibi dil hizmeti özelliklerini kendi programlama dilinize veya herhangi bir içerik türüne eklemek için düzenleyici uzantılarını kullanabilirsiniz. Metin boyama, kenar boşlukları, süslemeler ve diğer görsel öğeler gibi Visual Studio düzenleyicisinin görünümünü ve davranışını da özelleştirebilirsiniz. Ayrıca kendi içerik türünüzü tanımlayabilir ve içeriğinizin göründüğü metin görünümlerinin görünümünü ve davranışını belirtebilirsiniz.

 Düzenleyici uzantıları yazmaya başlamak için Visual Studio SDK'nın bir parçası olarak yüklenen düzenleyici proje şablonlarını kullanın. Visual Studio SDK, VSPackages'i kullanarak veya Yönetilen Genişletilebilirlik Çerçevesi'ni (MEF) kullanarak Visual Studio uzantılarının geliştirilmesini kolaylaştıran indirilebilir bir araç kümesidir.

> [!NOTE]
> Visual Studio SDK hakkında daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

 Kendi editör uzantılarınızı yazmadan önce aşağıdaki kavramlar ve teknolojiler hakkında bilgi edinmenizi öneririz.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Sunu Temeli (WPF) ve düzenleyici uzantıları
 Visual Studio düzenleyici kullanıcı arabirimi (UI), Windows Sunu Temeli (WPF) kullanılarak uygulanır. WPF zengin bir görsel deneyim ve kodun görsel yönlerini iş mantığından ayıran tutarlı bir programlama modeli sağlar. Düzenleyici uzantıları oluştururken birçok WPF öğesi ve özelliği kullanabilirsiniz. Daha fazla bilgi için [Windows Presentation Foundation'a](/dotnet/framework/wpf/index)bakın.

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) ve düzenleyici uzantıları
 Visual Studio düzenleyicisi, bileşenlerini ve uzantılarını yönetmek için Yönetilen Genişletilebilirlik Çerçevesi'ni (MEF) kullanır. MEF ayrıca geliştiricilerin Visual Studio gibi bir ana bilgisayar uygulaması için uzantıları daha kolay oluşturmalarını sağlar. Bu çerçevede, bir MEF sözleşmesine göre bir uzantı tanımlar ve mef bileşeni parçası olarak dışa aktarın. Ana bilgisayar uygulaması bileşen parçalarını bularak, kaydederek ve doğru içeriğe uygulandığından emin olarak yönetir.

> [!NOTE]
> Editördeki MEF hakkında daha fazla bilgi [için, editördeki Yönetilen Genişletilebilirlik Çerçevesi'ne](../extensibility/managed-extensibility-framework-in-the-editor.md)bakın.

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio editörü uzatma noktaları ve uzantıları
 Düzenleyici uzantı noktaları, özelleştirebileceğiniz ve genişletebileceğiniz MEF bileşen parçalarıdır. Bazı durumlarda, bir arabirim uygulayarak ve doğru meta verilerle birlikte dışa aktararak uzantı noktasını genişletirsiniz. Diğer durumlarda sadece bir uzantısı bildirmek ve belirli bir tür olarak dışa aktarın.

 Aşağıdaki editör uzantıları temel türleri şunlardır:

- Kenar boşlukları ve kaydırma çubukları

- Etiketler

- Süsleme -leri

- Seçenekler

- IntelliSense

  Düzenleyici uzantı noktaları hakkında daha fazla bilgi için [Dil hizmeti ve düzenleyici uzantı noktalarına](../extensibility/language-service-and-editor-extension-points.md)bakın.

## <a name="deploying-editor-extensions"></a>Düzenleyici uzantılarını dağıtma
 Visual Studio'da, çözüme *source.extension.vsixmanifest* adlı bir meta veri dosyası ekleyerek, çözümü oluşturarak ve sonra ikili dosyaların bir kopyasını ve bildirimi Visual Studio tarafından bilinen bir klasöre ekleyerek düzenleyici uzantılarını dağıtırsınız. Bildirim dosyası uzantıyla ilgili temel gerçekleri (örneğin, ad, yazar, sürüm ve içerik türü) tanımlar. VSIX manifesto dosyası ve uzantıların nasıl dağıtılanması hakkında daha fazla bilgi için [Ship Visual Studio uzantılarına](../extensibility/shipping-visual-studio-extensions.md)bakın.

 Bir bilgisayara uzantı yüklediğinizde, ikilileri ve bildirimi Visual Studio tarafından bilinen bir klasör alt klasörüne ekleyin.

> [!WARNING]
> Visual Studio'da bulunan düzenleyici genişletilebilirlik şablonlarından birini kullanıyorsanız, bildirimlerin ve dağıtım konumlarının ayrıntıları hakkında endişelenmenize gerek yoktur. Şablonlar, bir uzantıyı kaydetmek ve dağıtmak için gereken her şeyi içerir.

## <a name="run-extensions-in-the-experimental-instance"></a>Uzantıları deneysel örnekte çalıştırma
 Aşağıdaki deneysel klasöre (Windows Vista ve Windows 7'de) dağıtarak bir uzantı geliştirirken Visual Studio'nun çalışma sürümünü izole edebilirsiniz:

 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions\\{Şirket}\\{ExtensionID}*

 *%LOCALAPPDATA%* oturum açmış kullanıcının adı olduğu durumlarda, *Şirket* uzantının sahibi olan şirketin adıdır ve *ExtensionID* uzantının kimliğidir.

 Bir uzantıyı deney konumuna dağıttığınızda, hata ayıklama modunda çalışır. Visual Studio ikinci bir örnek başladı ve **Microsoft Visual Studio**- Deneysel Örnek adlandırılır.

## <a name="manage-extensions"></a>Uzantıları yönetme
 Visual Studio uzantıları **Uzantılar ve Güncellemeler** **(Araçlar** menüsünde) listelenir. Deneysel örnekte bir uzantıyı test ediyorsanız, bu uzantı deneysel örnekte **Uzantılar ve Güncelleştirmeler'de** listelenir, ancak geliştirme örneğinde listelenmez.

 Daha fazla bilgi için [Visual Studio uzantılarını bul ve kullan.](../ide/finding-and-using-visual-studio-extensions.md)

## <a name="use-templates-to-create-editor-extensions"></a>Düzenleyici uzantıları oluşturmak için şablonları kullanma
 Sınıflandırıcıları, süslemeleri ve kenar boşluklarını özelleştiren MEF uzantıları oluşturmak için düzenleyici şablonlarını kullanabilirsiniz. Hem C# hem de Visual Basic projeleri için şablonlar vardır. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

 Uzantıları oluşturmak için VSIX Project şablonu da kullanabilirsiniz. Bu şablon yalnızca her türlü uzantıyı dağıtmak için gereken öğeleri sağlar ve *source.extension.vsixmanifest* dosyasını, gerekli derleme başvurularını ve uzantıyı dağıtmanızı sağlayan yapı görevlerini içeren bir proje dosyasını içerir. Daha fazla bilgi için [VSIX proje şablonuna](../extensibility/vsix-project-template.md)bakın.

 Visual Studio Paketi uzantısından editör MEF bileşenleri de oluşturabilirsiniz. Ayrıntılar için aşağıdaki izilere bakın:

- [Walkthrough: Düzenleyici uzantılı bir kabuk komutu kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Walkthrough: Düzenleyici uzantılı kısayol tuşu kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
