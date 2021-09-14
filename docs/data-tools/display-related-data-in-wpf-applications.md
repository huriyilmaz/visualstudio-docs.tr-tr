---
title: WPF uygulamalarındaki ilgili verileri görüntüleme
description: WPF uygulamalarında ilgili verileri görüntüleme. Üst-alt ilişkide birbirlerine ilişkin birden çok tablodan veya vardan verilerle çalışma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c5cf789d120249ca283d655f59f5058a7b28f207
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631418"
---
# <a name="display-related-data-in-wpf-applications"></a>WPF uygulamalarındaki ilgili verileri görüntüleme

Bazı uygulamalarda, üst-alt ilişkide birbirlerine ilişkin birden çok tablodan veya vardan gelen verilerle çalışmak istiyor olabilir. Örneğin, bir tablodaki müşterileri görüntüleyen bir kılavuz görüntülemek istiyor `Customers` olabilir. Kullanıcı belirli bir müşteriyi seçerken başka bir kılavuzda ilgili müşterinin siparişlerini ilgili tablodan `Orders` görüntüler.

Veri Kaynakları penceresindeki öğeleri WPF Tasarımcısına sürükleyerek ilgili verileri **görüntülüyor** veriye bağlı denetimler oluşturabilirsiniz.

## <a name="to-create-controls-that-display-related-records"></a>İlgili kayıtların görüntüleniyor olduğu denetimler oluşturmak için

1. Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın** ve Veri **Kaynakları penceresini** açın.

2. Yeni **Veri Kaynağı Ekle'ye** tıklayın ve Veri **Kaynağı Yapılandırma sihirbazını** tamamlayın.

3. WPF tasarımcısını açın ve tasarımcının Veri Kaynakları penceresindeki öğeler için geçerli bir bırakma hedefi olan bir kapsayıcı **içerdiğini emin** olun.

     Geçerli bırakma hedefleri hakkında daha fazla bilgi için [bkz. WPF denetimlerini](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)Visual Studio.

4. Veri **Kaynakları penceresinde,** ilişkideki üst tabloyu veya nesneyi temsil eden düğümü genişletin. Üst tablo veya nesne, bire çok ilişkisinin "bir" tarafındadır.

5. Üst düğümü (veya üst düğümdeki tek tek öğeleri) **Veri** Kaynakları penceresinden tasarımcıdaki geçerli bir bırakma hedefine sürükleyin.

     Visual Studio sürükleyip her öğe için yeni veriye bağlı denetimler oluşturan XAML oluşturur. XAML ayrıca bırakma <xref:System.Windows.Data.CollectionViewSource> hedefinin kaynaklarına üst tablo veya nesne için yeni bir ekler. Bazı veri kaynakları için Visual Studio, verileri üst tabloya veya nesneye yüklemek için kod da oluşturur. Daha fazla bilgi için [bkz. WPF denetimlerini Visual Studio.](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)

6. Veri **Kaynakları penceresinde** ilgili alt tabloyu veya nesneyi bulun. İlgili alt tablolar ve nesneler, üst düğümün veri listesinin en altında genişletilebilir düğümler olarak görünür.

7. Veri Kaynakları penceresinden alt düğümü (veya alt  düğümdeki tek tek öğeleri) tasarımcıdaki geçerli bir bırakma hedefine sürükleyin.

     Visual Studio sürükleyip her bir öğe için yeni veriye bağlı denetimler oluşturan XAML oluşturur. XAML ayrıca bırakma <xref:System.Windows.Data.CollectionViewSource> hedefinin kaynaklarına alt tablo veya nesne için yeni bir ekler. Bu <xref:System.Windows.Data.CollectionViewSource> yeni, tasarımcıya sürüklemiş olduğunu üst tablonun veya nesnenin özelliğine bağlı olur. Bazı veri kaynakları için Visual Studio, verileri alt tabloya veya nesneye yüklemek için kod da oluşturur.

     Aşağıdaki şekilde, Veri **Kaynakları** penceresindeki bir veri kümesinde **Customers** tablosuyla ilgili **Siparişler tablosu gösterilir.**

     ![İlişkiyi gösteren Veri Kaynakları Penceresi](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)
