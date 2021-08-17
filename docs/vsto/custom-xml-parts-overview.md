---
title: Özel XML bölümlerine genel bakış
description: Bazı uygulama uygulamaları için belgelerde XML verilerini nasıl Microsoft Office öğrenin. Bir belgeye XML verileri eklerken, veriler özel XML bölümü olarak adlandırılmıştır.
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
ms.openlocfilehash: 9ac6edf5bbd05ee2f2b94c79208c7f72de270e7f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026635"
---
# <a name="custom-xml-parts-overview"></a>Özel XML bölümlerine genel bakış
  Xml verilerini bazı uygulamalar için belgelere Microsoft Office. Bir belgeye XML verileri eklerken, veriler özel XML *bölümü olarak adlandırılmıştır.*

 Bir belge içinde özel XML bölümleri oluşturmak ve değiştirmek için VSTO eklenti veya belge düzeyi çözümü Visual Studio. Özel XML parçaları oluşturmak ve değiştirmek Microsoft Office uygulamanın ilk başlatması gerek değildir.

 **Aşağıdakiler için geçerlidir:** Bu konu başlığı altında yer alan bilgiler belge düzeyi projeler ve VSTO, PowerPoint ve Word için Excel projeleri için geçerlidir. Daha fazla bilgi için [bkz. Uygulama ve Office tarafından kullanılabilen özellikler.](../vsto/features-available-by-office-application-and-project-type.md)

> [!NOTE]
> Visual Studio, veri nesnelerini belge düzeyinde özelleştirmelerde önbelleğe alasınız. Bazı benzerlikler olsa da bu özellik özel XML parçalarından farklıdır. Daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler.](../vsto/cached-data-in-document-level-customizations.md)

## <a name="understand-custom-xml-parts"></a>Özel XML parçalarını anlama
 Özel XML parçaları, Open XML Biçimleriyle birlikte 2007 Microsoft Office sistemiyle birlikte tanıtıldı. Bu biçimler Excel, PowerPoint ve Word *(.xlsx,*.pptx *ve*.docxgibi) için yeni XML tabanlı *dosya biçimlerini içerir.* Bu biçimlerde belgeler, ZIP arşivinde klasörlerde düzenlenmiş XML dosyalardan *(XML* bölümleri olarak da adlandırılmıştır) oluşur. XML parçalarının çoğu, belgenin yapısını ve durumunu tanımlamaya yardımcı olan yerleşik parçalardır. Ancak belgeler, belgelerde rastgele XML verilerini depolamak için kullanabileceğiniz özel XML bölümleri de içerebilir.

 XML dosya biçimleri, uygulamaların belgelerle eski ikili dosya biçimleriyle (.xls *,* *.ppt* ve.docgibi) *çalışmalarına olanak tanır.* ZIP arşivlerini okuyabilen herhangi bir uygulama, yüklenmemiş olsa bile belgelerin içeriğini Microsoft Office ve değiştirebilir.

 Open XML ve özel XML parçalarının yapısı hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Office (2007) Open XML dosya biçimlerine tanıtma](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Nasıl kullanılır: Open XML biçimlerini işleme belgeleri](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [Kılavuz: Word 2007 XML biçimi](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Open XML biçimlerini kullanarak Word 2007 belgeleri derleme](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> Excel, Word ve PowerPoint, ikili dosya biçimlerinde kaydedilen belgelerde özel XML bölümleri de kullanmanızı sağlar. Ancak, bir belge ikili biçimde kaydedilirse, özel XML parçalarını uygulamanıza başlamadan ek Microsoft Office değiştiremezsiniz.

## <a name="create-and-modify-custom-xml-parts"></a>Özel XML bölümleri oluşturma ve değiştirme
 Belge Office uygulamasında açık olduğunda veya belge kapatıldıklarında (yüklü olsa bile) özel XML bölümleri oluşturabilir Microsoft Office değiştirebilirsiniz.

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Uygulama çalışırken XML Office değiştirme
 Özel XML bölümleriyle çalışmak için belge düzeyi özelleştirme veya VSTO kullanabilirsiniz. Belge düzeyinde özelleştirme kullanıyorsanız, genellikle özelleştirilmiş belgede yer alan özel XML bölümleriyle çalışırsınız. Yeni bir Eklenti VSTO, uygulamada açık olan herhangi bir belgede özel XML bölümleri oluşturabilir veya değiştirebilirsiniz.

 Visual Studio kullanarak özel bir XML bölümü oluşturmak için, belgede <xref:Microsoft.Office.Core.CustomXMLPart> <xref:Microsoft.Office.Core.CustomXMLParts> koleksiyona yeni bir ekleyin. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Nasıl yapılır: Belge düzeyinde özelleştirmelere özel XML parçaları ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Nasıl kullanılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Office uygulamasını başlatmadan XML Office değiştirme
 Bir özel XML bölümünü, PowerPoint veya Word'Excel başlatmadan ekleyebilir veya değiştirebilirsiniz. Bu, xml verileriyle sunucu gibi yüklü uygulama yüklü Microsoft Office bilgisayarda bir belgede çalışmak istediğiniz durumlarda kullanışlıdır.

 Özel BIR XML bölümü eklemek için Microsoft Office Open XML SDK'sı sınıflarını kullanın. Bu sınıflar, belgelere özgü Open XML içeriğine erişim Office tasarlanmıştır. Örneğin, bir çalışma kitabına özel bir XML Excel eklemek için nesnesinin <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> yöntemini <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> kullanırsınız. Daha fazla bilgi için bkz. [Open XML SDK](/office/open-xml/open-xml-sdk).

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Özel XML parçalarını Word içerik denetimlerine bağlama
 Word çözümünde içerik denetimlerini özel BIR XML parçasının öğelerine bebilirsiniz. Bir içerik denetimi özel bir XML parçasına bağlı olduğunda, özel XML parçasında yer alan veriler içerik denetimi kullanıcı arabiriminde (UI) görüntülenir. Kullanıcı denetimdeki metni düzenlerse, ilgili XML öğesi otomatik olarak güncelleştirilir. Benzer şekilde, özel XML parçalarında öğe değerleri değiştirilirse, XML öğelerine bağlı içerik denetimleri yeni verileri görüntüler. Daha fazla bilgi için bkz. [İçerik denetimleri.](../vsto/content-controls.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyinde özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Nasıl yapılır: Belge düzeyinde özelleştirmelere özel XML parçaları ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [Nasıl kullanılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [İçerik denetimleri](../vsto/content-controls.md)
- [Adım adım kılavuz: İçerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
