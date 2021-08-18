---
title: Belge düzeyinde özelleştirmelerde XML şemaları ve verileri
description: Microsoft Excel word, şemaları belgelerinize eşleme özelliği sağlar ve belge içinde ve dışında XML verilerini içeri ve dışarı aktarmayı basitleştirebilir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3944655cd84f1034e2c3850514d45fdccf27a1ec
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045963"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Belge düzeyinde özelleştirmelerde XML şemaları ve verileri
  **Önemli** Microsoft Word ile ilgili bu konu başlığı altında açıklanan bilgiler, Birleşik Devletler Microsoft tarafından Ocak 2010'dan önce Microsoft tarafından lisanslanmıştır ve Ocak 2010'dan önce Microsoft tarafından lisanslanmıştır ve Microsoft Word Microsoft Word'den özel XML ile ilgili belirli bir işlevselliğin uygulamasını kaldıran ya da üzerinde çalışan programları kullanan veya geliştiren kişiler ve kuruluşların kullanımı için özel olarak sunulmuştur. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler'daki veya Birleşik Devletler'daki veya Microsoft tarafından 10 Ocak 2010'dan sonra lisansları alınan Microsoft Word ürünleri üzerinde çalışan programları kullanan veya geliştiren kişiler veya kuruluşlar tarafından okunamayabilirsiniz veya kullanılamaz; bu ürünler, o tarihten önce lisansa sahip olan veya satın alınan ve satın alınan ve satın alınan ürünlerle aynı şekilde davranmaz Birleşik Devletler.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel ve Microsoft Office Word, şemaları belgelerinize eşleme özelliği sağlar. Bu özellik, belge içinde ve dışında XML verilerini içeri ve dışarı aktarmayı basitleştirebilir.

 Visual Studio, eşlenmiş şema öğelerini belge düzeyi özelleştirmelerde programlama modelinde denetim olarak gösterir. Daha Excel, Visual Studio veritabanları, Web hizmetleri ve nesnelerdeki verilere denetimleri bağlama desteği ekler. Word ve Excel Visual Studio, çözümleriniz için gelişmiş bir son kullanıcı deneyimi oluşturmak için şemayla eşlenmiş bir belgeyle birlikte ekleyebilirsiniz. Daha fazla bilgi için bkz. [Eylemler bölmesine genel bakış.](../vsto/actions-pane-overview.md)

> [!NOTE]
> Çok parçalı XML şemalarını çok parçalı xml Excel kullanılamaz.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Şemalar çalışma kitaplarında Excel oluşturulan nesneler
 Bir çalışma kitabına şema eklerken, Visual Studio otomatik olarak birkaç nesne oluşturur ve bunları projenize ekler. Bu nesneler, Visual Studio tarafından yönetilemedikleri için Excel. Bunları silmek için eşlenen öğeleri çalışma sayfasından kaldırın veya Excel kullanarak şemayı kaldırın.

 İki ana nesne vardır:

- XML şeması (XSD dosyası). Çalışma kitabındaki her şema için Visual Studio projeye bir şema ekler. Bu, içinde XSD uzantısına sahip bir proje öğesi **olarak Çözüm Gezgini.**

- Türü türüne göre <xref:System.Data.DataSet> bir sınıf. Bu sınıf şemaya göre oluşturulur. Bu veri kümesi sınıfı, içinde **Sınıf Görünümü.**

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Şema öğeleri çalışma sayfalarıyla eşlen Excel oluşturulan nesneler
 **XML** Kaynağı görev bölmesindeki bir şema öğesini bir çalışma sayfasına eşle Visual Studio otomatik olarak birkaç nesne oluşturur ve bunları projenize ekler:

- Denetim. Çalışma kitabındaki her eşlenmiş nesne için, programlama modelinde bir denetim (tekrar etmeyen şema öğeleri için) veya bir denetim (şema öğelerini yinelemek <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> için) oluşturulur. Denetim <xref:Microsoft.Office.Tools.Excel.ListObject> yalnızca eşlemeler ve eşlenen nesneler çalışma kitabından silinerek silinebilir. Denetimler hakkında daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

- Bindingsource. Yinelenen olmayan bir şema öğesini çalışma sayfasına eşlerken bir oluşturulduğunda, bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> oluşturulur ve denetim öğesine bağlı <xref:System.Windows.Forms.BindingSource> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:System.Windows.Forms.BindingSource> olur. veri kaynağının belgeyle eşlenen şemayla eşleşen bir örneğine bağlamanız gerekir, örneğin, oluşturulan türü oluşturulmuş <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> bir sınıfın örneği. Özellikler penceresinde ortaya çıkar ve <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliklerini ayarerek **bağlamayı** oluşturun.

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>nesneleri için <xref:Microsoft.Office.Tools.Excel.ListObject> oluşturulmaz. Özellikler penceresinde ve <xref:Microsoft.Office.Tools.Excel.ListObject> özelliklerini ayarerek veri kaynağına el <xref:System.Windows.Forms.BindingSource.DataSource%2A> ile <xref:System.Windows.Forms.BindingSource.DataMember%2A> **bağlamanız** gerekir.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office şemaları ve Visual Studio Veri Kaynakları penceresini açın
 Office ve Visual Studio **Veri** Kaynakları penceresinin eşlenen şema işlevselliği, raporlama veya düzenleme için Excel çalışma sayfasında veri sunabilirsiniz. Her iki durumda da veri öğelerini çalışma sayfasındaki Excel sürükleyebilirsiniz. Her iki yöntem de veya web hizmeti gibi bir veri kaynağına bağlı veriler <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> olan denetimler oluşturun.

> [!NOTE]
> Yinelenen bir şema öğesini çalışma sayfasına eşlerken, Visual Studio <xref:Microsoft.Office.Tools.Excel.ListObject> oluşturur. <xref:Microsoft.Office.Tools.Excel.ListObject>, aracılığıyla verilere otomatik olarak bağlı <xref:System.Windows.Forms.BindingSource> değildir. Özellikler penceresinde ve <xref:Microsoft.Office.Tools.Excel.ListObject> özelliklerini ayarerek veri kaynağına el <xref:System.Windows.Forms.BindingSource.DataSource%2A> ile <xref:System.Windows.Forms.BindingSource.DataMember%2A> **bağlamanız** gerekir.

 Aşağıdaki tabloda iki yöntem arasındaki farklardan bazıları yer almaktadır.

|XML şeması|Veri Kaynakları penceresi|
|----------------|-------------------------|
|Bir Office kullanır.|Veri **Kaynakları penceresini** Visual Studio.|
|XML dosyalarından verileri içeri Office dışarı aktarmaya olanak sağlayan yerleşik veri kaynağı özelliklerini sağlar.|İçeri ve dışarı aktarma işlevlerini program aracılığıyla sağlayabilirsiniz.|
|Oluşturulan denetimleri verilerle doldurmak için kod yazmanız gerekir.|Veri Kaynakları **penceresinden eklenen** denetimler, veritabanı sunucularını kullanırken gerekli bağlantı dizeleriyle birlikte bunları doldurmak için otomatik olarak oluşturulmuş kod içerir.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Şemaların Word belgelerine ekli olduğu davranış
 Veri nesneleri, belge düzeyinde bir belge düzeyi projesinde kullanılan bir Word belgesine şema Office oluşturulmaz. Ancak, bir şema öğesini belgenize eşleyebilirsiniz, denetimler oluşturulur. Denetim türü, eşley istediğiniz öğe türüne bağlıdır; yinelenen öğeler <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimler, tekrar etmeyen öğeler ise <xref:Microsoft.Office.Tools.Word.XMLNode> denetimler üretir. Daha fazla bilgi için bkz. [XMLNodes Denetimi](../vsto/xmlnodes-control.md) ve [XMLNode Denetimi.](../vsto/xmlnode-control.md)

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>XML şemaları içeren çözümlerin dağıtımı
 Bir belgeye eşlenmiş XML şeması kullanan bir çözüm dağıtmak için bir yükleyici oluşturmanız gerekir. Yükleyici, şemayı kullanıcının bilgisayarına şema kitaplığına kaydetmeli. Şemayı kaydetmezsiniz, çünkü Word kullanıcı açtığında belgede yer alan öğeleri temel alan geçici bir şema üretir. Ancak kullanıcı, projeyi oluşturmak için kullanılan şemaya karşı doğrulama gerçekleştiremayacak veya şemayı kaydedecek. Yükleyiciler hakkında daha fazla bilgi için [bkz. Uygulamaları, hizmetleri ve bileşenleri dağıtma.](../deployment/deploying-applications-services-and-components.md)

 Şemanın kitaplıkta ve kayıtlı olup olmadığını kontrol etmek için projenize kod da ekleyebilirsiniz. Böyle bir şey yoksa, kullanıcıyı uyarma.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl kullanılır: Şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Nasıl ekleyebilirsiniz: Şemaları çalışma sayfalarıyla eşleme Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
