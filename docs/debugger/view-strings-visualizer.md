---
title: Dize görselleştiricisinde dizeleri | Microsoft Docs
description: Metin dizelerini, XML Visual Studio JSON'u görüntülemek için hata ayıklayıcısında dize görselleştiricisini kullanın. DataSet ve DataTable gibi diğer nesne türlerini görüntüebilirsiniz.
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
ms.openlocfilehash: 53201659ee729e142b215a38971a7d9cbd62afebc9d9aa3c72ef315ce58a2658
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418770"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Dize görselleştiricisinde dizeleri Visual Studio

Hata ayıklama sırasında Visual Studio yerleşik dize görselleştiricisi ile dizeleri görüntüabilirsiniz. Dize görselleştiricisi, bir veri ipucu veya hata ayıklayıcısı penceresi için çok uzun olan dizeleri gösterir. Ayrıca hatalı biçimlendirilmiş dizeleri tanımlamanıza da yardımcı olabilir.

Yerleşik dize görselleştiricisi düz metin, XML, HTML ve JSON seçeneklerini içerir. Yerleşik görselleştiricileri [DataSet, DataTable](../debugger/dataset-visualizer-dialog-box.md) ve DataView nesneleri gibi diğer birkaç tür için  Otomatikler veya diğer hata ayıklayıcı pencerelerinden de açabilirsiniz.

> [!NOTE]
> Bir görselleştiricide XAML veya WPF UI öğelerini incelemeniz gerekirse, hata ayıklarken [XAML](../xaml-tools/inspect-xaml-properties-while-debugging.md) özelliklerini inceleme veya WPF ağaç [görselleştiriciyi kullanma.](../debugger/how-to-use-the-wpf-tree-visualizer.md)

## <a name="open-a-string-visualizer"></a>Dize görselleştiriciyi açma

Dize görselleştiricisini açmak için hata ayıklama sırasında duraklatılmış olması gerekir. Düz metin, XML, HTML veya JSON dize değerine sahip bir değişkenin üzerine gelin ve büyüteç simgesini ![VisualizerIcon olarak seçin.](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")

![Dize görselleştiriciyi açma](../debugger/media/dbg-tips-string-visualizers.png "Dize görselleştiriciyi açma")

## <a name="view-string-visualizer-data"></a>Dize görselleştirici verilerini görüntüleme

Dize görselleştirici penceresinde İfade **alanı** üzerine gelinen değişkeni veya ifadeyi, **Değer alanında** ise dize değerini gösterir.

Boş bir **Değer,** seçilen görselleştiricinin dizeyi tanıyamay olduğu anlamına gelir. Örneğin XML **Görselleştiricisi,** XML  etiketi veya JSON dizesine sahip bir metin dizesi için boş bir Değer gösterir.

Seçilen görselleştiricinin tanıyamıyorum dizelerini görüntülemek için Metin **Görselleştirici'yi seçin.** Metin **Görselleştiricisi düz** metin gösterir.

### <a name="view-json-string-data"></a>JSON dize verilerini görüntüleme

JSON görselleştiricisinde aşağıdaki çizime benzer şekilde iyi leştirilmiş bir JSON dizesi görünür. Yanlış biçimlendirilmiş JSON bir hata simgesi (veya tanınmıyorsa boş) biçimlendirilmiş olabilir. JSON hatasını belirlemek için dizeyi kopyalayıp [JSLint](https://www.jslint.com/)gibi bir JSON lint aracına yapıştırın.

![JSON dize görselleştiricisi](../debugger/media/dbg-tips-string-visualizer-json.png "JSON dize görselleştiricisi")

### <a name="view-xml-string-data"></a>XML dize verilerini görüntüleme

XML görselleştiricisinde aşağıdaki çizime benzer şekilde iyi leştirilmiş bir XML dizesi görünür. Yanlış biçimlendirilmiş XML, XML etiketleri olmadan veya tanınmazsa boş biçimlendirilmiş olabilir.

![XML Dize Görselleştiricisi](../debugger/media/dbg-string-visualizers-xml.png "XML Dize Görselleştiricisi")

### <a name="view-html-string-data"></a>HTML dizesi verilerini görüntüleme

Aşağıdaki çizimde gösterildiği gibi, iyi oluşturulmuş bir HTML dizesi bir tarayıcıda işlenmiş gibi görünür. Yanlış biçimlendirilmiş HTML düz metin olarak biçimlendirilmiş olabilir.

![HTML dizesi görselleştiricisi](../debugger/media/dbg-string-visualizers-html.png "HTML Dizesi Görselleştiricisi")

## <a name="see-also"></a>Ayrıca bkz.

- [Özel görselleştiriciler oluşturma (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Mac için Visual Studio'de veri görselleştirmeleri](/visualstudio/mac/data-visualizations)