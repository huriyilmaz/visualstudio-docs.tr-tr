---
title: 'Nasıl Yapılır: XML Şema Tasarımcısını XML Değişmez Değerleri ile Kullanma'
description: bir Visual Basic projesindeki bir xml sabit değeri ile ilişkili bir şemayı görüntülemek için xml şema tasarımcısını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: a9c97b0c5bf8224b31dcab1974b697c35150afed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130188"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Nasıl yapılır: XML şema tasarımcısını XML değişmez değerleri ile kullanma

bu konu, bir Visual Basic projesindeki bir XML sabit değeri ile ilişkili bir şemanın nasıl görüntüleneceğini açıklamaktadır.

## <a name="create-a-new-visual-basic-project"></a>yeni bir Visual Basic projesi oluştur

1. Visual Studio'yu açın.

2. **xmldeğişmezleri** adlı yeni bir Visual Basic **konsol uygulaması** projesi oluşturun.

     yeni proje bir Visual Basic kaynak dosyası ( *Module1. vb*) içerir.

## <a name="add-an-existing-xsd-file"></a>Mevcut bir XSD dosyası Ekle

1. Not Defteri yeni bir metin dosyası açın. XML şeması örnek kodunu, [satın alma siparişi şemasından](../xml-tools/sample-xsd-file-simple-schema.md) kopyalayın ve dosyasına yapıştırın.

2. Dosyayı *PurchaseOrderSchema. xsd* adlı bir konuma kaydedin.

3. **Çözüm Gezgini**, projenin adına sağ tıklayın, **Ekle**' yi seçin ve ardından **Varolan öğe**' yi seçin. **Addexıting öğesi** iletişim kutusu görüntülenir. *PurchaseOrderSchema. xsd* dosyasına gidin, seçin ve ardından **Ekle**' ye tıklayın.

     Xmlharfler projesi artık iki dosya içerir: *Module1. vb* ve *PurchaseOrderSchema. xsd*.

## <a name="add-code"></a>Kod Ekle

projeye dahil olan XSD dosyasını temel alan bir XML sabit değeri ile Visual Basic kodu eklemek için:

1. *Module1. vb* dosyasındaki kodu aşağıdaki kodla değiştirin:

   ```vb
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

   xml **şema gezgini** , xml şema kümesiyle ilişkili xml sabit değeri olan bir Visual Basic dosyası ile yan yana görüntülenir.
