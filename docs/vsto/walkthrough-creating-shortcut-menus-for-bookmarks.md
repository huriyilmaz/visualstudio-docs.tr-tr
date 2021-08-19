---
title: 'Adım adım kılavuz: Yer işaretleri için kısayol menüleri oluşturma'
description: Belge düzeyi özelleştirmesinde Yer İşareti denetimleri için kısayol menüleri oluşturma hakkında bilgi Microsoft Word.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b852dce9799ebe7aee87bbecbe2beee7a6cd4616
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115024"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Adım adım kılavuz: Yer işaretleri için kısayol menüleri oluşturma
  Bu kılavuzda, Word için belge düzeyi özelleştirmede <xref:Microsoft.Office.Tools.Word.Bookmark> denetimler için kısayol menüleri oluşturma adımlarını gösterir. Kullanıcı yer işaretinde metne sağ tıkladığında bir kısayol menüsü görüntülenir ve kullanıcıya metni biçimlendirme seçenekleri sunar.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [projesini oluşturun.](#BKMK_CreateProject)

- [Belgeye metin ve yer işaretleri ekleyin.](#BKMK_addtextandbookmarks)

- [Kısayol menüsüne komutlar ekleyin.](#BKMK_AddCmndsShortMenu)

- [Yer işaretinde metni biçimlendirin.](#BKMK_formattextbkmk)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> Projeyi oluşturma
 İlk adım, Visual Studio'da bir Word belgesi Visual Studio.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

- Yer İşareti Kısayol Menüsü adına sahip **bir Word belgesi projesi oluşturun.** Sihirbazda Yeni belge **oluştur'a tıklayın.** Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio yeni Word belgesini tasarımcıda açar ve  Yer İşareti Kısayol Menüm projesini **Çözüm Gezgini.**

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> Belgeye metin ve yer işaretleri ekleme
 Belgenize metin ekleyin ve çakışan iki yer işareti ekleyin.

### <a name="to-add-text-to-your-document"></a>Belgenize metin eklemek için

- Projenizin tasarımcısında görünen belgeye aşağıdaki metni yazın.

     **Bu, bir yer işaretinde metne sağ tıklarsanız kısayol menüsü oluşturma örneğidir.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Belgenize Yer İşareti denetimi eklemek için

1. Araç **Kutusunda,** Word Denetimleri **sekmesinden** bir denetimi <xref:Microsoft.Office.Tools.Word.Bookmark> belgenize sürükleyin.

    Yer **İşareti Denetimi Ekle** iletişim kutusu görüntülenir.

2. "Metne sağ tıklarsanız kısayol menüsü oluşturma" sözcüklerini seçin ve ardından Tamam'a **tıklayın.**

    `bookmark1` , belgeye eklenir.

3. <xref:Microsoft.Office.Tools.Word.Bookmark>"Yer işaretinde metne sağ tıklayın" sözcüklerine başka bir denetim ekleyin.

    `bookmark2` , belgeye eklenir.

   > [!NOTE]
   > "Metne sağ tıklayın" sözcükleri hem hem de `bookmark1` `bookmark2` içindedir.

   Tasarım zamanında bir belgeye yer işareti eklerken <xref:Microsoft.Office.Tools.Word.Bookmark> bir denetim oluşturulur. Yer işaretinin çeşitli olaylarına karşı programlayabilirsiniz. Kullanıcı yer işaretinde metne sağ tıkladığında kısayol menüsünün görüntülendiğinde yer <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> işaretinde kod yazabilirsiniz.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> Kısayol menüsüne komut ekleme
 Belgeye sağ tıklarken görüntülenen kısayol menüsüne düğme ekleyin.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Kısayol menüsüne komut eklemek için

1. Projeye **bir Şerit XML** öğesi ekleyin. Daha fazla bilgi için [bkz. Nasıl Kullanmaya başlayın şeridini özelleştirme.](../vsto/how-to-get-started-customizing-the-ribbon.md)

2. Bu **Çözüm Gezgini** **ThisDocument.cs veya** **ThisDocument.vb öğesini seçin.**

3. Menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.**

     ThisDocument **sınıf** dosyası Kod Düzenleyicisi'nde açılır.

4. ThisDocument sınıfına **aşağıdaki kodu** ekleyin. Bu kod CreateRibbonExtensibilityObject yöntemini geçersiz kılar ve Ribbon XML sınıfını Office döndürür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet1":::

5. Bu **Çözüm Gezgini** Şerit XML dosyasını seçin. Varsayılan olarak, Şerit XML dosyası Ribbon1.xml.

6. Menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.**

     Şerit xml dosyası Kod Düzenleyicisi'nde açılır.

7. Kod Düzenleyicisi'nde Şerit XML dosyasının içeriğini aşağıdaki kodla değiştirin.

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

     Bu kod, belgeye sağ tıklarken görüntülenen kısayol menüsüne iki düğme ekler.

8. **'Çözüm Gezgini** sağ tıklayın ve ardından Kodu `ThisDocument` **Görüntüle'ye tıklayın.**

9. Sınıf düzeyinde aşağıdaki değişkenleri ve yer işareti değişkenlerini bildirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet2":::

10. Bu **Çözüm Gezgini** Şerit kod dosyasını seçin. Şerit kod dosyası varsayılan olarak **Ribbon1.cs** veya **Ribbon1.vb olarak adlandırılmıştır.**

11. Menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.**

     Şerit kod dosyası Kod Düzenleyicisi'nde açılır.

12. Şerit kod dosyasına aşağıdaki yöntemi ekleyin. Bu, belgenin kısayol menüsüne eklediğimiz iki düğme için bir geri çağırma yöntemidir. Bu yöntem, bu düğmelerin kısayol menüsünde görünip görünmey olmadığını belirler. Kalın ve italik düğmeler yalnızca yer işareti içindeki metne sağ tıklarsanız görünür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet5":::

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> Yer işaretinde metni biçimlendirme

### <a name="to-format-the-text-in-the-bookmark"></a>Yer işaretinde metni biçimlendirmek için

1. Şerit kod dosyasında, yer işaretine `ButtonClick` biçimlendirme uygulamak için bir olay işleyicisi ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet6":::

2. **Çözüm Gezgini** **ThisDocument.cs veya** **ThisDocument.vb öğesini seçin.**

3. Menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.**

     ThisDocument **sınıf** dosyası Kod Düzenleyicisi'nde açılır.

4. ThisDocument sınıfına **aşağıdaki kodu** ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet3":::

    > [!NOTE]
    > Yer işaretlerinin çakışması durumlarını işlemek için kod yazmanız gerekir. Yoksa, varsayılan olarak, seçimde tüm yer işaretleri için kod çağrılır.

5. C# içinde, yer işareti denetimleri için olay işleyicilerini olayına eklemeniz <xref:Microsoft.Office.Tools.Word.Document.Startup> gerekir. Olay işleyicileri oluşturma hakkında daha fazla bilgi için [bkz. Nasıl oluşturulur: Office projelerinde olay işleyicileri oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet4":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Bir yer işaretinde metne sağ tıklarsanız ve metnin düzgün bir şekilde biçimlendirilen kısayol menüsünde kalın ve italik menü öğelerinin görüntülenmiş olduğunu doğrulamak için belgenizi test edin.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. İlk yer işaretine sağ tıklayın ve ardından Kalın'a **tıklayın.**

3. içinde tüm metnin kalın olarak `bookmark1` biçimlendirildi olduğunu doğrulayın.

4. Yer işaretlerinin çakıştır olduğu metne sağ tıklayın ve ardından **Italic 'e tıklayın.**

5. içinde tüm metnin italik olduğunu ve yalnızca metnin çakışan kısmının `bookmark2` `bookmark1` `bookmark2` italik olduğunu doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bir sonraki görevlerden bazıları:

- Bir konak denetiminde konak denetimlerinin olaylarına yanıt vermek için Excel. Daha fazla bilgi için [bkz. Adım adım kılavuz: NamedRange denetimi olaylarına karşı program.](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)

- Yer işaretinde biçimlendirmeyi değiştirmek için onay kutusu kullanın. Daha fazla bilgi için [bkz. Adım adım: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme.](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Yer işareti denetimi](../vsto/bookmark-control.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
