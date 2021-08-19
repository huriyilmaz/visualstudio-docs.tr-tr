---
title: Dize Görselleştirici iletişim kutusu | Microsoft Docs
description: Hata ayıklama sırasında yerleşik Dize Görselleştirici iletişim kutusuyla dizeleri Visual Studio.
ms.date: 10/10/2018
ms.custom: contperf-fy21q4
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 52d50d7e2bf204de7907f568318b100aa53349d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146686"
---
# <a name="string-visualizer-dialog-box"></a>Dize Görselleştirici iletişim kutusu

Hata ayıklama sırasında Visual Studio yerleşik dize görselleştiricisi ile dizeleri görüntüabilirsiniz. Dize görselleştiricisi, bir veri ipucu veya hata ayıklayıcısı penceresi için çok uzun olan dizeleri gösterir. Ayrıca hatalı biçimlendirilmiş dizeleri tanımlamanıza da yardımcı olabilir.

Yerleşik dize görselleştiricileri [Metin,](#text-string-data) [XML,](#xml-string-data) [HTML](#html-string-data)ve [JSON seçeneklerini](#json-string-data) içerir. Yerleşik görselleştiricileri [DataSet, DataTable](../debugger/dataset-visualizer-dialog-box.md) ve DataView nesneleri gibi diğer birkaç tür için  Otomatikler veya diğer hata ayıklayıcı pencerelerinden de açabilirsiniz.

> [!NOTE]
> Bir görselleştiricide XAML veya WPF UI öğelerini incelemeniz gerekirse, hata ayıklarken [XAML](../xaml-tools/inspect-xaml-properties-while-debugging.md) özelliklerini inceleme veya WPF ağaç [görselleştiriciyi kullanma.](../debugger/how-to-use-the-wpf-tree-visualizer.md)

Dize görselleştiricisini açmak için hata ayıklama sırasında duraklatılmış olması gerekir. Düz metin, XML, HTML veya JSON dize değerine sahip bir değişkenin üzerine gelin ve büyüteç simgesini ![VisualizerIcon olarak seçin.](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")

## <a name="uielement-list"></a>UIElement listesi

**İfade** alanı, üzerine gelinen değişkeni veya ifadeyi gösterir.

**Değer** alanı dize değerini gösterir. Boş bir **Değer,** seçilen görselleştiricinin dizeyi tanıyamay olduğu anlamına gelir. Örneğin XML **Görselleştiricisi,** XML  etiketi veya JSON dizesine sahip bir metin dizesi için boş bir Değer gösterir. Seçilen görselleştiricinin tanıyamıyorum dizelerini görüntülemek için bunun yerine **Metin Görselleştirici'yi** seçin. Metin **Görselleştiricisi düz** metin gösterir.

### <a name="text-string-data"></a>Metin dizesi verileri

Metin **Görselleştiricisi düz** metin gösterir. Bir C++ dizesi için özel biçimlendirmeye ihtiyacınız varsa, bir [Natvis görselleştirmesi oluşturun.](../debugger/create-custom-views-of-native-objects.md)

![Metin dizesi görselleştiricisi](../debugger/media/dbg-string-visualizer-text.png "Metin dizesi görselleştiricisi")

### <a name="json-string-data"></a>JSON dize verileri

JSON görselleştiricisinde aşağıdaki çizime benzer şekilde iyi leştirilmiş bir JSON dizesi görünür. Yanlış biçimlendirilmiş JSON bir hata simgesi (veya tanınmıyorsa boş) biçimlendirilmiş olabilir. JSON hatasını belirlemek için dizeyi kopyalayıp [JSLint](https://www.jslint.com/)gibi bir JSON lint aracına yapıştırın.

![JSON dize görselleştiricisi](../debugger/media/dbg-tips-string-visualizer-json.png "JSON dize görselleştiricisi")

### <a name="xml-string-data"></a>XML dizesi verileri

XML görselleştiricisinde aşağıdaki çizime benzer şekilde iyi leştirilmiş bir XML dizesi görünür. Yanlış biçimlendirilmiş XML, XML etiketleri olmadan veya tanınmazsa boş biçimlendirilmiş olabilir.

![XML Dize Görselleştiricisi](../debugger/media/dbg-string-visualizers-xml.png "XML Dize Görselleştiricisi")

### <a name="html-string-data"></a>HTML dizesi verileri

Aşağıdaki çizimde gösterildiği gibi, iyi oluşturulmuş bir HTML dizesi bir tarayıcıda işlenmiş gibi görünür. Yanlış biçimlendirilmiş HTML düz metin olarak biçimlendirilmiş olabilir.

![HTML dizesi görselleştiricisi](../debugger/media/dbg-string-visualizers-html.png "HTML Dizesi Görselleştiricisi")

## <a name="see-also"></a>Ayrıca bkz.

- [Özel görselleştiriciler oluşturma (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Mac için Visual Studio'daki veri görselleştirmeleri](/visualstudio/mac/data-visualizations)