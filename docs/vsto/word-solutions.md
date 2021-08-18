---
title: Word çözümleri
description: Word'u otomatikleştirmek Visual Studio Word özelliklerini genişletmek ve Word kullanıcı arabirimini (UI) özelleştirmek için Visual Studio çözümlerini nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 89de9e72f7ac8aa178b2a76a184a564857337d74
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046054"
---
# <a name="word-solutions"></a>Word çözümleri
  Visual Studio, Word'de belge düzeyinde özelleştirmeler oluşturmak ve VSTO için Microsoft Office sağlar. Word'u otomatikleştirmek, Word özelliklerini genişletmek ve Word kullanıcı arabirimini (UI) özelleştirmek için bu çözümleri kullanabilirsiniz. Belge düzeyi özelleştirmeler ile eklenti eklentileri arasındaki farklar hakkında daha fazla VSTO için bkz. [Office çözüm geliştirmeye genel &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:

- [Word'i otomatikleştirin.](#automating)

- [Word için belge düzeyinde özelleştirmeler geliştirin.](#doclevel)

- [Word VSTO eklentilerini geliştirin.](#applevel)

- [Word kullanıcı arabirimini özelleştirin.](#UI)

## <a name="automate-word"></a><a name="automating"></a> Word'i otomatikleştirme
 Word nesne modeli, Word'leri otomatikleştirmek için kullanabileceğiniz birçok türü gösterir. Örneğin program aracılığıyla tablolar oluşturabilir, belgeleri biçimlendirebilirsiniz ve metni aralıklar ve paragraflar olarak ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Word nesne modeline genel bakış.](../vsto/word-object-model-overview.md)

 Web'de Word Visual Studio, çözümleriniz içinde *konak öğelerini ve* *konak denetimlerini* de kullanabilirsiniz. Bunlar Word nesne modelinde yaygın olarak kullanılan ve nesneleri gibi belirli nesneleri genişleten <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.ContentControl> nesnelerdir. Genişletilmiş nesneler, temel alınan Word nesneleri gibi davranır, ancak nesnelere ek olaylar ve veri bağlama özellikleri ekler. Daha fazla bilgi için [bkz. Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme.](../vsto/automating-word-by-using-extended-objects.md)

## <a name="develop-document-level-customizations-for-word"></a><a name="doclevel"></a> Word için belge düzeyinde özelleştirmeler geliştirme
 Word için belge düzeyinde Microsoft Office, belirli bir belgeyle ilişkili bir derlemeden oluşur. Derleme genellikle kullanıcı arabirimini özelleştirerek ve Word'u otomatiklaştırarak belgeyi genişleter. Word'VSTO ilişkili bir eklentiden farklı olarak, özelleştirmede uygulayan işlevler yalnızca ilişkili belge Word'de açık olduğunda kullanılabilir.

 Word için belge düzeyinde bir özelleştirme projesi oluşturmak üzere, yeni belge oluşturma iletişim kutusundaki Word Belgesi veya Word **Project** proje şablonlarını Visual Studio. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

 Belge düzeyinde özelleştirmelerin nasıl iş olduğu hakkında daha fazla bilgi için, [Belge düzeyi özelleştirmelerin mimarisi.](../vsto/architecture-of-document-level-customizations.md)

### <a name="word-customization-programming-model"></a>Sözcük özelleştirme programlama modeli
 Word için belge düzeyinde bir proje ekleyebilirsiniz Visual Studio çözüme temel oluşturan `ThisDocument` adlı bir sınıf oluşturulur. Bu sınıf çözümünüzle ilişkili belgeyi temsil eder ve kodunuzu yazmak için bir başlangıç noktası sağlar.

 Sınıf ve belge düzeyi projesinde kullanabileceğiniz diğer özellikler hakkında daha fazla bilgi `ThisDocument` için bkz. [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-word"></a><a name="applevel"></a>Word VSTO eklentilerini geliştirme
 VSTO Word için bir Microsoft Office, Word tarafından yüklenen bir derlemeden oluşur. Derleme genellikle kullanıcı arabirimini özelleştirerek ve Word'u otomatiklaştırarak Word'u genişleter. Belirli bir belgeyle ilişkili olan belge düzeyinde özelleştirmeden farklı olarak, VSTO eklentisinde uygulayan işlevler tek bir belgeyle sınırlı değildir.

 Word için VSTO eklenti projesi oluşturmak için, yeni uygulamanın Yeni Project iletişim kutusunda Word **Visual Studio.** Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

 Eklentilerin nasıl VSTO genel bilgi için bkz. [VSTO Eklentilerinin Mimarisi.](../vsto/architecture-of-vsto-add-ins.md)

### <a name="word-add-in-programming-model"></a>Word Eklenti programlama modeli
 Word VSTO Eklenti projesini Visual Studio, çözüme temel oluşturan `ThisAddIn` adlı bir sınıf üretir. Bu sınıf kodunuzu yazmak için bir başlangıç noktası sağlar ve Word'in nesne modelini eklentinizin VSTO gösterir.

 Bir eklentide kullanabileceğiniz sınıf ve diğer özellikler hakkında daha `ThisAddIn` fazla bilgi VSTO bkz. Program VSTO [Eklentileri.](../vsto/programming-vsto-add-ins.md)

## <a name="customize-the-user-interface-of-word"></a><a name="UI"></a> Word'in kullanıcı arabirimini özelleştirme
 Word'in kullanıcı arabirimini özelleştirmenin birkaç farklı yolu vardır. Bazı seçenekler tüm proje türleri tarafından kullanılabilir ve diğer seçenekler yalnızca eklentilerde VSTO belge düzeyinde özelleştirmeler için kullanılabilir.

### <a name="options-for-all-project-types"></a>Tüm proje türleri için seçenekler
 Aşağıdaki tabloda hem belge düzeyi özelleştirmeler hem de eklentiler için kullanılabilen VSTO seçenekleri listelemektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Şeridi özelleştirin.|[Şerit'e genel bakış](../vsto/ribbon-overview.md)|
|Özelleştirilmiş Windows (belge düzeyinde özelleştirme için) veya açık herhangi bir belgeye (bir Belge Ekle için) Form denetimleri veya genişletilmiş Word denetimleri VSTO ekleyin.|[Nasıl kullanılır: Windows Formlar denetimleri Office ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Nasıl kullanılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Nasıl kullanılır: Word belgelerine yer işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Belge düzeyi özelleştirme seçenekleri
 Aşağıdaki tabloda, yalnızca belge düzeyinde özelleştirmeler için kullanılabilen özelleştirme seçenekleri listelemektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Belgeye bir eylemler bölmesi ekleyin.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)<br /><br /> [Nasıl kullanılır: Word belgelerine veya çalışma kitaplarını Excel bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Belge yüzeyine genişletilmiş XMLNode ve XMLNodes denetimleri ekleyin.|[Nasıl kullanılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Nasıl kullanılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>Eklenti VSTO seçenekleri
 Aşağıdaki tabloda, yalnızca eklentilerde kullanılabilen özelleştirme VSTO listele.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Özel bir görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)|Word nesne modeli tarafından sağlanan ana türlere genel bir bakış sağlar.|
|[Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)|Word çözümlerde kullanabileceğiniz genişletilmiş nesneler (tarafından [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sağlanır) hakkında bilgi sağlar.|
|[Windows Belgelerde form Office genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)|Word belgelerine Formlar Windows nasıl ekleyebilirsiniz?|
|[Adım adım kılavuz: Word için ilk belge düzeyi özelleştirmenizi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Word için temel bir belge düzeyi özelleştirmesi oluşturmayı gösterir.|
|[Kılavuz: Word için VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Word için Eklenti'VSTO temel bir uygulama oluşturma hakkında bilgi sağlar.|
|[Adım adım kılavuz: Bir belgeye çalışma zamanında bir belgeye VSTO ekleme](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Çalışma zamanında bir Windows Formlar düğmesi ve bir belgeye bir eklenti kullanarak bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> VSTO gösterir.|
|[Office geliştirmede Word 2010](/previous-versions/office/developer/office-2010/ff601860(v=office.14))|Word çözümleri geliştirmeyle ilgili makalelerin ve başvuru belgelerinin bağlantılarını sağlar (Office kullanarak Visual Studio).|
