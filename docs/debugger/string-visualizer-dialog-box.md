---
title: Dize görselleştiricisi (metin, XML, HTML, JSON)
description: Visual Studio 'de hata ayıklarken yerleşik dize görselleştiricisi iletişim kutusuyla dizeleri görüntüleyin.
ms.date: 10/10/2021
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
ms.openlocfilehash: da842df7f92bdcdbd5463755a9c56b5d42613778
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130350813"
---
# <a name="view-text-xml-html-json-strings-in-the-string-visualizer"></a>String Visualizer 'da metin, XML, HTML, JSON dizelerini görüntüleme

Visual Studio hata ayıklaması yaparken, dizeleri yerleşik dize görselleştiricisi ile görüntüleyebilirsiniz. Dize görselleştiricisi bir veri ipucu veya hata ayıklayıcı penceresi için çok uzun olan dizeleri gösterir. Hatalı biçimlendirilmiş dizeleri belirlemenize de yardımcı olabilir.

Yerleşik dize Görselleştiriciler [metin](#text-string-data), [XML](#xml-string-data), [HTML](#html-string-data)ve [JSON](#json-string-data) seçeneklerini içerir. Ayrıca, **oto** veya diğer hata ayıklayıcı pencerelerinin [veri kümesi, DataTable ve DataView](../debugger/dataset-visualizer-dialog-box.md) nesneleri gibi diğer diğer türler için de yerleşik Görselleştiriciler açabilirsiniz.

> [!NOTE]
> Görselleştirici içinde XAML veya WPF Kullanıcı arabirimi öğelerini incelemeniz gerekiyorsa, [hata ayıklama SıRASıNDA xaml özelliklerini](../xaml-tools/inspect-xaml-properties-while-debugging.md) görüntüleyin veya inceleyin ya da [WPF Ağacı Görselleştiricisini Kullanma](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-the-visualizer"></a>Görselleştiriciyi açın

Dize Görselleştiricisini açmak için:
1. Hata ayıklama sırasında duraklatın. 
2. Düz metin, XML, HTML veya JSON dize değerine sahip bir değişkenin üzerine gelin.
3. Büyüteç simgesini ![Visualizersimgesini](../debugger/media/dbg-tips-visualizer-icon.png "Görselleştirici simgesi")seçin.

## <a name="uielement-list"></a>UIElement listesi

**İfade** alanı, üzerine geldiğinizde bulunan değişkeni veya ifadeyi gösterir.

**Değer** alanı dize değerini gösterir. Boş **değer** , seçilen Görselleştirici dizeyi tanıyamayacağı anlamına gelir. Örneğin, **XML GÖRSELLEŞTIRICISI** XML etıketı veya JSON dizesi olmayan bir metin dizesi için boş bir **değer** gösterir. Seçilen Görselleştirici tanıyamayacağı dizeleri görüntülemek için, bunun yerine **metin Görselleştirici** ' ı seçin. **Metin görselleştiricisi** düz metin gösterir.

### <a name="text-string-data"></a>Metin dizesi verileri

**Metin görselleştiricisi** düz metin gösterir. C++ dizesi için özel biçimlendirmeye ihtiyacınız varsa, [Natvis görselleştirmesi](../debugger/create-custom-views-of-native-objects.md)oluşturun.

![Metin dizesi görselleştiricisi](../debugger/media/dbg-string-visualizer-text.png "Metin dizesi görselleştiricisi")

### <a name="json-string-data"></a>JSON dize verileri

Doğru biçimlendirilmiş bir JSON dizesi, JSON Görselleştirici içindeki aşağıdaki çizime benzer şekilde görünür. Hatalı biçimlendirilmiş JSON bir hata simgesi gösterebilir (veya tanınmazsa boş). JSON hatasını belirlemek için, dizeyi kopyalayıp [JSLint](https://www.jslint.com/)gıbı bir JSON oluşturma aracına yapıştırın.

![JSON dize görselleştiricisi](../debugger/media/dbg-tips-string-visualizer-json.png "JSON dize görselleştiricisi")

### <a name="xml-string-data"></a>XML dize verileri

Doğru biçimlendirilmiş bir XML dizesi, XML Görselleştiricisinin aşağıdaki çizimine benzer şekilde görünür. Hatalı biçimlendirilmiş XML, XML etiketleri olmadan veya tanınmazsa boş olarak görüntülenebilir.

![XML dize görselleştiricisi](../debugger/media/dbg-string-visualizers-xml.png "XML dize görselleştiricisi")

### <a name="html-string-data"></a>HTML dize verileri

İyi biçimlendirilmiş bir HTML dizesi, aşağıdaki çizimde gösterildiği gibi, bir tarayıcıda işlenmiş gibi görünür. Hatalı biçimlendirilmiş HTML düz metin olarak görüntülenebilir.

![HTML dize görselleştiricisi](../debugger/media/dbg-string-visualizers-html.png "HTML dize görselleştiricisi")

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Görselleştiriciler oluşturma (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Mac için Visual Studio veri görselleştirmeleri](/visualstudio/mac/data-visualizations)
