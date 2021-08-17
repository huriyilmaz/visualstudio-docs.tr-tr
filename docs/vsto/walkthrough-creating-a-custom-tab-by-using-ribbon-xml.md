---
title: 'Adım adım kılavuz: Şerit XML kullanarak özel sekme oluşturma'
description: Şerit (XML) kullanarak Add-Ins ve Microsoft Word otomatikleştirmeyi öğrenin.
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
ms.openlocfilehash: 49d93a5251c0eb45b3ea9246b0850ad57ae9b1bd2590d681ba44dd3f995025d7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121225913"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Adım adım kılavuz: Şerit XML kullanarak özel sekme oluşturma
  Bu kılavuzda Şerit (XML) öğesini kullanarak özel şerit sekmesi **oluşturma adımlarını görebilirsiniz.**

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Eklentiler **sekmesine düğme** ekleme. Eklentiler **sekmesi,** Şerit XML dosyasında tanımlanan varsayılan sekmedir.

- Eklentiler Microsoft Office düğmeleri kullanarak Word'de **otomatikleşme.**

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım, Word VSTO Eklenti projesi oluşturmaktır. Daha sonra bu **belgenin Eklentiler sekmesini** özelleştirebilirsiniz.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. **MyRibbonAddIn** adıyla bir **Word** Eklenti projesi oluşturun.

     Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn.cs** veya **ThisAddIn.vb** kod dosyasını açar ve **MyRibbonAddIn** projesini **Çözüm Gezgini.**

## <a name="create-the-vsto-add-ins-tab"></a>VSTO Eklentileri sekmesini oluşturma
 Eklentiler sekmesini **oluşturmak için** projenize **bir Şerit (XML)** öğesi ekleyin. Bu kılavuzda daha sonra bu sekmeye bazı düğmeler eklenecektir.

### <a name="to-create-the-add-ins-tab"></a>Eklentiler sekmesini oluşturmak için

1. Yeni **Project** Ekle'ye **tıklayın.**

2. Yeni Öğe **Ekle iletişim kutusunda** Şerit **(XML) öğesini seçin.**

3. Yeni Şeridin adını **MyRibbon** olarak değiştirerek Ekle'ye **tıklayın.**

     **MyRibbon.cs** veya **MyRibbon.vb** dosyası tasarımcıda açılır. MyRibbon.xmladlı bir XML **dosyası** da projenize eklenir.

4. Bu **Çözüm Gezgini,** **ThisAddin.cs veya ThisAddin.vb** 'ye sağ **tıklayın** ve ardından Kodu **Görüntüle'ye tıklayın.**

5. **ThisAddin sınıfına aşağıdaki kodu** ekleyin. Bu kod yöntemini geçersiz `CreateRibbonExtensibilityObject` kılar ve Şerit XML sınıfını Office döndürür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. Bu **Çözüm Gezgini,** **MyRibbonAddIn** projesine sağ tıklayın ve ardından Derleme'ye **tıklayın.** Projenin hatasız olarak derlemesini doğrulayın.

## <a name="add-buttons-to-the-add-ins-tab"></a>Eklentiler sekmesine düğme ekleme
 Bu eklentinin VSTO amacı, kullanıcılara etkin belgeye ortak metin ve belirli bir tablo eklemenin bir yolunu vermektir. Kullanıcı arabirimini sağlamak için, Şerit XML **dosyasını değiştirerek** Eklentiler sekmesine iki düğme ekleyin. Bu kılavuzda daha sonra düğmeler için geri çağırma yöntemleri tanımlayacağız. Şerit XML dosyası hakkında daha fazla bilgi için bkz. [Şerit XML](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Eklentiler sekmesine düğme eklemek için

1. Bu **Çözüm Gezgini,** Dosya'ya sağ **MyRibbon.xml** ve ardından Aç'a **tıklayın.**

2. Sekme öğesinin içeriğini **aşağıdaki** XML ile değiştirin. Bu XML, varsayılan denetim grubunun etiketini İçerik olarak **değiştirir** ve Metin Ekle ve Tablo Ekle etiketlerini içeren **iki** yeni **düğme ekler.**

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

## <a name="automate-the-document-by-using-the-buttons"></a>Düğmeleri kullanarak belgeyi otomatikleştirme
 Kullanıcı `onAction` tıkladığında eylemleri gerçekleştirmek için **Metin Ekle ve** Tablo **Ekle** düğmeleri için geri çağırma yöntemleri eklemeniz gerekir. Şerit denetimleri için geri çağırma yöntemleri hakkında daha fazla bilgi için bkz. [Şerit XML](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Düğmeler için geri çağırma yöntemleri eklemek için

1. Bu **Çözüm Gezgini,** **MyRibbon.cs** veya **MyRibbon.vb'ye** sağ tıklayın ve ardından Aç'a **tıklayın.**

2. Aşağıdaki kodu **MyRibbon.cs veya MyRibbon.vb** **dosyasının en üstüne** ekleyin. Bu kod ad alanı için bir diğer ad <xref:Microsoft.Office.Interop.Word> oluşturur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb" id="Snippet1":::

3. Sınıfına aşağıdaki yöntemi `MyRibbon` ekleyin. Bu, etkin belgeye **imlecin geçerli** konumunun bir dize ekleyen Metin Ekle düğmesi için bir geri çağırma yöntemidir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet2":::

4. Sınıfına aşağıdaki yöntemi `MyRibbon` ekleyin. Bu, imleçte geçerli **konumdaki** etkin belgeye tablo ekleyen Tablo Ekle düğmesi için bir geri çağırma yöntemidir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet3":::

## <a name="testing-the-vsto-add-in"></a>VSTO Eklentiyi Test Etme
 Projeyi çalıştırarak Word açılır ve şeritte **Eklentiler adlı** sekme görünür. Kodu **test etmek için** **Eklentiler sekmesindeki** **Metin Ekle ve Tablo** Ekle düğmelerine tıklayın.

### <a name="to-test-your-vsto-add-in"></a>Eklentinizi VSTO için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Şeritte **Eklentiler sekmesinin** görünür olduğunu onaylayın.

3. Eklentiler **sekmesine** tıklayın.

4. Şeritte **İçerik** grubunun görünür olduğunu onaylayın.

5. İçerik **grubunda Metin** Ekle **düğmesine** tıklayın.

     İmlecin geçerli konumunun belgeye bir dize eklenir.

6. İçerik **grubunda Tablo** Ekle **düğmesine** tıklayın.

     İmlecin geçerli konumunun belgeye bir tablo eklenir.

## <a name="next-steps"></a>Sonraki adımlar
 Kullanıcı arabirimini özelleştirme hakkında daha fazla Office şu konulardan öğrenebilirsiniz:

- Farklı bir uygulamanın şeridini Office özelleştirin. Şeridi özelleştirmeyi destekleyen uygulamalar hakkında daha fazla bilgi için bkz. Şerit'e [genel bakış.](../vsto/ribbon-overview.md)

- Şerit Tasarımcısı'Office bir uygulamanın şeridini özelleştirin. Daha fazla bilgi için bkz. [Şerit Tasarımcısı.](../vsto/ribbon-designer.md)

- Özel eylemler bölmesi oluşturun. Daha fazla bilgi için bkz. [Eylemler bölmesine genel bakış.](../vsto/actions-pane-overview.md)

- Form Bölgelerini Microsoft Office Outlook kullanıcı arabirimini Outlook özelleştirin. Daha fazla bilgi için [bkz. Adım adım: Form Outlook tasarlama.](../vsto/walkthrough-designing-an-outlook-form-region.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
