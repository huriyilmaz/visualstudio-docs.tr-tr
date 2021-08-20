---
title: Bul penceresinden Iletiler görünümünü aç | Microsoft Docs
description: Bir hedef pencere seçmek için Spy + + ' daki pencere bul iletişim kutusunu kullanın ve ardından bu pencere için bir Iletiler görünümü açın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 852769189cf7294696f562d4d7ed6e89ce962cbd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128240"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Nasıl yapılır: Bul Penceresinden İletiler Görünümünü Açma
Bir hedef pencere seçmek için **pencere bul** iletişim kutusunu kullanmayı ve ardından söz konusu pencerenin iletiler görünümünü açmayı kullanışlı bulabilirsiniz.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Pencereyi bul iletişim kutusunu kullanarak bir Iletiler görünümü penceresi açmak için

1. Windows 'larınızı hem Spy + + hem de hedef pencere görünür olacak şekilde düzenleyin.

2. **Spy** menüsünde **pencereyi bul**' u seçin.

    [Pencereyi bul Iletişim kutusu](../debugger/find-window-dialog-box.md) açılır.

3. **Windows** sekmesinden **bulucu aracını** hedef pencerenin üzerine sürükleyin. Aracı sürüklerken, **pencereyi bul** iletişim kutusu seçili penceredeki ayrıntıları görüntüler.

   - veya

     İncelemek istediğiniz pencerenin işleyicisine sahipseniz (örneğin, hata ayıklayıcıdan kopyalanmış), bunu **tanıtıcı** metin kutusuna yazabilirsiniz.

4. **Göster** altında **iletiler**' i seçin.

5. **Tamam**'a basın.

    Boş bir [Iletiler görünümü](../debugger/messages-view.md) penceresi açılır ve Spy + + araç çubuğuna bir **iletiler** menüsü eklenir.

6. **İletiler** menüsünde **günlüğe kaydetme seçenekleri**' ni seçin.

    [Ileti seçenekleri Iletişim kutusu](../debugger/message-options-dialog-box.md) açılır.

7. Göstermek istediğiniz iletilerin seçeneklerini belirleyin.

8. İletileri kaydetmeye başlamak için **Tamam** 'a basın.

    Seçilen seçeneklere bağlı olarak, iletiler etkin Iletiler görünümü penceresinde akışa başlar.

9. Yeterli iletiniz olduğunda **iletiler** menüsünden **günlüğü durdur** ' u seçin.
