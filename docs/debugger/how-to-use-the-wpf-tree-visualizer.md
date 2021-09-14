---
title: WPF Ağacı Görselleştiricisini Kullanma | Microsoft Docs
description: wpf nesnesinin görsel ağacını araştırmak ve Visual Studio wpf bağımlılık özelliklerini görüntülemek için Windows Presentation Foundation (WPF) görselleştiricisi kullanın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725414"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Nasıl Yapılır: WPF Ağacı Görselleştiricisini Kullanma
WPF nesnesinin görsel ağacını araştırmak ve söz konusu ağaçta yer alan nesneler için WPF bağımlılık özelliklerini görüntülemek için WPF ağacı görselleştiricisi ' ni kullanabilirsiniz. Görsel ağaçlar hakkında daha fazla bilgi için bkz. [WPF Içindeki ağaçlar](/dotnet/framework/wpf/advanced/trees-in-wpf). Bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 WPF ağaç görselleştiricisi öğesini açtığınızda, iki bölme _görürsünüz: sol_ taraftaki **görsel ağaç** ve sağdaki **Özellikler** **:**_tür_ bölmesi. **Görsel ağaç** bölmesindeki herhangi bir nesneyi seçin ve _ad_**:**_tür_ bölmesi **özellikleri** , bu nesnenin özelliklerini gösterecek şekilde otomatik olarak güncelleştirilir.

 > [!NOTE]
 > Ayrıca, [canlı görsel ağacı ve canlı Özellik Gezgini '](../xaml-tools/inspect-xaml-properties-while-debugging.md) nı kullanarak WPF nesnelerinin görsel ağacını inceleyebilirsiniz. WPF ağacı görselleştiricisi eski bir özelliktir ve etkin geliştirme aşamasındadır.

### <a name="to-open-the-wpf-tree-visualizer"></a>WPF Ağacı Görselleştiricisini açmak için

1. Bir veri Ipucunda, bir WPF nesnesi adının yanındaki bir veri **İpucu, bir** **pencere penceresi veya** **Yereller** penceresinde, büyüteç simgesine bitişik olan oka tıklayın.

     Görselleştiricilerin bir listesi görüntülenir.

2. **WPF ağaç görselleştiricisi** öğesine tıklayın.

### <a name="to-search-the-visual-tree"></a>Görsel ağacı aramak için

- **Görsel ağaç** bölmesinde, **arama** kutusuna arama yapmak istediğiniz dizeyi yazın.

  WPF ağacı görselleştiricisi, görsel ağaçtaki yazdığınız dizeyle eşleşen ilk nesneyi hemen bulur. Daha doğru bir eşleşme bulmak için daha fazla karakter yazın.

  - Görsel ağaç içindeki bir sonraki eşleştirmeye gitmek için **İleri**' ye tıklayın.

  - Önceki eşleştirmeye geri dönmek **için önceki ' ye tıklayın.**

  - Arama ölçütlerini temizlemek için **Temizle**' ye tıklayın.

### <a name="to-search-the-properties-list"></a>Özellikler listesinde arama yapmak için

- _Ad_**:**_tür_ **bölmesine,** **filtre** kutusunda arama yapmak istediğiniz dizeyi yazın.

  WPF ağaç görselleştiricisi, yazdığınız dizeyle eşleşen özellikleri hemen bulur; artık listede, yalnızca yazdığınız dizeyle eşleşen özellikler görüntülenir. Daha doğru bir eşleşme bulmak için daha fazla karakter yazın.

  - Arama ölçütlerini temizlemek için **Temizle**' ye tıklayın.

### <a name="to-close-the-visualizer"></a>Görselleştiriciyi kapatmak için

- İletişim kutusunun sağ üst köşesindeki **Kapat** simgesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [WPF İçinde Ağaçlar](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Bağımlılık Özelliklerine Genel Bakış](/dotnet/framework/wpf/advanced/dependency-properties-overview)
