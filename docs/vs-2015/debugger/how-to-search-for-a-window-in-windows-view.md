---
title: 'Nasıl yapılır: Windows görünümünde pencere arama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9d7a64191db82d5fb0b82518d3db1cf1eb1e0ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858778"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Nasıl Yapılır: Pencereler Görünümünde Pencere Arama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows görünümündeki belirli bir pencereyi, onun tanıtıcısını, başlığını, sınıfını veya başlık ve sınıfının bir birleşimini arama ölçütü olarak kullanarak arayabilirsiniz. Aramanın başlangıç yönünü de belirtebilirsiniz. İletişim kutusundaki alanlar, pencere ağacındaki seçili pencerenin özniteliklerini gösterir.  
  
 İkinci düzeye (masaüstünün alt öğesi olan tüm pencereler) genişletilmiş ağacıyla başlayın, böylece Masaüstü düzeyi pencereleri sınıf adı ve başlığıyla tanımlayabilmenizi sağlayabilirsiniz. Masaüstü düzeyi bir pencere seçtikten sonra, belirli bir alt pencereyi bulmak için bu düzeyi genişletebilirsiniz.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Windows görünümünde bir pencere aramak için  
  
1. Windows 'u Spy + +, [Windows görünüm](../debugger/windows-view.md) penceresi ve hedef pencere görünür olacak şekilde düzenleyin.  
  
2. **Arama** menüsünde, **pencereyi bul**' u seçin.  
  
     [Pencere arama Iletişim kutusu](../debugger/window-search-dialog-box.md) açılır.  
  
    > [!TIP]
    > Ekran dağınıklığını azaltmak için Spy 'ı **Gizle** seçeneğini belirleyin. Bu seçenek, ana Spy + + penceresini gizleme ve yalnızca **pencere arama** iletişim kutusunu diğer uygulamalarınızın üzerine görünür halde bırakır. **Tamam** ' ı veya **iptal**' i tıklattığınızda veya **Spy + +** seçeneğini belirlediğinizde, Spy + + ana penceresi geri yüklenir.  
  
3. **Bulucu aracını** hedef pencerenin üzerine sürükleyin. Aracı sürüklerken **pencere ara** iletişim kutusu seçili penceredeki ayrıntıları görüntüler.  
  
     veya  
  
     İstediğiniz pencerenin tanıtıcısını biliyorsanız (örneğin, hata ayıklayıcıdan), bunu **tanıtıcı** kutusuna yazabilirsiniz.  
  
     veya  
  
     İstediğiniz pencerenin başlığını ve/veya sınıfını biliyorsanız, bunları **başlık** ve **sınıf** metin kutularına yazabilir ve **tanıtıcı** metin kutusunu temizleyebilirsiniz.  
  
4. Aramanın ilk yönü için **yukarı** veya **aşağı** seçeneğini belirleyin.  
  
5. **Tamam**’a tıklayın.  
  
     Eşleşen bir pencere bulunursa, [Windows görünümü](../debugger/windows-view.md) penceresinde vurgulanır.
