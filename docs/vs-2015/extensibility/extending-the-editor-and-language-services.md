---
title: Düzenleyiciyi ve dil hizmetlerini genişletme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 085e1b5c1fbfbbaf5649966738f2864e0b72ed35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674778"
---
# <a name="extending-the-editor-and-language-services"></a>Düzenleyiciyi ve Dil Hizmetlerini Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dil hizmeti özelliklerini (IntelliSense gibi) kendi düzenleyicinize ekleyebilirsiniz ve Visual Studio Code Editor özelliklerinin çoğunu genişletebilirsiniz.  Neyi genişletebileceğinize ilişkin tam bir liste için bkz. [dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md).  
  
 Managed Extensibility Framework (MEF) kullanarak çoğu düzenleyici özelliğini genişletebilirsiniz. Örneğin, genişletmek istediğiniz Düzenleyici özelliği söz dizimi renklendirmesi ise, farklı renklendirmesini istediğiniz sınıflandırmaları ve bunların nasıl işlenmesini istediğinizi tanımlayan bir MEF *bileşen bölümü* yazabilirsiniz. Düzenleyici aynı özelliğin birden fazla uzantısını da destekler.  
  
 Düzenleyici sunum katmanı, Windows Presentation Framework (WPF) tabanlıdır. WPF, esnek metin biçimlendirme için bir grafik kitaplığı sağlar ve ayrıca grafik ve animasyon gibi görselleştirmeler sağlar.  
  
 Visual Studio SDK, daha önceki sürümler için yazılmış VSPackages 'leri desteklemek üzere *dolgular* olarak bilinen bağdaştırıcılar sağlar. Bununla birlikte, mevcut bir VSPackage varsa, daha iyi performans ve güvenilirlik elde etmek için bunu yeni teknolojiyle güncelleştirmeniz önerilir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Dil Hizmeti ve Düzenleyici Uzantılarıyla Çalışmaya Başlama](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Düzenleyicide bir uzantının nasıl oluşturulduğunu açıklar.|  
|[Düzenleyicinin İçinde](../extensibility/inside-the-editor.md)|Düzenleyicinin genel yapısını açıklar ve bazı özelliklerini listeler.|  
|[Düzenleyicide Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|Düzenleyiciyle Managed Extensibility Framework (MEF) kullanımını açıklar.|  
|[Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)|Düzenleyicinin uzantı noktalarını listeler. Uzantı noktaları, genişletilebilen düzenleyici özelliklerini temsil eder.|  
|[İzlenecek Yol: Görünüm Kenarlığı, Komutlar ve Ayarlar (Sütun Kılavuzları) Oluşturma](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|İzlenecek yol gösterir ve kodu belirli bir görüntüleme genişliğine sahip olmanıza yardımcı olmak üzere gudie Lines sütununu çizen bir görünüm kenarlığı oluşturmayı açıklar.  Ayrıca, okuma ve yazma ayarlarının yanı sıra komut penceresinden çağırabileceğiniz komutları bildirmek ve uygulamak da gösterilmektedir.|  
|[Düzenleyici İçeri Aktarımları](../extensibility/editor-imports.md)|Bir uzantının içeri aktarabileceğiniz hizmetleri listeler.|  
|[Eski Kodu Düzenleyiciye Uyarlama](../extensibility/adapting-legacy-code-to-the-editor.md)|Düzenleyiciyi genişletmek için eski kodu (Visual Studio 2010 öncesi) uyarlamak için farklı yollar açıklanmaktadır.|  
|[Eski Dil Hizmetini Geçirme](../extensibility/internals/migrating-a-legacy-language-service.md)|VSPackage tabanlı dil hizmetinin nasıl geçirileceği açıklanmaktadır.|  
|[İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Bir içerik türünün bir dosya adı uzantısına nasıl bağlanacağını gösterir.|  
|[İzlenecek Yol: Dış Boşluk Karakteri Oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)|Kenar boşluğuna bir simgenin nasıl ekleneceğini gösterir.|  
|[İzlenecek Yol: Metni Vurgulama](../extensibility/walkthrough-highlighting-text.md)|Metnin vurgulanmasını sağlamak için *etiketlerin* nasıl kullanılacağını gösterir.|  
|[İzlenecek Yol: Ana Hat Oluşturma](../extensibility/walkthrough-outlining.md)|Belirli küme ayraçları için nasıl anahat ekleneceğini gösterir.|  
|[İzlenecek Yol: Eşleşen Küme Ayraçlarını Görüntüleme](../extensibility/walkthrough-displaying-matching-braces.md)|Eşleşen ayraçların nasıl vurgulanmasını gösterir.|  
|[İzlenecek Yol: HızlıBilgi Araç İpuçlarını Görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Özellikler, Yöntemler ve olaylar gibi kod öğelerini tanımlayan hızlı bilgi açılarının nasıl görüntüleneceğini gösterir.|  
|[İzlenecek Yol: İmza Yardımını Görüntüleme](../extensibility/walkthrough-displaying-signature-help.md)|Bir İmzadaki parametrelerin sayısı ve türleri hakkında bilgi veren açılanları görüntülemeyi gösterir.|  
|[İzlenecek Yol: Deyim Tamamlamayı Görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)|Deyimin tamamlanmasına nasıl uygulanacağını gösterir.|  
|[İzlenecek Yol: Kod Parçacıkları Uygulama](../extensibility/walkthrough-implementing-code-snippets.md)|Kod parçacığı genişletmesinin nasıl uygulanacağını gösterir.|  
|[İzlenecek Yol: Ampul Önerilerini Görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Kod önerileri için hafif bulbs görüntülemeyi gösterir.|  
|[İzlenecek Yol: Düzenleyici Uzantısı ile Kabuk Komutu Kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Bir VSPackage içindeki bir menü komutunun bir MEF bileşeniyle nasıl ilişkilendirileceğini gösterir.|  
|[İzlenecek Yol: Düzenleyici Uzantısı ile Kısayol Tuşu Kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Bir VSPackage içindeki bir menü kısayolunun MEF bileşeniyle nasıl ilişkilendirileceğini gösterir.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Managed Extensibility Framework (MEF) hakkında bilgi sağlar.|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Windows Presentation Foundation (WPF) hakkında bilgi sağlar.|  
  
## <a name="reference"></a>Başvuru  
 Visual Studio Düzenleyicisi aşağıdaki ad alanlarını içerir.  
  
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
