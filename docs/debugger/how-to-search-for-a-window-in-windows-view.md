---
title: Windows görünümünde pencere ara | Microsoft Docs
description: Visual Studio 'da tanıtıcısını, başlığını, sınıfını veya başlık ve sınıfının bir birleşimini kullanarak Spy + + aracının Windows görünümündeki belirli bir pencereyi arayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0051a17d3a2360776f48cee2bd7f1d2f11a2492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920104"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Nasıl Yapılır: Pencereler Görünümünde Pencere Arama
Windows görünümündeki belirli bir pencereyi, onun tanıtıcısını, başlığını, sınıfını veya başlık ve sınıfının bir birleşimini arama ölçütü olarak kullanarak arayabilirsiniz. Aramanın başlangıç yönünü de belirtebilirsiniz. İletişim kutusundaki alanlar, pencere ağacındaki seçili pencerenin özniteliklerini gösterir.

 İkinci düzeye (masaüstünün alt öğesi olan tüm pencereler) genişletilmiş ağacıyla başlayın, böylece Masaüstü düzeyi pencereleri sınıf adı ve başlığıyla tanımlayabilmenizi sağlayabilirsiniz. Masaüstü düzeyi bir pencere seçtikten sonra, belirli bir alt pencereyi bulmak için bu düzeyi genişletebilirsiniz.

### <a name="to-search-for-a-window-in-windows-view"></a>Windows görünümünde bir pencere aramak için

1. Windows 'u Spy + +, [Windows görünüm](../debugger/windows-view.md) penceresi ve hedef pencere görünür olacak şekilde düzenleyin.

2. **Arama** menüsünde, **pencereyi bul**' u seçin.

    [Pencere arama Iletişim kutusu](../debugger/window-search-dialog-box.md) açılır.

   > [!TIP]
   > Ekran dağınıklığını azaltmak için Spy 'ı **Gizle** seçeneğini belirleyin. Bu seçenek, ana Spy + + penceresini gizleme ve yalnızca **pencere arama** iletişim kutusunu diğer uygulamalarınızın üzerine görünür halde bırakır. **Tamam** ' ı veya **iptal**' i tıklattığınızda veya **Spy + +** seçeneğini belirlediğinizde, Spy + + ana penceresi geri yüklenir.

3. **Bulucu aracını** hedef pencerenin üzerine sürükleyin. Aracı sürüklerken **pencere ara** iletişim kutusu seçili penceredeki ayrıntıları görüntüler.

   - veya

     İstediğiniz pencerenin tanıtıcısını biliyorsanız (örneğin, hata ayıklayıcıdan), bunu **tanıtıcı** kutusuna yazabilirsiniz.

   - veya

     İstediğiniz pencerenin başlığını ve/veya sınıfını biliyorsanız, bunları **başlık** ve **sınıf** metin kutularına yazabilir ve **tanıtıcı** metin kutusunu temizleyebilirsiniz.

4. Aramanın ilk yönü için **yukarı** veya **aşağı** seçeneğini belirleyin.

5. **Tamam**'a tıklayın.

    Eşleşen bir pencere bulunursa, [Windows görünümü](../debugger/windows-view.md) penceresinde vurgulanır.