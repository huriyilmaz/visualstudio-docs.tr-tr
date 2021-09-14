---
title: 'Nasıl kullanılır: Kısayol menülerine Komut Ekleme'
description: VSTO Eklentiyi kullanarak Office uygulamanın kısayol menüsüne komutlar ekleyebilirsiniz.
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
ms.openlocfilehash: 4694ca84475aa569b047e8de818613fe30d04c29
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725591"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Nasıl kullanılır: Kısayol menülerine komut ekleme
  Bu konuda, VSTO Eklenti kullanarak bir Office uygulamanın kısayol menüsüne komutlar ekleme açıklanmıştır.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Kısayol menülerine komut eklemek için Office

1. Belge **düzeyine veya** Eklenti projesine Şerit XML VSTO ekleyin. Daha fazla bilgi için [bkz. Nasıl Kullanmaya başlayın şerit özelleştirme.](../vsto/how-to-get-started-customizing-the-ribbon.md) İçinde

2. **Çözüm Gezgini** **ThisAddin.cs veya** **ThisAddin.vb öğesini seçin.**

3. Menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.**

     **ThisAddin sınıf** dosyası Kod Düzenleyicisi'nde açılır.

4. **ThisAddin sınıfına aşağıdaki kodu** ekleyin. Bu kod yöntemini geçersiz `CreateRibbonExtensibilityObject` kılar ve Ribbon XML sınıfını Office döndürür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet1":::

5. Bu **Çözüm Gezgini** Şerit XML dosyasını seçin. Varsayılan olarak, Şerit XML dosyası *Ribbon1.xml.*

6. Menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.**

     Şerit xml dosyası Kod Düzenleyicisi'nde açılır.

7. Kod Düzenleyicisi'nde kısayol menüsünü ve kısayol menüsüne eklemek istediğiniz denetimi açıklayan XML ekleyin.

     Aşağıdaki örnek, bir sözcük belgesi için kısayol menüsüne düğme, menü ve galeri denetimi ekler. Bu kısayol menüsünün denetim kimliği ContextMenuText'tir. 2010 kısayol Office kimliklerinin tam listesi için [bkz. Office 2010](https://www.microsoft.com/download/details.aspx?id=6627)yardım dosyaları: Office fluent kullanıcı arabirimi denetim tanımlayıcıları.

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

8. Bu **Çözüm Gezgini** **MyRibbon.cs** veya **MyRibbon.vb'yi seçin.**

9. Işlemek istediğiniz her denetim için `Ribbon1` sınıfına bir geri çağırma yöntemi ekleyin.

     Aşağıdaki geri çağırma yöntemi Düğmem **düğmesini** işler. Bu kod, etkin belgeye, büyüleyicinin geçerli yerinde bir dize ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Adım adım kılavuz: Yer işaretleri için Kısayol menüleri oluşturma](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Office 2010'da bağlam menülerini özelleştirme](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
