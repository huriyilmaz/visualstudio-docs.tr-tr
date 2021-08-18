---
title: Windows View | Microsoft Docs
description: Tanıtıcısını, açıklamalı alt yazısını, sınıfını veya Windows içinde açıklamalı alt yazı ve sınıf birleşimini kullanarak Spy++ aracının Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7321a7ba358f47d02ba78769883765ebec555b4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097135"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Nasıl Yapılır: Pencereler Görünümünde Pencere Arama
Tanıtıcısını, açıklamalı alt yazısını, sınıfını veya açıklamalı alt yazısını ve sınıfını arama ölçütü olarak kullanarak belirli bir pencereyi Windows görünümde arayabilirsiniz. Ayrıca aramanın başlangıç yönünü de belirtsiniz. İletişim kutusundaki alanlar, pencere ağacında seçili pencerenin özniteliklerini gösterir.

 Masaüstü düzeyindeki pencereleri sınıf adlarına ve başlığına göre tanımlayabilirsiniz. Ağacın ikinci düzeye genişleterek (masaüstünü küçük olan tüm pencereler) başlatma. Masaüstü düzeyinde bir pencere seçtikten sonra, belirli bir alt pencereyi bulmak için bu düzeyi genişletebilirsiniz.

### <a name="to-search-for-a-window-in-windows-view"></a>Görünümde bir pencereyi Windows için

1. Pencerelerinizi Spy++, Windows [Görünümü penceresi](../debugger/windows-view.md) ve hedef pencere görünür olacak şekilde düzenleme.

2. Arama **menüsünden** Pencere **Bul'a tıklayın.**

    Pencere [Araması İletişim Kutusu](../debugger/window-search-dialog-box.md) açılır.

   > [!TIP]
   > Ekran dağınıklığı azaltmak için Spy'ı **Gizle seçeneğini** belirleyin. Bu seçenek ana Spy++ penceresini açar ve yalnızca **diğer** uygulamalarınızı görünür durumda bırakır. Spy++ ana penceresi Tamam'a veya **İptal'e** **tıklarsanız** veya Spy++ gizle seçeneğini **temizleyseniz geri** yüklenir.

3. Bulıcı **Aracı'nı** hedef pencerenin üzerine sürükleyin. Siz aracı sürüklerken, **Pencere Araması** iletişim kutusunda seçilen pencereyle ilgili ayrıntılar görüntülenir.

   - veya -

     Pencerenin tanıtıcısını biliyorsanız (örneğin, hata ayıklayıcısından), bunu Tanıtıcı kutusuna **yazabilirsiniz.**

   - veya -

     Pencerenin açıklamalı alt yazısını ve/veya sınıfını biliyorsanız, bunları  **Açıklamalı** Alt Yazı ve Sınıf metin kutularına yazarak Tutamaç metin **kutusunu** temizebilirsiniz.

4. **Aramanın** ilk **yönü** için Yukarı veya Aşağı'ya seçin.

5. **Tamam**'a tıklayın.

    Eşleşen bir pencere bulunursa, Görünüm penceresinde [Windows vurgulanır.](../debugger/windows-view.md)