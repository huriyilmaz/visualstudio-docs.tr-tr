---
title: Word çözümleri
description: word 'ü otomatikleştirebilmek, word özelliklerini genişletmek ve word kullanıcı arabirimini (uı) özelleştirmek için Visual Studio çözümlerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 99db8e596032e67f2d2bc0cc4794e116af70412a225bfa201686949c53b68f9d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121225627"
---
# <a name="word-solutions"></a>Word çözümleri
  Visual Studio, Microsoft Office Word için belge düzeyi özelleştirmeler ve VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. Bu çözümleri, Word 'Ü otomatikleştirmek, Word özelliklerini genişletmek ve Word Kullanıcı arabirimini (UI) özelleştirmek için kullanabilirsiniz. belge düzeyi özelleştirmeleri ve VSTO eklentileri arasındaki farklılıklar hakkında daha fazla bilgi için, bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:

- [Word 'Ü otomatikleştirin](#automating).

- [Word için belge düzeyi özelleştirmeleri geliştirin](#doclevel).

- [Word için VSTO eklentileri geliştirin](#applevel).

- [Word 'ün Kullanıcı arabirimini özelleştirin](#UI).

## <a name="automate-word"></a><a name="automating"></a> Word 'Ü Otomatikleştir
 Word nesne modeli, Word 'Ü otomatikleştirebilmek için kullanabileceğiniz birçok türü ortaya çıkarır. Örneğin, programlama yoluyla tablo oluşturabilir, belgeleri biçimlendirebilir ve metin aralıklarını ve paragrafları ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).

 Visual Studio ' de Word çözümleri geliştirirken, çözümlerinizde *konak öğelerini* ve *konak denetimlerini* de kullanabilirsiniz. Bunlar, ve nesneleri gibi Word nesne modelinde yaygın olarak kullanılan belirli nesneleri genişleten nesnelerdir <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.ContentControl> . Genişletilmiş nesneler, temel aldığı Word nesneleri gibi davranır, ancak nesnelere ek olaylar ve veri bağlama özellikleri ekler. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-word"></a><a name="doclevel"></a> Word için belge düzeyi özelleştirmeleri geliştirme
 Microsoft Office Word için belge düzeyi özelleştirmesi, belirli bir belgeyle ilişkili bir derlemeden oluşur. Derleme, genellikle, Kullanıcı arabirimini özelleştirerek ve Word 'Ü otomatikleştirerek belgeyi genişletir. word ile ilişkili olan VSTO eklentisinin aksine, bir özelleştirmeye uyguladığınız işlevsellik yalnızca ilişkili belge Word 'de açık olduğunda kullanılabilir.

 word için belge düzeyi özelleştirme projesi oluşturmak için, Visual Studio **yeni Project** iletişim kutusundaki word belgesi veya word şablonu proje şablonları ' nı kullanın. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Belge düzeyi özelleştirmelerinin nasıl çalıştığı hakkında daha fazla bilgi için [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md).

### <a name="word-customization-programming-model"></a>Word özelleştirme programlama modeli
 Word için belge düzeyi projesi oluşturduğunuzda Visual Studio, çözümünüzün temeli olan adlı bir sınıf oluşturur `ThisDocument` . Bu sınıf, çözümünüzle ilişkili belgeyi temsil eder ve kodunuzu yazmak için bir başlangıç noktası sağlar.

 `ThisDocument`Belge düzeyi projede kullanabileceğiniz sınıf ve diğer özellikler hakkında daha fazla bilgi için, bkz. [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-word"></a><a name="applevel"></a>Word için VSTO eklentileri geliştirin
 Microsoft Office word için VSTO eklentisi word tarafından yüklenen bir derlemeden oluşur. Derleme tipik olarak, Kullanıcı arabirimini özelleştirerek ve Word 'Ü otomatikleştirerek Word 'Ü genişletir. belirli bir belgeyle ilişkili olan belge düzeyi özelleştirmesinden farklı olarak, bir VSTO eklentisi içinde uyguladığınız işlevsellik tek bir belgeyle sınırlı değildir.

 word için VSTO bir eklenti projesi oluşturmak için, Visual Studio **yeni Project** iletişim kutusundaki word eklentisi proje şablonlarını kullanın. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

 VSTO eklentilerin nasıl çalıştığı hakkında genel bilgi için bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

### <a name="word-add-in-programming-model"></a>Word eklenti programlama modeli
 bir Word VSTO eklentisi projesi oluşturduğunuzda Visual Studio, çözümünüzün temeli olan adlı bir sınıf oluşturur `ThisAddIn` . bu sınıf, kodunuzun yazılması için bir başlangıç noktası sağlar ve ayrıca, VSTO eklentinize Word nesne modelini de gösterir.

 `ThisAddIn`bir VSTO eklentisi içinde kullanabileceğiniz sınıf ve diğer özellikler hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-word"></a><a name="UI"></a> Word 'ün Kullanıcı arabirimini özelleştirme
 Word 'ün Kullanıcı arabirimini özelleştirmenin birkaç farklı yolu vardır. bazı seçenekler tüm proje türleri için kullanılabilir ve diğer seçenekler yalnızca VSTO eklentileri veya belge düzeyi özelleştirmeleri için kullanılabilir.

### <a name="options-for-all-project-types"></a>Tüm proje türleri için seçenekler
 aşağıdaki tabloda hem belge düzeyi özelleştirmeleri hem de VSTO eklentileri için kullanılabilen özelleştirme seçenekleri listelenmektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Şeridi özelleştirin.|[Şerite genel bakış](../vsto/ribbon-overview.md)|
|özelleştirilmiş belgeye (belge düzeyi özelleştirmesi için) veya herhangi bir açık belgeye (bir VSTO eklentisi için) Windows Forms denetimleri veya genişletilmiş sözcük denetimleri ekleyin.|[nasıl yapılır: Office belgelere Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Nasıl yapılır: Word belgelerine yer işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Belge düzeyi özelleştirmeleri seçenekleri
 Aşağıdaki tabloda yalnızca belge düzeyinde özelleştirmeler için kullanılabilen özelleştirme seçenekleri listelenmektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Belgeye bir eylemler bölmesi ekleyin.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)<br /><br /> [nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Belge yüzeyine genişletilmiş XMLNode ve XMLNodes denetimleri ekleyin.|[Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>VSTO eklentileri seçenekleri
 aşağıdaki tabloda yalnızca VSTO eklentileri için kullanılabilen özelleştirme seçenekleri listelenmektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Özel bir görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)|Word nesne modeli tarafından sağlanan ana türlere genel bir bakış sağlar.|
|[Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)|Word çözümlerinde kullanabileceğiniz Genişletilmiş nesneler (tarafından sağlanan) hakkında bilgiler sağlar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|
|[Windows Office belgelere genel bakış üzerinde form denetimleri](../vsto/windows-forms-controls-on-office-documents-overview.md)|Word belgelerine nasıl Windows Forms denetimleri ekleyebileceğiniz açıklanmaktadır.|
|[İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Word için temel bir belge düzeyi özelleştirmesi oluşturmayı gösterir.|
|[izlenecek yol: Word için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Word için temel bir VSTO eklentisinin nasıl oluşturulacağını gösterir.|
|[izlenecek yol: bir VSTO eklentisi içinde çalışma zamanında belgeye denetim ekleme](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> VSTO eklentisi kullanarak çalışma zamanında bir Windows Forms düğme ve bir belgeye nasıl ekleneceğini gösterir.|
|[Office geliştirmede Word 2010](/previous-versions/office/developer/office-2010/ff601860(v=office.14))|Word çözümlerini geliştirme (Visual Studio kullanarak Office geliştirmeye özgü değil) hakkındaki makalelere ve başvuru belgelerine bağlantılar sağlar.|
