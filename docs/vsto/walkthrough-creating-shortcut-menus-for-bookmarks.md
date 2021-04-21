---
title: 'İzlenecek yol: yer işaretleri için kısayol menüleri oluşturma'
description: Microsoft Word için belge düzeyi özelleştirmesindeki yer Işareti denetimleri için kısayol menüleri oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 48381d452b0c67a34581092a47896aba60e7125c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826310"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>İzlenecek yol: yer işaretleri için kısayol menüleri oluşturma
  Bu izlenecek yol <xref:Microsoft.Office.Tools.Word.Bookmark> , Word için belge düzeyi özelleştirmesindeki denetimler için kısayol menülerinin nasıl oluşturulacağını gösterir. Bir Kullanıcı bir yer işareti içindeki metne sağ tıkladığında, bir kısayol menüsü görünür ve metin biçimlendirme için Kullanıcı seçeneklerini verir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [Projeyi oluşturun](#BKMK_CreateProject).

- [Belgeye metin ve yer Işaretleri ekleyin](#BKMK_addtextandbookmarks).

- [Kısayol menüsüne komut ekleyin](#BKMK_AddCmndsShortMenu).

- [Yer işaretindeki metni biçimlendirin](#BKMK_formattextbkmk).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> Projeyi oluşturma
 İlk adım, Visual Studio 'da bir Word belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

- **My Bookmark kısayol Menu** adlı bir Word belgesi projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Word belgesini açar ve **Çözüm Gezgini** Için **yer işareti kısayol menü** projesini ekler.

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> Belgeye metin ve yer işaretleri ekleme
 Belgenize bazı metinler ekleyin ve ardından iki çakışan yer işareti ekleyin.

### <a name="to-add-text-to-your-document"></a>Belgenize metin eklemek için

- Projenizin tasarımcısında görüntülenen belgede aşağıdaki metni yazın.

     **Bu, bir yer işareti içindeki metne sağ tıkladığınızda bir kısayol menüsü oluşturma örneğidir.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Belgenize bir yer Işareti denetimi eklemek için

1. **Araç kutusu**' nda, **Word denetimleri** sekmesinden belgenize bir denetim sürükleyin <xref:Microsoft.Office.Tools.Word.Bookmark> .

    **Yer Işareti denetimi Ekle** iletişim kutusu görünür.

2. "Metne sağ tıklayıp kısayol menüsü oluşturma" sözcüklerini seçin ve ardından **Tamam**' a tıklayın.

    `bookmark1` belgeye eklenir.

3. Sözcüklere başka bir <xref:Microsoft.Office.Tools.Word.Bookmark> denetim ekleme "bir yer işareti içindeki metne sağ tıklayın".

    `bookmark2` belgeye eklenir.

   > [!NOTE]
   > "Metne sağ tıklama" sözcükleri hem hem de içinde bulunur `bookmark1` `bookmark2` .

   Tasarım zamanında belgeye bir yer işareti eklediğinizde bir <xref:Microsoft.Office.Tools.Word.Bookmark> denetim oluşturulur. Yer işaretinin birkaç olayına karşı programlama yapabilirsiniz. Yer <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> işaretinin olayında, Kullanıcı, yer işaretindeki metne sağ tıkladığında bir kısayol menüsü göründüğünde kod yazabilirsiniz.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> Kısayol menüsüne komut ekleme
 Belgeye sağ tıkladığınızda görüntülenen kısayol menüsüne düğmeler ekleyin.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Bir kısayol menüsüne komut eklemek için

1. Projeye bir **ŞERIT XML** öğesi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. **Çözüm Gezgini** içinde **ThisDocument. cs** veya **ThisDocument. vb** öğesini seçin.

3. Menü çubuğunda kodu **görüntüle**' yi seçin  >  .

     **ThisDocument** sınıfı dosyası kod düzenleyicisinde açılır.

4. Aşağıdaki kodu **ThisDocument** sınıfına ekleyin. Bu kod CreateRibbonExtensibilityObject yöntemini geçersiz kılar ve Şerit XML sınıfını Office uygulamasına döndürür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet1":::

5. **Çözüm Gezgini**, Şerit XML dosyasını seçin. Varsayılan olarak, Şerit XML dosyası Ribbon1.xml olarak adlandırılır.

6. Menü çubuğunda kodu **görüntüle**' yi seçin  >  .

     Şerit XML dosyası kod düzenleyicisinde açılır.

7. Kod Düzenleyicisi 'nde, Şerit XML dosyasının içeriğini aşağıdaki kodla değiştirin.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     Bu kod, belgeye sağ tıkladığınızda görüntülenen kısayol menüsüne iki düğme ekler.

8. **Çözüm Gezgini**' de sağ tıklayın `ThisDocument` ve **kodu görüntüle**' ye tıklayın.

9. Aşağıdaki değişkenleri ve sınıf düzeyinde bir yer işareti değişkeni bildirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet2":::

10. **Çözüm Gezgini**, Şerit kod dosyasını seçin. Varsayılan olarak, Şerit kod dosyası **Ribbon1. cs** veya **Ribbon1. vb** olarak adlandırılır.

11. Menü çubuğunda kodu **görüntüle**' yi seçin  >  .

     Şerit kod dosyası kod düzenleyicisinde açılır.

12. Şerit kod dosyasında aşağıdaki yöntemi ekleyin. Bu, belgenin kısayol menüsüne eklediğiniz iki düğme için bir geri çağırma yöntemidir. Bu yöntem, bu düğmelerin kısayol menüsünde görünüp görünmeyeceğini belirler. Kalın ve italik düğmeler yalnızca yer işareti içindeki metni sağ tıklattığınızda görünür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet5":::

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> Yer işaretinde metni biçimlendirme

### <a name="to-format-the-text-in-the-bookmark"></a>Yer işaretindeki metni biçimlendirmek için

1. Şerit kod dosyasında, `ButtonClick` yer işaretine biçimlendirme uygulamak için bir olay işleyicisi ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet6":::

2. **Çözüm Gezgini**, **ThisDocument. cs** veya **ThisDocument. vb** öğesini seçin.

3. Menü çubuğunda kodu **görüntüle**' yi seçin  >  .

     **ThisDocument** sınıfı dosyası kod düzenleyicisinde açılır.

4. Aşağıdaki kodu **ThisDocument** sınıfına ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet3":::

    > [!NOTE]
    > Yer işaretlerinin çakıştığı durumu işlemek için kod yazmanız gerekir. Aksi takdirde, varsayılan olarak, seçimdeki tüm yer işaretleri için kod çağırılır.

5. C# dilinde, olaya yer işareti denetimleri için olay işleyicileri eklemeniz gerekir <xref:Microsoft.Office.Tools.Word.Document.Startup> . Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet4":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Kalın ve italik menü öğelerinin kısayol menüsünde göründüğünü doğrulamak için belgenizi test edin ve bir yer işaretinde metin ' i sağ tıklayıp metnin düzgün biçimlendirildiğinden emin olun.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. İlk yer işaretine sağ tıklayın ve ardından **kalın**' ı tıklatın.

3. İçindeki tüm metnin `bookmark1` kalın olarak biçimlendirildiğini doğrulayın.

4. Yer işaretlerinin çakıştığı metni sağ tıklatın ve ardından **italik**' i tıklatın.

5. İçindeki tüm metnin `bookmark2` italik olduğunu ve yalnızca çakışan metnin bir kısmını italik olduğunu doğrulayın `bookmark1` `bookmark2` .

## <a name="next-steps"></a>Sonraki adımlar
 Daha sonra gelebilecek bazı görevler şunlardır:

- Excel 'de konak denetimlerinin olaylarına yanıt vermek için kod yazın. Daha fazla bilgi için bkz. [Walkthrough: bir NamedRange denetimindeki olaylara karşı](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)programlama.

- Yer işareti içindeki biçimlendirmeyi değiştirmek için bir onay kutusu kullanın. Daha fazla bilgi için bkz. [Izlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Yer işareti denetimi](../vsto/bookmark-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
