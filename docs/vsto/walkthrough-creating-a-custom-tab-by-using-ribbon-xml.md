---
title: 'İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma'
description: Add-Ins sekmesine düğme ekleme ve şeriti (XML) kullanarak Microsoft Word otomatikleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2aec6648b1a432166f4ba9205fb07beef91f5ebf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147563"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma
  Bu izlenecek yol, **Şerit (XML)** öğesini kullanarak nasıl özel Şerit sekmesinin oluşturulduğunu gösterir.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- **Eklentiler** sekmesine düğmeler ekleme. **Eklentiler** sekmesi, Şerit XML dosyasında tanımlanan varsayılan sekmedir.

- **eklentiler** sekmesindeki düğmeleri kullanarak Microsoft Office Word 'ü otomatikleştirme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Proje oluşturma
 ilk adım, bir Word VSTO eklentisi projesi oluşturmaktır. Daha sonra bu belgenin **Eklentiler** sekmesini özelleştireceğinizi göreceksiniz.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **MyRibbonAddIn** adlı bir **Word eklenti** projesi oluşturun.

     daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn. cs** veya **ThisAddIn. vb** kod dosyasını açar ve **Çözüm Gezgini** **MyRibbonAddIn** projesini ekler.

## <a name="create-the-vsto-add-ins-tab"></a>VSTO eklentileri sekmesini oluşturma
 **Eklentiler** sekmesini oluşturmak için, projenize bir **Şerit (XML)** öğesi ekleyin. Bu izlenecek yolda daha sonra bu sekmeye bazı düğmeler ekleyeceksiniz.

### <a name="to-create-the-add-ins-tab"></a>Eklentiler sekmesini oluşturmak için

1. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (XML)** öğesini seçin.

3. Yeni şeridin adını **MyRibbon** olarak değiştirin ve **Ekle**' ye tıklayın.

     **MyRibbon. cs** veya **MyRibbon. vb** dosyası tasarımcıda açılır. **MyRibbon.xml** ADLı bir XML dosyası projenize de eklenir.

4. **Çözüm Gezgini**, **ThisAddIn. cs** veya **ThisAddIn. vb** öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

5. Aşağıdaki kodu **ThisAddIn** sınıfına ekleyin. bu kod, yöntemini geçersiz kılar `CreateRibbonExtensibilityObject` ve şerit XML sınıfını Office uygulamasına döndürür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. **Çözüm Gezgini**, **MyRibbonAddIn** projesine sağ tıklayın ve ardından **Oluştur**' a tıklayın. Projenin hata olmadan yapılandırıldığını doğrulayın.

## <a name="add-buttons-to-the-add-ins-tab"></a>Eklentiler sekmesine düğme ekleme
 bu VSTO eklentisinin hedefi, kullanıcılara ortak metin ve belirli bir tabloyu etkin belgeye eklemek için bir yol vermektir. Kullanıcı arabirimini sağlamak için, Şerit XML dosyasını değiştirerek **Eklentiler** sekmesine iki düğme ekleyin. Bu izlenecek yolda daha sonra düğmeler için geri çağırma yöntemleri tanımlayacaksınız. Şerit XML dosyası hakkında daha fazla bilgi için bkz. [RIBBON XML](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Eklentiler sekmesine düğme eklemek için

1. **Çözüm Gezgini**' de, **MyRibbon.xml** ' a sağ tıklayın ve sonra **Aç**' a tıklayın.

2. **Tab** öğesinin IÇERIĞINI aşağıdaki XML ile değiştirin. Bu XML, varsayılan denetim grubunun etiketini **içerik** olarak değiştirir ve Etiketler **metin ekle** ve **Tablo Ekle** şeklinde iki yeni düğme ekler.

    ```xml
    <tab idMso="TabAddIns">
        <group id="ContentGroup" label="Content">
            <button id="textButton" label="Insert Text"
                 screentip="Text" onAction="OnTextButton"
                 supertip="Inserts text at the cursor location."/>
            <button id="tableButton" label="Insert Table"
                 screentip="Table" onAction="OnTableButton"
                 supertip="Inserts a table at the cursor location."/>
        </group>
    </tab>
    ```

## <a name="automate-the-document-by-using-the-buttons"></a>Düğmeleri kullanarak belgeyi otomatikleştirin
 `onAction`Kullanıcı bu kullanıcılara tıkladığında eylemler gerçekleştirmek Için **metin ekle** ve **Tablo Ekle** düğmeleri için geri çağırma yöntemleri eklemeniz gerekir. Şerit denetimleri için geri çağırma yöntemleri hakkında daha fazla bilgi için bkz. [RIBBON XML](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Düğmelere geri çağırma yöntemleri eklemek için

1. **Çözüm Gezgini**, **MyRibbon. cs** veya **MyRibbon. vb** öğesine sağ tıklayın ve sonra **Aç**' a tıklayın.

2. Aşağıdaki kodu **MyRibbon. cs** veya **MyRibbon. vb** dosyasının en üstüne ekleyin. Bu kod, ad alanı için bir diğer ad oluşturur <xref:Microsoft.Office.Interop.Word> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb" id="Snippet1":::

3. Sınıfına aşağıdaki yöntemi ekleyin `MyRibbon` . Bu, imlecin geçerli konumundaki etkin belgeye bir dize ekleyen **metin ekle** düğmesi için bir geri çağırma yöntemidir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet2":::

4. Sınıfına aşağıdaki yöntemi ekleyin `MyRibbon` . Bu, imlecin geçerli konumundaki etkin belgeye tablo ekleyen **Tablo Ekle** düğmesi için bir geri çağırma yöntemidir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet3":::

## <a name="testing-the-vsto-add-in"></a>VSTO eklentisini test etme
 Projeyi çalıştırdığınızda, Word açılır ve şeritte **Eklentiler adlı sekme** görünür. Kodu test etmek için **Eklentiler** sekmesindeki **metin ekle** ve **Tablo Ekle** düğmelerine tıklayın.

### <a name="to-test-your-vsto-add-in"></a>VSTO eklentisini test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Şeritte **Eklentiler sekmesinin görünür** olduğunu onaylayın.

3. **Eklentiler** sekmesine tıklayın.

4. **İçerik** grubunun şeritte görünür olduğunu doğrulayın.

5. **İçerik** grubundaki **metin ekle** düğmesine tıklayın.

     İmlecin geçerli konumundaki belgeye bir dize eklenir.

6. **İçerik** grubundaki **Tablo Ekle** düğmesine tıklayın.

     İmlecin geçerli konumundaki belgeye bir tablo eklenir.

## <a name="next-steps"></a>Sonraki adımlar
 Office kullanıcı arabirimini nasıl özelleştireceğinizi öğrenmek için aşağıdaki konulardan daha fazla bilgi edinebilirsiniz:

- farklı bir Office uygulamasının şeridini özelleştirin. Şeriti özelleştirmeyi destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

- şerit tasarımcısını kullanarak bir Office uygulamasının şeridini özelleştirin. Daha fazla bilgi için bkz. [Şerit Tasarımcısı](../vsto/ribbon-designer.md).

- Özel Eylemler bölmesi oluşturun. Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

- Outlook Form bölgelerini kullanarak Microsoft Office Outlook kullanıcı arabirimini özelleştirin. daha fazla bilgi için bkz. [izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
