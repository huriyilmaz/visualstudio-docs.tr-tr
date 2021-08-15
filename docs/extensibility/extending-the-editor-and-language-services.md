---
title: Düzenleyici ve Dil Hizmetleri | Microsoft Docs
description: Bir düzenleyiciye dil hizmeti özellikleri ekleyebilir ve kod düzenleyicisinin Visual Studio genişletebilirsiniz. Aşağıdakiler hakkında bilgi Managed Extensibility Framework.
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
ms.openlocfilehash: 3f349cd733be2ae45eeca22d9e1f30693568b107caee075f4ecadf6ad22950ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432897"
---
# <a name="extend-the-editor-and-language-services"></a>Düzenleyiciyi ve dil hizmetlerini genişletme
Dil hizmeti özelliklerini (IntelliSense gibi) kendi düzenleyicinize ekleyebilir ve kod düzenleyicisinin çoğu Visual Studio genişletebilirsiniz.  Genişletebilirsiniz nelerin tam listesi için bkz. [Dil hizmeti ve düzenleyici uzantısı noktaları.](../extensibility/language-service-and-editor-extension-points.md)

 Düzenleyici özelliklerinin çoğunu, Managed Extensibility Framework (MEF) kullanarak genişletersiniz. Örneğin, genişletmek istediğiniz düzenleyici özelliği söz dizimi renklendirmesi ise, farklı renklendirme istediğiniz sınıflandırmaları ve bunları nasıl işlemelerini istediğinizi tanımlayan bir *MEF* bileşeni bölümü yazabilirsiniz. Düzenleyici aynı özelliğin birden çok uzantısını da destekler.

 Düzenleyici sunu katmanı, Presentation Framework 'Windows (WPF) temel alır. WPF, esnek metin biçimlendirmesi için bir grafik kitaplığının yanı sıra grafik ve animasyon gibi görselleştirmeler sağlar.

 Visual Studio SDK'sı, önceki sürümler için yazılmış *VSPackage'ları* desteklemek için dolgu olarak bilinen bağdaştırıcılar sağlar. Bununla birlikte, var olan bir VSPackage'niz varsa, daha iyi performans ve güvenilirlik elde etmek için bunu yeni teknolojiye güncelleştirmenizi öneririz.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Kullanmaya başlayın hizmeti ve düzenleyici uzantılarıyla birlikte](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Düzenleyicide bir uzantının nasıl oluşturularak ilgili açıklamayı açıklar.|
|[Düzenleyicinin içinde](../extensibility/inside-the-editor.md)|Düzenleyicinin genel yapısını açıklar ve bazı özelliklerini listeler.|
|[Managed Extensibility Framework düzenleyicide](../extensibility/managed-extensibility-framework-in-the-editor.md)|Düzenleyici ile Managed Extensibility Framework (MEF) kullanmayı açıklar.|
|[Dil hizmeti ve düzenleyici uzantısı noktaları](../extensibility/language-service-and-editor-extension-points.md)|Düzenleyicinin uzantı noktalarını listeler. Uzantı noktaları, uzatılabilir düzenleyici özelliklerini temsil ediyor.|
|[Kılavuz: Görünüm kenarlığı, komutlar ve ayarlar oluşturma (sütun kılavuzları)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Kodu belirli bir görüntüleme genişliğine göre tutmanıza yardımcı olmak için sütun kılavuz çizgileri çizen bir görünüm donatma üzerinde yol gösterir ve açıklama sağlar.  Ayrıca, okuma ve yazma ayarlarının yanı sıra Komut Penceresinden çağırabilirsiniz komutların bildiril ve uygulanmasını gösterir.|
|[Düzenleyici içeri aktarmaları](../extensibility/editor-imports.md)|Bir uzantının içeri aktarabilirsiniz hizmetleri listeler.|
|[Eski kodu düzenleyiciye uyarlama](/previous-versions/visualstudio/visual-studio-2015/extensibility/adapting-legacy-code-to-the-editor?preserve-view=true&view=vs-2015)|Düzenleyiciyi genişletmek için eski kodu (2010 Visual Studio) uyarlamanın farklı yollarını açıklar.|
|[Eski dil hizmetini geçirme](../extensibility/internals/migrating-a-legacy-language-service.md)|VSPackage tabanlı dil hizmetinin nasıl geçirilir?|
|[Adım adım kılavuz: İçerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|İçerik türünü bir dosya adı uzantısına bağlamayı gösterir.|
|[Adım adım kılavuz: Kenar boşluğu ifadesi oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)|Kenar boşluğuna simge eklemeyi gösterir.|
|[Adım adım kılavuz: Metni vurgulama](../extensibility/walkthrough-highlighting-text.md)|Metni vurgulamak için *etiketlerin* nasıl kullanıllarını gösterir.|
|[Adım adım kılavuz: Açıklama ekleme](../extensibility/walkthrough-outlining.md)|Belirli küme ayracı türleri için nasıl bir açıklama ekli olduğunu gösterir.|
|[Adım adım kılavuz: Eşleşen ayraçları görüntüleme](../extensibility/walkthrough-displaying-matching-braces.md)|Eşleşen küme ayraçlarını vurgulamayı gösterir.|
|[Adım adım kılavuz: QuickInfo araç ipucu görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Özellikler, yöntemler ve olaylar gibi kod öğelerini açıklayan QuickInfo açılır pencerelerinin nasıl görüntüleniyor olduğunu gösterir.|
|[Adım adım kılavuz: İmzayı görüntüleme yardımı](../extensibility/walkthrough-displaying-signature-help.md)|Bir imzada parametre sayısı ve türleri hakkında bilgi vermek için açılan pencerelerin nasıl görüntüleniyor olduğunu gösterir.|
|[Adım adım kılavuz: Deyim tamamlamayı görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)|Deyim tamamlamanın nasıl uygulandığını gösterir.|
|[Adım adım kılavuz: Kod parçacıklarını uygulama](../extensibility/walkthrough-implementing-code-snippets.md)|Kod parçacığı genişletmesinin nasıl uygulandığını gösterir.|
|[Adım adım kılavuz: Ampul önerilerini görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Kod önerileri için ampulleri görüntülemeyi gösterir.|
|[Adım adım kılavuz: Düzenleyici uzantısıyla kabuk komutu kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|VSPackage'daki menü komutunu mef bileşeniyle ilişkilendirmeyi gösterir.|
|[Adım adım kılavuz: Düzenleyici uzantısıyla kısayol tuşu kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|VSPackage'daki menü kısayolunu MEF bileşeniyle ilişkilendirmeyi gösterir.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Managed Extensibility Framework (MEF) hakkında bilgi sağlar.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Presentation Foundation (WPF) hakkında bilgi sağlar.|

## <a name="reference"></a>Başvuru
 Örnek Visual Studio aşağıdaki ad alanlarını içerir.

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