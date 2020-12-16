---
title: Belge düzeyi özelleştirmelerde XML şemaları ve verileri
description: Microsoft Excel ve Word, şemaları belgelerinize eşleme yeteneği sağlar ve XML verilerini belgeye içeri ve dışarı aktarmayı basitleştirebilirler.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57fad7982f762c4837399e12552cd109c9a9086c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527858"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Belge düzeyi özelleştirmelerde XML şemaları ve verileri
  **Önemli** Microsoft Word ile ilgili bu konu başlığı altında verilen bilgiler, Microsoft Word 'deki özel XML ile ilgili belirli bir işlevselliğin uygulanmasını kaldırdıkları zaman, Birleşik Devletler ve bölgeleri dışında bulunan veya Microsoft tarafından Microsoft tarafından lisanslanan Microsoft Word ürünleri, Microsoft 'un Microsoft Word ile ilgili belirli işlevlerin bir uygulamasını kaldırdığınızda Microsoft 'un 2010 Ocak 'tan önce lisanslı olduğu kişiler ve kuruluşların avantajı ve kullanımı için özel olarak sunulur. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler veya şirket içinde çalışan ya da Microsoft tarafından, 10 Ocak 2010 ' den sonra Microsoft tarafından lisanslanan Microsoft Word ürünlerini kullanan bireyler veya kuruluşlar tarafından okunamaz veya kullanılmıyor olabilir. Bu ürünler, bu tarihten önce lisanslanan ürünlerle aynı veya satın alınmadan ve Birleşik Devletler dışında kullanılmak üzere lisanslanmaz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Excel ve Microsoft Office Word 'Ü Microsoft Office şemaları belgelerinize eşleme yeteneği sağlar. Bu özellik, XML verilerinin belgeye içeri ve dışarı aktarılmasını kolaylaştırabilir.

 Visual Studio, belge düzeyi özelleştirmelerde eşlenen şema öğelerini programlama modelinde denetim olarak kullanıma sunar. Excel için, Visual Studio, denetimleri veritabanlarındaki, Web hizmetlerindeki ve nesnelerdeki verilere bağlama desteği ekler. Word ve Excel için, Visual Studio, çözümleriniz için gelişmiş bir son kullanıcı deneyimi oluşturmak üzere şema eşlemeli bir belgeyle birlikte kullanılabilecek eylemler bölmesi için destek ekler. Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

> [!NOTE]
> Excel çözümlerinde çok parçalı XML şemaları kullanamazsınız.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Şemalar Excel çalışma kitaplarına eklendiğinde oluşturulan nesneler
 Bir çalışma kitabına şema iliştirmeye çalıştığınızda, Visual Studio otomatik olarak birkaç nesne oluşturur ve bunları projenize ekler. Bu nesneler, Excel tarafından yönetildiklerinden, Visual Studio araçları kullanılarak silinmemelidir. Bunları silmek için, eşlenen öğeleri çalışma sayfasından kaldırın veya Excel araçlarını kullanarak şemayı ayırın.

 İki ana nesne vardır:

- XML şeması (XSD dosyası). Visual Studio, çalışma kitabındaki her şema için projeye bir şema ekler. Bu, **Çözüm Gezgini** içinde xsd uzantılı bir proje öğesi olarak görünür.

- Türü belirtilmiş bir <xref:System.Data.DataSet> sınıf. Bu sınıf, şemaya göre oluşturulur. Bu veri kümesi sınıfı **sınıf görünümü** görünür.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Şema öğeleri Excel çalışma sayfalarına eşlendiğinde oluşturulan nesneler
 **XML kaynağı** görev bölmesinden bir şema öğesini bir çalışma sayfasına eşlediğinizde, Visual Studio otomatik olarak birkaç nesne oluşturur ve bunları projenize ekler:

- Kontrollerini. Çalışma kitabındaki her eşlenmiş nesne için, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> programlama modelinde bir denetim (tekrarlamayan şema öğeleri için) veya bir <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim (yinelenen şema öğeleri için) oluşturulur. <xref:Microsoft.Office.Tools.Excel.ListObject>Denetim yalnızca eşlemeler ve eşlenmiş nesneler çalışma kitabından silinerek silinebilir. Denetimler hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

- Listeye. <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Çalışma sayfasına tekrarsız bir şema öğesi eşleyerek bir oluşturduğunuzda, bir <xref:System.Windows.Forms.BindingSource> oluşturulur ve <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Denetim öğesine bağlanır <xref:System.Windows.Forms.BindingSource> . <xref:System.Windows.Forms.BindingSource>Oluşturulan bir sınıfın örneği gibi, öğesini belgeyle eşleştirilmiş şemayla eşleşen bir veri kaynağı örneğine bağlamanız gerekir <xref:System.Data.DataSet> . <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> **Özellikler** penceresinde gösterilen ve özelliklerini ayarlayarak bağlamayı oluşturun.

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>Nesneler için oluşturulmaz <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> **Özellikler** penceresinde ve özelliklerini ayarlayarak veri kaynağına el ile bağlamanız gerekir.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office eşlenmiş şemalar ve Visual Studio veri kaynakları penceresi
 Office ve Visual Studio **veri kaynakları** penceresinin eşlenmiş şema işlevselliği, raporlama veya düzenlemeyle Ilgili bir Excel çalışma sayfasındaki verileri sunmanıza yardımcı olabilir. Her iki durumda da, Excel çalışma sayfasına veri öğelerini sürükleyebilirsiniz. Her iki yöntem de bir veya bir Web hizmeti gibi bir veri kaynağı ile veri bağlantılı denetimler oluşturur <xref:System.Windows.Forms.BindingSource> <xref:System.Data.DataSet> .

> [!NOTE]
> Bir yinelenen şema öğesini bir çalışma sayfasına eşlediğinizde, Visual Studio bir oluşturur <xref:Microsoft.Office.Tools.Excel.ListObject> . , <xref:Microsoft.Office.Tools.Excel.ListObject> Üzerinden verilere otomatik olarak bağlanmadı <xref:System.Windows.Forms.BindingSource> . <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> **Özellikler** penceresinde ve özelliklerini ayarlayarak veri kaynağına el ile bağlamanız gerekir.

 Aşağıdaki tabloda, iki yöntem arasındaki bazı farklılıklar gösterilmektedir.

|XML şeması|Veri Kaynakları penceresi|
|----------------|-------------------------|
|Office arabirimini kullanır.|Visual Studio 'da **veri kaynakları** penceresini kullanır.|
|XML dosyalarından verileri içeri ve dışarı aktarmaya yönelik yerleşik Office özelliklerini sunar.|Program aracılığıyla içeri ve dışarı aktarma işlevselliği sağlamanız gerekir.|
|Oluşturulan denetimleri verilerle doldurmanız için kod yazmanız gerekir.|**Veri kaynakları** penceresinden eklenen denetimlerin, veritabanı sunucularını kullanırken gerekli bağlantı dizeleriyle birlikte onları dolduracak şekilde otomatik olarak oluşturulduğu kod vardır.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Şemaları Word belgelerine İliştirme durumu
 Belge düzeyi Office projesinde kullanılan Word belgesine bir şema iliştirçalıştığınızda veri nesneleri oluşturulmaz. Ancak, belgenize bir şema öğesi eşlediğinizde denetimler oluşturulur. Denetimin türü, eşlemenizi yaptığınız öğe türüne bağlıdır; Yinelenen öğeler <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimleri ve yinelenmeyen öğeleri <xref:Microsoft.Office.Tools.Word.XMLNode> denetimleri oluşturur. Daha fazla bilgi için bkz. [XMLNodes denetimi](../vsto/xmlnodes-control.md) ve [XMLNode denetimi](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>XML şemaları içeren çözümlerin dağıtımı
 Bir belgeye eşlenmiş bir XML şeması kullanan bir çözümü dağıtmak için bir yükleyici oluşturmanız gerekir. Yükleyici, şemayı kullanıcının bilgisayarındaki şema kitaplığına kaydetmelidir. Şemayı kaydetmeyin, Word Kullanıcı tarafından açıldığında belgedeki öğeleri temel alan geçici bir şema oluşturduğundan çözüm çalışmaya devam edecektir. Ancak Kullanıcı, projeyi oluşturmak için kullanılan şemaya karşı doğrulama gerçekleştiremez veya kaydedebilir. Yükleyiciler hakkında daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

 Ayrıca, şemanın kitaplıkta olup olmadığını denetlemek için projenize kod ekleyebilir ve kaydolmasını sağlayabilirsiniz. Değilse, kullanıcıyı uyarabilirsiniz.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
