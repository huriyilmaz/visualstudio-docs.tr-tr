---
title: 'Nasıl yapılır: Kısayol menülerine komut ekleme'
description: VSTO eklentisini kullanarak bir Office uygulamasındaki kısayol menüsüne nasıl komut ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a85b45dbe8ffd616b89078795f0cd9ffe11da7fd97e92339dab8ed2162ae2d2f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424221"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Nasıl yapılır: Kısayol menülerine komut ekleme
  bu konu başlığı altında, bir VSTO eklentisi kullanarak bir Office uygulamasındaki kısayol menüsüne nasıl komut ekleyeceğiniz gösterilmektedir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Office içindeki Kısayol menülerine komut eklemek için

1. belge düzeyi veya VSTO eklentisi projesine **şerit XML** öğesi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md). İçinde

2. **Çözüm Gezgini**, **ThisAddIn. cs** veya **ThisAddIn. vb** öğesini seçin.

3. Menü çubuğunda kodu **görüntüle**' yi seçin  >  .

     **ThisAddIn** sınıfı dosyası kod düzenleyicisinde açılır.

4. Aşağıdaki kodu **ThisAddIn** sınıfına ekleyin. bu kod, yöntemini geçersiz kılar `CreateRibbonExtensibilityObject` ve şerit XML sınıfını Office uygulamasına döndürür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet1":::

5. **Çözüm Gezgini**, Şerit XML dosyasını seçin. Varsayılan olarak, Şerit XML dosyası *Ribbon1.xml* olarak adlandırılır.

6. Menü çubuğunda kodu **görüntüle**' yi seçin  >  .

     Şerit XML dosyası kod düzenleyicisinde açılır.

7. Kod Düzenleyicisi 'nde, kısayol menüsünü ve kısayol menüsüne eklemek istediğiniz denetimi tanımlayan XML ekleyin.

     Aşağıdaki örnek bir Word belgesi için kısayol menüsüne bir düğme, menü ve bir galeri denetimi ekler. Bu kısayol menüsünün denetim KIMLIĞI ContextMenuText ' dir. Office 2010 kısayol control ıd 'nin tüm listesi için bkz. [Office 2010 yardım dosyaları: Office akıcı kullanıcı arabirimi denetim tanımlayıcıları](https://www.microsoft.com/download/details.aspx?id=6627).

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />
          <menu id="MySubMenu" label="My Submenu" >
            <button id="MyButton2" label="Button on submenu" />
          </menu>
          <gallery id="galleryOne" label="My Gallery">
            <item id="item1" imageMso="HappyFace" />
            <item id="item2" imageMso="HappyFace" />
            <item id="item3" imageMso="HappyFace" />
            <item id="item4" imageMso="HappyFace" />
          </gallery>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

8. **Çözüm Gezgini**, **MyRibbon. cs** veya **MyRibbon. vb** öğesini seçin.

9. `Ribbon1`İşlemek istediğiniz her denetim için sınıfa bir geri çağırma yöntemi ekleyin.

     Aşağıdaki geri çağırma yöntemi **düğme** düğmesini işler. Bu kod, etkin belgeye curser 'ın geçerli konumundaki bir dize ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [İzlenecek yol: yer işaretleri için kısayol menüleri oluşturma](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Office 2010 ' de bağlam menülerini özelleştirme](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
