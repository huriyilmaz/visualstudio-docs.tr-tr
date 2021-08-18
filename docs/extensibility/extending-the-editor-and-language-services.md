---
title: Düzenleyiciyi ve dil hizmetlerini genişletme | Microsoft Docs
description: bir düzenleyiciye dil hizmeti özellikleri ekleyebilir ve Visual Studio kod düzenleyicisinin özelliklerini genişletebilirsiniz. Managed Extensibility Framework hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8fa21afe5bffa298847aa90229e087c94b38f8a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125133"
---
# <a name="extend-the-editor-and-language-services"></a>Düzenleyiciyi ve dil hizmetlerini genişletme
kendi düzenleyicinize dil hizmeti özellikleri (ıntellisense gibi) ekleyebilir ve Visual Studio kod düzenleyicisinin birçok özelliğini genişletebilirsiniz.  Neyi genişletebileceğinize ilişkin tam bir liste için bkz. [dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md).

 Managed Extensibility Framework (MEF) kullanarak çoğu düzenleyici özelliğini genişletebilirsiniz. Örneğin, genişletmek istediğiniz Düzenleyici özelliği söz dizimi renklendirmesi ise, farklı renklendirmesini istediğiniz sınıflandırmaları ve bunların nasıl işlenmesini istediğinizi tanımlayan bir MEF *bileşen bölümü* yazabilirsiniz. Düzenleyici aynı özelliğin birden fazla uzantısını da destekler.

 düzenleyici sunum katmanı, Windows presentation çerçevesini (WPF) temel. WPF, esnek metin biçimlendirme için bir grafik kitaplığı sağlar ve ayrıca grafik ve animasyon gibi görselleştirmeler sağlar.

 Visual Studio SDK, daha önceki sürümler için yazılmış vspackages 'leri desteklemek üzere *dolgular* olarak bilinen bağdaştırıcılar sağlar. Bununla birlikte, mevcut bir VSPackage varsa, daha iyi performans ve güvenilirlik elde etmek için bunu yeni teknolojiyle güncelleştirmeniz önerilir.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Dil hizmeti ve Düzenleyici uzantıları ile çalışmaya başlama](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Düzenleyicide bir uzantının nasıl oluşturulduğunu açıklar.|
|[Düzenleyicinin içinde](../extensibility/inside-the-editor.md)|Düzenleyicinin genel yapısını açıklar ve bazı özelliklerini listeler.|
|[düzenleyicide Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|düzenleyiciyle Managed Extensibility Framework (MEF) kullanımını açıklar.|
|[Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)|Düzenleyicinin uzantı noktalarını listeler. Uzantı noktaları, genişletilebilen düzenleyici özelliklerini temsil eder.|
|[İzlenecek yol: Görünüm kenarlığı, komutlar ve ayarlar oluşturma (sütun Kılavuzu)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|İzlenecek yol gösterir ve kodu belirli bir görüntüleme genişliğine sahip olmanıza yardımcı olmak üzere sütun kılavuzu çizgileri çizen bir görünüm kenarlığı oluşturmayı açıklar.  Ayrıca, okuma ve yazma ayarlarının yanı sıra komut penceresinden çağırabileceğiniz komutları bildirmek ve uygulamak da gösterilmektedir.|
|[Düzenleyici içeri aktarmaları](../extensibility/editor-imports.md)|Bir uzantının içeri aktarabileceğiniz hizmetleri listeler.|
|[Eski kodu düzenleyiciye uyarlayabilirsiniz](/previous-versions/visualstudio/visual-studio-2015/extensibility/adapting-legacy-code-to-the-editor?preserve-view=true&view=vs-2015)|düzenleyiciyi genişletmek için eski kodu (ön Visual Studio 2010) uyarlamak için farklı yollar açıklanmaktadır.|
|[Eski dil hizmetini geçirme](../extensibility/internals/migrating-a-legacy-language-service.md)|VSPackage tabanlı dil hizmetinin nasıl geçirileceği açıklanmaktadır.|
|[İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Bir içerik türünün bir dosya adı uzantısına nasıl bağlanacağını gösterir.|
|[İzlenecek yol: kenar boşluğu karakteri oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)|Kenar boşluğuna bir simgenin nasıl ekleneceğini gösterir.|
|[İzlenecek yol: metni vurgula](../extensibility/walkthrough-highlighting-text.md)|Metnin vurgulanmasını sağlamak için *etiketlerin* nasıl kullanılacağını gösterir.|
|[İzlenecek yol: Ana hat ekleme](../extensibility/walkthrough-outlining.md)|Belirli küme ayraçları için nasıl anahat ekleneceğini gösterir.|
|[İzlenecek yol: eşleşen ayraçları görüntüle](../extensibility/walkthrough-displaying-matching-braces.md)|Eşleşen ayraçların nasıl vurgulanmasını gösterir.|
|[İzlenecek yol: hızlı bilgi araç ipuçlarını görüntüle](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Özellikler, Yöntemler ve olaylar gibi kod öğelerini tanımlayan hızlı bilgi açılarının nasıl görüntüleneceğini gösterir.|
|[İzlenecek yol: imza yardımını görüntüle](../extensibility/walkthrough-displaying-signature-help.md)|Bir İmzadaki parametrelerin sayısı ve türleri hakkında bilgi veren açılanları görüntülemeyi gösterir.|
|[İzlenecek yol: görüntüleme ifadesinin tamamlanması](../extensibility/walkthrough-displaying-statement-completion.md)|Deyimin tamamlanmasına nasıl uygulanacağını gösterir.|
|[İzlenecek yol: kod parçacıklarını uygulama](../extensibility/walkthrough-implementing-code-snippets.md)|Kod parçacığı genişletmesinin nasıl uygulanacağını gösterir.|
|[İzlenecek yol: ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Kod önerileri için hafif bulbs görüntülemeyi gösterir.|
|[İzlenecek yol: Düzenleyici uzantısı ile bir Shell komutu kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Bir VSPackage içindeki bir menü komutunun bir MEF bileşeniyle nasıl ilişkilendirileceğini gösterir.|
|[İzlenecek yol: bir düzenleyici uzantısıyla kısayol tuşu kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Bir VSPackage içindeki bir menü kısayolunun MEF bileşeniyle nasıl ilişkilendirileceğini gösterir.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Managed Extensibility Framework (MEF) hakkında bilgi sağlar.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Presentation Foundation (WPF) hakkında bilgi sağlar.|

## <a name="reference"></a>Başvuru
 Visual Studio düzenleyicisi aşağıdaki ad alanlarını içerir.

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