---
title: VSTO eklenti projesindeki hizmetten veriye bağlama
description: Microsoft Word belgesine denetim eklemeyi, denetimleri MSDN Içerik hizmetinden alınan verilere bağlamayı ve çalışma zamanında olaylara yanıt vermeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b6993cb3eebc7641f4486bdc617ecb78e40aa05c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824534"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>İzlenecek yol: VSTO eklenti projesindeki bir hizmetten veriye bağlama
  VSTO eklenti projelerinde verileri konak denetimlerine bağlayabilirsiniz. Bu izlenecek yol, Microsoft Office bir Word belgesine nasıl denetim ekleneceğini, denetimlerin MSDN Içerik hizmetinden alınan verilere nasıl bağlanacağını ve çalışma zamanında olaylara nasıl yanıt verileceğini gösterir.

 **Uygulama hedefi:** Bu konudaki bilgiler Word 2010 için uygulama düzeyi projelere yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma zamanında <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belgeye denetim ekleme.

- <xref:Microsoft.Office.Tools.Word.RichTextContentControl>Denetimi bir Web hizmetinden veriye bağlama.

- <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>Bir denetimin olayına yanıt verme <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-project"></a>Yeni proje oluşturma
 İlk adım, bir Word VSTO eklenti projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Visual Basic veya C# kullanarak **MTPS Içerik hizmeti** adlı BIR Word VSTO eklentisi projesi oluşturun.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio, `ThisAddIn.vb` veya `ThisAddIn.cs` dosyasını açar ve projeyi **Çözüm Gezgini** ekler.

## <a name="add-a-web-service"></a>Web hizmeti Ekle
 Bu izlenecek yol için, MTPS Içerik hizmeti adlı bir Web hizmeti kullanın. Bu Web hizmeti, bir XML dizesi veya düz metin biçiminde belirtilen bir MSDN makalesindeki bilgileri döndürür. Daha sonraki bir adımda, döndürülen bilgilerin bir içerik denetiminde nasıl görüntüleneceği gösterilmektedir.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>MTPS içerik hizmetini projeye eklemek için

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' ye tıklayın.

2. **Veri kaynağı Yapılandırma sihirbazında** **hizmet**' e ve ardından **İleri**' ye tıklayın.

3. **Adres** alanına aşağıdaki URL 'yi yazın:

   `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

4. **Git**' e tıklayın.

5. **Ad alanı** alanında **contentservice** yazın ve **Tamam**' a tıklayın.

6. **Başvuru ekleme Sihirbazı** Iletişim kutusunda **son**' a tıklayın.

## <a name="add-a-content-control-and-bind-to-data-at-run-time"></a>Çalışma zamanında içerik denetimi ekleme ve verilere bağlama
 VSTO eklenti projelerinde, çalışma zamanında denetimleri ekler ve bağlar. Bu izlenecek yol için, Kullanıcı denetimin içine tıkladığında, içerik denetimini Web hizmetinden veri almaya yönelik şekilde yapılandırın.

### <a name="to-add-a-content-control-and-bind-to-data"></a>İçerik denetimi eklemek ve verilere bağlamak için

1. Sınıfında, `ThisAddIn` MTPS Içerik hizmeti, içerik denetimi ve veri bağlama için değişkenleri bildirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet2":::

2. Sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Bu yöntem, etkin belgenin başlangıcında bir içerik denetimi oluşturur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet4":::

3. Sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Bu yöntem, Web hizmetine bir istek oluşturmak ve göndermek için gereken nesneleri başlatır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet6":::

4. Kullanıcı içerik denetiminin içini tıklattığında ve verileri içerik denetimine bağladığında içerik denetimleri hakkında MSDN Kitaplığı belgesini almak için bir olay işleyicisi oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet5":::

5. `AddRichTextControlAtRange` `InitializeServiceObjects` Yönteminden ve yöntemlerini çağırın `ThisAddIn_Startup` . C# programcıları için bir olay işleyicisi ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet3":::

## <a name="test-the-add-in"></a>Eklentiyi test etme
 Word 'Ü açtığınızda <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Denetim görüntülenir. Denetimdeki metin, içinde tıkladığınızda değişir.

### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisini test etmek için

1. **F5** tuşuna basın.

2. İçerik denetiminin içine tıklayın.

     Bilgiler, MTPS Içerik hizmetinden indirilir ve içerik denetimi içinde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
