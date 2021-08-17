---
title: Dize görselleştiricisi içindeki dizeleri görüntüleme | Microsoft Docs
description: metin dizelerini, XML, HTML ve JSON görüntülemek için Visual Studio hata ayıklayıcıda dize görselleştiricisi kullanın. Veri kümesi ve DataTable dahil diğer nesne türlerini görüntüleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e2e3fb8a8b2933d49d6bb522a3982819083812c7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035968"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visual Studio dize görselleştiricisi içindeki dizeleri görüntüleme

Visual Studio hata ayıklaması yaparken, dizeleri yerleşik dize görselleştiricisi ile görüntüleyebilirsiniz. Dize görselleştiricisi bir veri ipucu veya hata ayıklayıcı penceresi için çok uzun olan dizeleri gösterir. Hatalı biçimlendirilmiş dizeleri belirlemenize de yardımcı olabilir.

Yerleşik dize görselleştiricisi düz metin, XML, HTML ve JSON seçenekleri içerir. Ayrıca, **oto** veya diğer hata ayıklayıcı pencerelerinin [veri kümesi, DataTable ve DataView](../debugger/dataset-visualizer-dialog-box.md) nesneleri gibi diğer diğer türler için de yerleşik Görselleştiriciler açabilirsiniz.

> [!NOTE]
> Görselleştirici içinde XAML veya WPF Kullanıcı arabirimi öğelerini incelemeniz gerekiyorsa, [hata ayıklama SıRASıNDA xaml özelliklerini](../xaml-tools/inspect-xaml-properties-while-debugging.md) görüntüleyin veya inceleyin ya da [WPF Ağacı Görselleştiricisini Kullanma](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Dize görselleştiricisi açın

Dize görselleştiricisi ' i açmak için hata ayıklama sırasında duraklamalısınız. Düz metin, XML, HTML veya JSON dize değerine sahip bir değişkenin üzerine gelin ve büyüteç simgesini ![Visualizersimgesini](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")seçin.

![Dize görselleştiricisi açın](../debugger/media/dbg-tips-string-visualizers.png "Dize görselleştiricisi aç")

## <a name="view-string-visualizer-data"></a>Dize görselleştiricisi verilerini görüntüle

Dize görselleştiricisi penceresinde, **ifade** alanı üzerinde, üzerine geldiğinizde değişken veya ifade gösterilir ve **değer** alanı dize değerini gösterir.

Boş **değer** , seçilen Görselleştirici dizeyi tanıyamayacağı anlamına gelir. Örneğin, **XML GÖRSELLEŞTIRICISI** XML etıketı veya JSON dizesi olmayan bir metin dizesi için boş bir **değer** gösterir.

Seçilen Görselleştirici tanıyamayacağı dizeleri görüntülemek için **metin Görselleştirici**' ı seçin. **Metin görselleştiricisi** düz metin gösterir.

### <a name="view-json-string-data"></a>JSON dize verilerini görüntüleme

Doğru biçimlendirilmiş bir JSON dizesi, JSON Görselleştirici içindeki aşağıdaki çizime benzer şekilde görünür. Hatalı biçimlendirilmiş JSON bir hata simgesi gösterebilir (veya tanınmazsa boş). JSON hatasını belirlemek için, dizeyi kopyalayıp [JSLint](https://www.jslint.com/)gıbı bir JSON oluşturma aracına yapıştırın.

![JSON dize görselleştiricisi](../debugger/media/dbg-tips-string-visualizer-json.png "JSON dize görselleştiricisi")

### <a name="view-xml-string-data"></a>XML dize verilerini görüntüle

Doğru biçimlendirilmiş bir XML dizesi, XML Görselleştiricisinin aşağıdaki çizimine benzer şekilde görünür. Hatalı biçimlendirilmiş XML, XML etiketleri olmadan veya tanınmazsa boş olarak görüntülenebilir.

![XML dize görselleştiricisi](../debugger/media/dbg-string-visualizers-xml.png "XML dize görselleştiricisi")

### <a name="view-html-string-data"></a>HTML dize verilerini görüntüleme

İyi biçimlendirilmiş bir HTML dizesi, aşağıdaki çizimde gösterildiği gibi, bir tarayıcıda işlenmiş gibi görünür. Hatalı biçimlendirilmiş HTML düz metin olarak görüntülenebilir.

![HTML dize görselleştiricisi](../debugger/media/dbg-string-visualizers-html.png "HTML dize görselleştiricisi")

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Görselleştiriciler oluşturma (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Mac için Visual Studio veri görselleştirmeleri](/visualstudio/mac/data-visualizations)