---
title: Editör ve Dil Hizmetlerinin Genişletilmesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711707"
---
# <a name="extend-the-editor-and-language-services"></a>Editör ve dil hizmetlerini genişletme
Kendi düzenleyicinize dil hizmeti özellikleri (IntelliSense gibi) ekleyebilir ve Visual Studio kod düzenleyicisinin çoğu özelliğini genişletebilirsiniz.  Genişletebileceğiniz lerin tam listesi için [Dil hizmeti ve düzenleyici uzantı noktalarına](../extensibility/language-service-and-editor-extension-points.md)bakın.

 Yönetilen Genişletilebilirlik Çerçevesi'ni (MEF) kullanarak çoğu düzenleyici özelliğini genişletirsiniz. Örneğin, uzatmak istediğiniz düzenleyici özelliği sözdizimi boyama ise, farklı boyama istediğiniz sınıflandırmaları ve bunların nasıl ele alınmasını istediğinizi tanımlayan bir MEF *bileşeni bölümü* yazabilirsiniz. Düzenleyici de aynı özelliğin birden çok uzantıları destekler.

 Düzenleyici sunu katmanı Windows Sunu Çerçevesi 'ni (WPF) temel alıntır. WPF esnek metin biçimlendirme için bir grafik kitaplığı sağlar ve grafik ve animasyonlar gibi görselleştirmeler de sağlar.

 Visual Studio SDK, önceki *sürümler* için yazılmış VSPackages'ı desteklemek için şim olarak bilinen bağdaştırıcılar sağlar. Bununla birlikte, mevcut bir VSPackage'ıniz varsa, daha iyi performans ve güvenilirlik elde etmek için yeni teknolojiye güncellemenizi öneririz.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Dil hizmeti ve editör uzantıları ile başlayın](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Editöre uzantı oluşturmanın nasıl yapılacağını açıklar.|
|[Editörün içinde](../extensibility/inside-the-editor.md)|Editörün genel yapısını açıklar ve bazı özelliklerini listeler.|
|[Editörde Yönetilen Genişletilebilirlik Çerçevesi](../extensibility/managed-extensibility-framework-in-the-editor.md)|Yönetilen Genişletilebilirlik Çerçevesi'nin (MEF) editörle nasıl kullanılacağını açıklar.|
|[Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)|Editörün uzantı noktalarını listeler. Uzantı noktaları genişletilebilen düzenleyici özelliklerini temsil emzir.|
|[İzlenme: Görünüm süslemesi, komutlar ve ayarlar (sütun kılavuzları) oluşturma](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Yürür ve belirli bir ekran genişliğine kod tutmanıza yardımcı olmak için sütun kılavuz satırları çizer bir görünüm süsleme bina açıklar.  Ayrıca okuma ve yazma ayarlarını ve Komut Penceresinden çağırabileceğiniz komutları bildirmeyi ve uygular.|
|[Düzenleyici alma](../extensibility/editor-imports.md)|Uzantın içe aktarabileceği hizmetleri listeler.|
|[Eski kodu düzenleyiciye uyarlama](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Eski kodu (Visual Studio 2010 öncesi) düzenleyiciyi genişletmek için uyarlamanın farklı yollarını açıklar.|
|[Eski bir dil hizmetini geçirme](../extensibility/internals/migrating-a-legacy-language-service.md)|VSPackage tabanlı bir dil hizmetinin nasıl geçirilen nasıl açıkladığını açıklar.|
|[Walkthrough: İçerik türünü dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|İçerik türünü dosya adı uzantısına nasıl bağlayacaklarını gösterir.|
|[Walkthrough: Bir kenar boşluğu gph oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)|Kenar boşluğuna simge nin nasıl ekleyeceğini gösterir.|
|[Walkthrough: Metni vurgulama](../extensibility/walkthrough-highlighting-text.md)|Metni vurgulamak için *etiketlerin* nasıl kullanılacağını gösterir.|
|[Walkthrough: Anahat ekleme](../extensibility/walkthrough-outlining.md)|Belirli türdeki ayraçlar için anahat eklemeyi gösterir.|
|[Walkthrough: Eşleşen ayraçları görüntüleme](../extensibility/walkthrough-displaying-matching-braces.md)|Eşleşen ayraçları nasıl vurgulayın gösterir.|
|[Walkthrough: QuickInfo araç ipuçlarını görüntüleyin](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Özellikler, yöntemler ve olaylar gibi kod öğelerini açıklayan QuickInfo açılır pencerelerinin nasıl görüntülenebildiğini gösterir.|
|[Walkthrough: İmza yardımlarını görüntüleme](../extensibility/walkthrough-displaying-signature-help.md)|İmzadaki parametre sayısı ve türleri hakkında bilgi veren açılır pencerelerin nasıl görüntülenebildiğini gösterir.|
|[Walkthrough: Görüntü deyimi tamamlama](../extensibility/walkthrough-displaying-statement-completion.md)|İfade tamamlamanın nasıl uygulanacağını gösterir.|
|[Walkthrough: Kod parçacıkları uygulama](../extensibility/walkthrough-implementing-code-snippets.md)|Kod-parçacık genişletmenin nasıl uygulanacağını gösterir.|
|[Walkthrough: Ekran ampul önerileri](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Kod önerileri için ampullerin nasıl görüntülenebildiğini gösterir.|
|[Walkthrough: Düzenleyici uzantılı bir kabuk komutu kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|VSPackage'daki menü komutunu MEF bileşeniyle nasıl ilişkilendirineni gösterir.|
|[Walkthrough: Düzenleyici uzantısı ile kısayol tuşu kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|VSPackage'daki menü kısayolu ile MEF bileşeninin nasıl ilişkilendirilir olduğunu gösterir.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Yönetilen Genişletilebilirlik Çerçevesi (MEF) hakkında bilgi sağlar.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Sunu Temeli (WPF) hakkında bilgi sağlar.|

## <a name="reference"></a>Başvuru
 Visual Studio editörü aşağıdaki ad boşluklarını içerir.

 <xref:Microsoft.VisualStudio.Language.Intellisense>

 <xref:Microsoft.VisualStudio.Language.StandardClassification>

 <xref:Microsoft.VisualStudio.Editor>

 <xref:Microsoft.VisualStudio.Text>

 <xref:Microsoft.VisualStudio.Text.Adornments>

 <xref:Microsoft.VisualStudio.Text.Classification>

 <xref:Microsoft.VisualStudio.Text.Differencing>

 <xref:Microsoft.VisualStudio.Text.Document>

 <xref:Microsoft.VisualStudio.Text.Editor>

 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>

 <xref:Microsoft.VisualStudio.Text.Formatting>

 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>

 <xref:Microsoft.VisualStudio.Text.Operations>

 <xref:Microsoft.VisualStudio.Text.Outlining>

 <xref:Microsoft.VisualStudio.Text.Projection>

 <xref:Microsoft.VisualStudio.Text.Tagging>

 <xref:Microsoft.VisualStudio.Utilities>
