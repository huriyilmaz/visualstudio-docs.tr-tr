---
title: 'Nasıl yapılır: XML şema tasarımcısını XML değişmez değerleri ile kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656287"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Nasıl Yapılır: XML Şema Tasarımcısını XML Değişmez Değerleri ile Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, bir Visual Basic projesindeki bir XML sabit değeri ile ilişkili bir şemanın nasıl görüntüleneceğini açıklamaktadır.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>Yeni bir Visual Basic konsol uygulaması projesi oluşturmak için

1. Visual Studio 2010 ' i başlatın.

2. **Dosya** menüsünde **Yeni**' yi ve ardından **Proje**' yi seçin. **Yeni Proje** iletişim kutusu görünür. **Proje türleri**Için **diğer diller '** i seçin ve ardından **Visual Basic**' yi seçin. **Şablonlar**Için konsol uygulaması ' nı seçin. Ardından `XMLLiterals` **ad** alanını ve **konum** alanına proje konumunu yazın. **Tamam**’a tıklayın.

     Yeni poject oluşturulur. Xmlsabit değerler projesi bir Visual Basic kaynak dosyası (Module1. vb) içerir.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Projeye var olan bir XSD dosyasını eklemek için

1. Not defteri 'nde yeni bir metin dosyası açın. XML şeması örnek kodunu, [satın alma siparişi şemasından](../xml-tools/sample-xsd-file-simple-schema.md) kopyalayın ve dosyasına yapıştırın.

2. Dosyayı PurchaseOrderSchema. xsd adlı bir konuma kaydedin.

3. Çözüm Gezgini, projenin adına sağ tıklayın, **Ekle**' yi seçin ve ardından **var olan öğe... öğesini**seçin. **Addexıting öğesi** iletişim kutusu görüntülenir. PurchaseOrderSchema. xsd dosyasına gidin, seçin ve ardından **Ekle**' ye tıklayın.

     Xmlharfler projesi artık iki dosya içerir: Module1. vb ve PurchaseOrderSchema. xsd.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Projeye dahil olan XSD dosyasını temel alan bir XML sabit değeri ile Visual Basic kodu eklemek için

1. Module1. vb dosyasındaki kodu aşağıdaki kodla değiştirin:

    ```
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

    Module Module1
        Sub Main()

            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                                 <ns:ShipTo country="US">
                                     <ns:name>name1</ns:name>
                                     <ns:street>street1</ns:street>
                                     <ns:city>city1</ns:city>
                                     <ns:state>state1</ns:state>
                                     <ns:zip>1</ns:zip>
                                 </ns:ShipTo>
                                 <ns:BillTo country="US">
                                     <ns:name>name1</ns:name>
                                     <ns:street>street1</ns:street>
                                     <ns:city>city1</ns:city>
                                     <ns:state>state1</ns:state>
                                     <ns:zip>1</ns:zip>
                                 </ns:BillTo>
                             </ns:PurchaseOrder>

        End Sub
    End Module
    ```

2. XML sabit değerinde bir xml düğümüne veya XML ad alanı içeri aktarma öğesine sağ tıklayın ve **şema Gezgininde göster**' i seçin.

     XML şema Gezgini, XML şema kümesi ile XML sabit değeri olan bir Visual Basic dosyası ile yan yana görüntülenir.
