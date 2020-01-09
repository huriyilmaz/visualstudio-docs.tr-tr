---
title: WPF uygulamalarındaki ilgili verileri görüntüleme
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6ab1301e421f8326cf4cdda97556ecb19e394c29
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586685"
---
# <a name="display-related-data-in-wpf-applications"></a>WPF uygulamalarındaki ilgili verileri görüntüleme

Bazı uygulamalarda, bir üst-alt ilişkisinde birbirleriyle ilgili birden çok tablodan veya varlıktan gelen verilerle çalışmak isteyebilirsiniz. Örneğin, bir `Customers` tablosundan müşterileri görüntüleyen bir kılavuz göstermek isteyebilirsiniz. Kullanıcı belirli bir müşteriyi seçtiğinde, başka bir kılavuz ilgili bir `Orders` tablosundan söz konusu müşteriye ait siparişleri görüntüler.

**Veri kaynakları** penceresinden WPF tasarımcısına öğe sürükleyerek ilgili verileri görüntüleyen veriye göre bağlantılı denetimler oluşturabilirsiniz.

## <a name="to-create-controls-that-display-related-records"></a>İlişkili kayıtları görüntüleyen denetimler oluşturmak için

1. Veri **kaynakları** penceresini açmak için **veri** menüsünde **veri kaynaklarını göster** ' e tıklayın.

2. Tıklayın **yeni veri kaynağı Ekle**ve tamamlayın **veri kaynağı yapılandırması** Sihirbazı.

3. WPF tasarımcısını açın ve tasarımcı 'nın **veri kaynakları** penceresindeki öğeler için geçerli bir bırakma hedefi olan bir kapsayıcı içerdiğinden emin olun.

     Geçerli bırakma hedefleri hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. **Veri kaynakları** penceresinde, ilişkide üst tabloyu veya nesneyi temsil eden düğümü genişletin. Üst tablo veya nesne, bire çok ilişkinin "bir" tarafında yer alır.

5. Üst düğümü (veya üst düğümdeki herhangi bir öğeyi) **veri kaynakları** penceresinden tasarımcıda geçerli bir bırakma hedefi üzerine sürükleyin.

     Visual Studio, sürüklediğiniz her öğe için yeni veri bağlantılı denetimler oluşturan XAML oluşturur. XAML Ayrıca, ana tablo veya nesne için bırakma hedefinin kaynaklarına yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. Visual Studio, bazı veri kaynaklarında verileri üst tabloya veya nesneye yüklemek için de kod üretir. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. **Veri kaynakları** penceresinde ilgili alt tabloyu veya nesneyi bulun. İlişkili alt tablolar ve nesneler, üst düğümün veri listesinin alt kısmında Genişletilebilir düğüm olarak görünür.

7. Alt düğümü (veya alt düğümdeki herhangi bir öğeyi) **veri kaynakları** penceresinden tasarımcıda geçerli bir bırakma hedefi üzerine sürükleyin.

     Visual Studio, sürüklediğiniz öğelerin her biri için yeni veri bağlantılı denetimler oluşturan XAML oluşturur. XAML ayrıca bırakma hedefinin kaynaklarına alt tablo veya nesne için yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. Bu yeni <xref:System.Windows.Data.CollectionViewSource>, yalnızca tasarımcıya sürüklediğiniz üst tablonun veya nesnenin özelliğine bağlanır. Visual Studio, bazı veri kaynaklarında verileri alt tabloya veya nesnesine yüklemek için de kod üretir.

     Aşağıdaki şekilde, **veri kaynakları** penceresinde bir veri kümesindeki **müşteriler** tablosunun ilgili **siparişler** tablosu gösterilmektedir.

     ![İlişkiyi gösteren veri kaynakları penceresi](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)
