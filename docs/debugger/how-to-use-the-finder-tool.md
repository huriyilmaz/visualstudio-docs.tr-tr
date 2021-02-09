---
title: Bulucu aracını kullanma | Microsoft Docs
description: Hata ayıklama oturumu sırasında pencere özelliklerini veya iletilerini göstermek için Spy + + aracının pencereyi bul iletişim kutusunda Bulucu aracını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d48e9b580d25b521721fafa7dc475bdbe3532656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912227"
---
# <a name="how-to-use-the-finder-tool"></a>Nasıl yapılır: Bulucu Aracı Kullanma
Pencere özelliklerini veya iletilerini göstermek için **pencereyi bul** Iletişim kutusunda Bulucu aracını kullanabilirsiniz. Finder aracı devre dışı bırakılan alt pencereleri de bulabilir ve devre dışı bırakılan alt pencereler çakıştığında, hangi pencerenin vurgulanmasını ayırt edebilir.

 ![Spy&#43;&#43; pencere bul Iletişim kutusu](../debugger/media/icon_spy--_find.png "Icon_Spy + + _Find") Pencereyi bul iletişim kutusunda Bulucu aracı

 Yukarıdaki şekilde, aşağıdaki adım 3 ' ten sonra pencere bul iletişim kutusu gösterilmektedir.

### <a name="to-display-window-properties-or-messages"></a>Pencere özelliklerini veya iletilerini görüntüleme

1. Windows 'larınızı hem Spy + + hem de hedef pencere görünür olacak şekilde düzenleyin.

2. **Spy** menüsünde **pencereyi bul**' u seçin.

    [Pencereyi bul Iletişim kutusu](../debugger/find-window-dialog-box.md) açılır.

3. **Bulucu aracını** hedef pencerenin üzerine sürükleyin.

    Aracı sürüklerken, **pencereyi bul** iletişim kutusu seçili penceredeki ayrıntıları görüntüler.

   - veya

     İncelemek istediğiniz pencerenin işleyicisine sahipseniz (örneğin, hata ayıklayıcıdan kopyalanmış), bunu **tanıtıcı** metin kutusuna yazın.

   > [!TIP]
   > Ekran dağınıklığını azaltmak için Spy 'ı **Gizle** seçeneğini belirleyin. Bu seçenek, ana Spy + + penceresini gizleme ve yalnızca diğer uygulamalarınızın üzerine görünen **pencereyi bul** iletişim kutusunu bırakır. **Tamam** ' ı veya **iptal**' i tıklattığınızda veya **Spy + +** seçeneğini belirlediğinizde, Spy + + ana penceresi geri yüklenir.

4. **Göster** altında **Özellikler** veya **iletiler**' i seçin.

5. **Tamam**'a basın.

    **Özellikler**' i seçtiyseniz [Pencere özellikleri iletişim kutusu](../debugger/window-properties-dialog-box.md) açılır. **İletiler**' i seçtiyseniz, bir [iletiler görünümü](../debugger/messages-view.md) penceresi açılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Kullanma](../debugger/using-spy-increment.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)