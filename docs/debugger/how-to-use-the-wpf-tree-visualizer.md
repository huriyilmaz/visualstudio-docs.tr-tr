---
title: WPF Ağaç Görselleştiricisi'nin | Microsoft Docs
description: WpF Windows Presentation Foundation görsel ağacını keşfetmek ve WPF bağımlılık özelliklerini bir wpf nesnesinde görüntülemek için Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 76a32b8fb6f6c61c27f673b150ec75541ce244f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154024"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Nasıl Yapılır: WPF Ağacı Görselleştiricisini Kullanma
BIR WPF nesnesinin görsel ağacını keşfetmek ve bu ağaçta bulunan nesnelerin WPF bağımlılık özelliklerini görüntülemek için WPF Ağacı görselleştiricisi kullanabilirsiniz. Görsel ağaçları hakkında daha fazla bilgi için [bkz. WPF'de Ağaçlar.](/dotnet/framework/wpf/advanced/trees-in-wpf) Bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [Bağımlılık Özelliklerine Genel Bakış.](/dotnet/framework/wpf/advanced/dependency-properties-overview)

 WPF Ağacı görselleştiricisi'ni açabilirsiniz: sol tarafta **Görsel** Ağaç ve  sağ tarafta Ad **:**_Tür_ bölmesi. Görsel Ağaç bölmesinde herhangi **bir nesneyi** seçin; Ad  **Özellikleri:**_Tür_ bölmesi, bu nesnenin özelliklerini gösterecek şekilde otomatik olarak güncelleştirilir.

 > [!NOTE]
 > WPF nesnelerinin [görsel ağacını incelemek için Canlı](../xaml-tools/inspect-xaml-properties-while-debugging.md) Görsel Ağaç ve Canlı Özellik Gezgini'ni de kullanabilirsiniz. WPF Ağaç Görselleştiricisi eski bir özelliktir ve etkin geliştirme aşamasında değildir.

### <a name="to-open-the-wpf-tree-visualizer"></a>WPF Ağacı görselleştiriciyi açmak için

1. Bir DataTip, **İzleme** **penceresi,** Otomatikler  penceresi veya Yereller penceresinde, WPF nesne adının yanındaki büyüteç simgesinin yanındaki oka tıklayın.

     Görselleştiricilerin listesi görüntülenir.

2. **WPF Ağaç Görselleştiricisi'ne tıklayın.**

### <a name="to-search-the-visual-tree"></a>Görsel ağacında arama yapmak için

- Görsel **Ağaç bölmesinde,** Arama kutusuna aramak istediğiniz **dizeyi** yazın.

  WPF Ağacı görselleştiricisi görsel ağaçta, yazmış olduğunuz dizeyle eşleşen ilk nesneyi hemen bulur. Daha doğru bir eşleşme bulmak için daha fazla karakter yazın.

  - Görsel ağacının içindeki bir sonraki eşleşmeye gitmek için, Sonraki 'ye **tıklayın.**

  - Önceki eşleşmeye geri dönmek için **Prev 'ye tıklayın.**

  - Arama ölçütlerini temizlemek için **Temizle'ye tıklayın.**

### <a name="to-search-the-properties-list"></a>Özellikler listesinde arama yapmak için

- Ad **Özellikleri:** _Tür_ bölmesinde, Filtre kutusuna aramak istediğiniz **dizeyi** yazın.

  WPF Ağacı görselleştiricisi, yazmış olduğunuz dizeyle eşleştirilmiş özellikleri hemen bulur; şimdi, liste yalnızca sizin yazarak dizeyle eşleşen özellikleri görüntüler. Daha doğru bir eşleşme bulmak için daha fazla karakter yazın.

  - Arama ölçütlerini temizlemek için **Temizle'ye tıklayın.**

### <a name="to-close-the-visualizer"></a>Görselleştiriciyi kapatmak için

- İletişim **kutusunun** sağ üst köşesindeki Kapat simgesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [WPF İçinde Ağaçlar](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Bağımlılık Özelliklerine Genel Bakış](/dotnet/framework/wpf/advanced/dependency-properties-overview)
