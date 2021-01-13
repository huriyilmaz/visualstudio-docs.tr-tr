---
title: Iletiler görünümünde Ileti arama | Microsoft Docs
description: Visual Studio 'da hata ayıklama sırasında tanıtıcı, tür veya ileti KIMLIĞINI arama ölçütü olarak kullanarak, Spy + + aracının Iletiler görünümündeki belirli bir iletiyi arayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c351eacc6fc3793065bcd11eb5456eebdc1864f3
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148591"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Nasıl Yapılır: İletiler Görünümünde İleti Arama
İleti görünümünde belirli bir iletiyi, tanıtıcı, tür veya ileti KIMLIĞINI arama ölçütü olarak kullanarak arayabilirsiniz. Bunlardan herhangi biri veya bir bileşim, geçerli arama ölçütleri olacaktır. Aramanın başlangıç yönü de belirtilebilir. İletişim kutusundaki alanlar, seçili durumdaki iletinin öznitelikleriyle önceden yüklenir.

### <a name="to-search-for-a-message-in-messages-view"></a>Iletiler görünümünde ileti aramak için

1. Windows 'larınızı Spy + + etkin [Iletiler görünümü](../debugger/messages-view.md) penceresi görünür olacak şekilde düzenleyin.

2. **Arama** menüsünde **ileti bul**' u seçin.

    [Ileti arama Iletişim kutusu](../debugger/message-search-dialog-box.md) açılır.

3. **Bulucu aracını** istenen pencerenin üzerine sürükleyin. Aracı sürüklerken **Ileti arama** iletişim kutusu seçili penceredeki ayrıntıları görüntüler.

   - veya

     İletilerini incelemek istediğiniz pencerenin işleyicisine sahipseniz, bunu **tanıtıcı** metin kutusuna yazın.

   - veya

     İstediğiniz ileti türünü ve/veya ileti KIMLIĞINI biliyorsanız, **tür** ve **ileti** açılan menülerinden bunları seçin ve **tanıtıcı** metin kutusunu temizleyin.

4. Değerlerini belirtmek istemediğiniz tüm alanları temizleyin.

   > [!TIP]
   > Ekran dağınıklığını azaltmak için Spy 'ı **Gizle** seçeneğini belirleyin. Bu seçenek, ana Spy + + penceresini gizleme ve yalnızca diğer uygulamalarınızın üzerine görünen **pencereyi bul** iletişim kutusunu bırakır. **Tamam** ' ı veya **iptal**' i tıklattığınızda veya **Spy + +** seçeneğini belirlediğinizde, Spy + + ana penceresi geri yüklenir.

5. Aramanın ilk yönü için **yukarı** veya **aşağı** seçeneğini belirleyin.

6. **Tamam**'a tıklayın.

   Eşleşen bir ileti bulunursa, Iletiler görünümü penceresinde vurgulanır. Bkz. [Iletiler görünümü](../debugger/messages-view.md).