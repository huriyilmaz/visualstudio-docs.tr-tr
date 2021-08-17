---
title: Özel XML bölümlerine genel bakış
description: bazı Microsoft Office uygulamaları için belgelere XML verilerini nasıl katıştıracağınızı öğrenin. XML verilerini bir belgeye katıştırdığınızda, veriler özel bir XML parçası olarak adlandırılır.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: dfa45ffc37ffdbdabbb35d043b43e5005098d0d8b30554e110a724dfba5922fe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394816"
---
# <a name="custom-xml-parts-overview"></a>Özel XML bölümlerine genel bakış
  bazı Microsoft Office uygulamaları için belgelere XML verisi ekleyebilirsiniz. XML verilerini bir belgeye katıştırdığınızda, veriler *Özel BIR XML parçası* olarak adlandırılır.

 Visual Studio bir VSTO eklenti veya belge düzeyi çözümü kullanarak bir belgede özel XML bölümleri oluşturabilir ve değiştirebilirsiniz. özel XML parçalarını oluşturmak ve değiştirmek için Microsoft Office uygulamayı başlatmanız gerekmez.

 **Uygulama hedefi:** bu konudaki bilgiler, Excel, PowerPoint ve Word için belge düzeyi projelere ve VSTO eklenti projelerine yöneliktir. daha fazla bilgi için bkz. [Office uygulama ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Visual Studio ayrıca, belge düzeyi özelleştirmelerde veri nesnelerini önbelleğe almanıza olanak sağlar. Bu özellik özel XML bölümlerinden farklıdır, ancak bazı benzerlikler vardır. Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md).

## <a name="understand-custom-xml-parts"></a>Özel XML parçalarını anlama
 özel xml parçaları 2007 Microsoft Office sisteminde, Open XML biçimleriyle birlikte sunulmuştur. bu biçimler Excel, PowerPoint ve Word için yeni XML tabanlı dosya biçimlerini ( *.xlsx*, *.pptx* ve *.docx* gibi) içerir. Bu biçimlerdeki belgeler, bir ZIP arşivinde klasörler halinde düzenlenmiş XML dosyalarından ( *XML parçaları* olarak da adlandırılır) oluşur. XML bölümlerinin çoğu, belgenin yapısını ve durumunu tanımlamaya yardımcı olan yerleşik bölümlerdir. Ancak belgeler, belgelerde rastgele XML verilerini depolamak için kullanabileceğiniz özel XML parçalarını da içerebilir.

 XML dosyası biçimleri, uygulamaların, eski ikili dosya biçimleri ( *.xls*, *.ppt* ve *.doc* gibi) mümkün olmayan yöntemlerle belgelerle çalışmasını sağlar. zıp arşivlerini okuyabilen herhangi bir uygulama, Microsoft Office yüklü olmasa bile belgelerin içeriğini inceleyebilir ve değiştirebilir.

 Açık XML ve özel XML bölümlerinin yapısı hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Office (2007) Open XML dosya biçimlerini tanıtma](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Nasıl yapılır: açık XML biçimleri belgelerini Işleme](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [İzlenecek yol: Word 2007 XML biçimi](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Open XML biçimlerini kullanarak Word 2007 belgeleri oluşturun](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> Excel, Word ve PowerPoint, ikili dosya biçimlerinde kaydedilmiş belgelerde özel XML parçalarını kullanmanıza da olanak tanır. ancak, bir belge ikili biçimde kaydedilirse, Microsoft Office uygulamayı başlatmadan özel XML parçalarını ekleyemez veya değiştiremezsiniz.

## <a name="create-and-modify-custom-xml-parts"></a>Özel XML parçalarını oluşturma ve değiştirme
 belge Office uygulamada açık olduğunda veya Microsoft Office yüklü olmasa bile belge kapatıldığında özel XML bölümleri oluşturabilir veya değiştirebilirsiniz.

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Office uygulama çalışırken XML parçalarını değiştirme
 belge düzeyi özelleştirmesi veya VSTO eklentisi kullanarak özel XML parçalarıyla çalışabilirsiniz. Belge düzeyi özelleştirmesi kullanıyorsanız, genellikle özelleştirilmiş belgedeki özel XML parçalarıyla çalışırsınız. VSTO eklentisi kullanıyorsanız, uygulamada açık olan herhangi bir belgede özel XML bölümleri oluşturabilir veya değiştirebilirsiniz.

 Visual Studio kullanarak özel bir XML bölümü oluşturmak için, belgede koleksiyona yeni bir ekleyin <xref:Microsoft.Office.Core.CustomXMLPart> <xref:Microsoft.Office.Core.CustomXMLParts> . Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [nasıl yapılır: VSTO eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Office uygulaması başlatmadan XML parçalarını değiştirme
 Excel, PowerPoint veya Word 'ü başlatmadan özel bir XML bölümü ekleyebilir veya düzenleyebilirsiniz. bu, bir sunucu gibi Microsoft Office uygulamaları yüklü olmayan bir bilgisayardaki bir belgede XML verileriyle çalışmak istiyorsanız yararlıdır.

 Microsoft Office başlatmadan özel bir xml bölümü eklemek için, Open xml SDK 'sında sınıfları kullanın. bu sınıflar, Office belgelerine özgü açık XML içeriğine erişim sağlamak için tasarlanmıştır. örneğin, bir Excel çalışma kitabına özel bir XML bölümü eklemek için, <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> bir nesnenin yöntemini kullanırsınız <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> . Daha fazla bilgi için bkz. [Open XML SDK](/office/open-xml/open-xml-sdk).

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Özel XML parçalarını Word içerik denetimlerine bağlama
 Bir Word çözümünde içerik denetimlerini özel bir XML bölümünde bulunan öğelere bağlayabilirsiniz. Bir içerik denetimi özel bir XML bölümüne bağlandığında, özel XML bölümündeki veriler içerik denetiminin Kullanıcı arabiriminde (UI) görüntülenir. Kullanıcı denetimdeki metni düzenlerse, karşılık gelen XML öğesi otomatik olarak güncelleştirilir. Benzer şekilde, özel XML bölümlerinin öğe değerleri değiştirilirse, XML öğelerine bağlanan içerik denetimleri yeni verileri görüntüler. Daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [nasıl yapılır: VSTO eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [İçerik denetimleri](../vsto/content-controls.md)
- [İzlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
