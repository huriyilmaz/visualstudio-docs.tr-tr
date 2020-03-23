---
title: MSBuild Dönüşümleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34394ba35a349a1564f6c3fdd43052be3e1fdf03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633115"
---
# <a name="msbuild-transforms"></a>MSBuild dönüşümleri

Dönüştürme, bir öğe listesinin bire bir diğerine dönüştürülmesidir. Bir projenin madde listelerini dönüştürmesini etkinleştirmeye ek olarak, dönüştürme, bir hedefin girdive çıktıları arasında doğrudan eşlemesini tanımlamasını sağlar. Bu konu dönüşümleri ve MSBuild'in projeleri daha verimli bir şekilde oluşturmak için bunları nasıl kullandığını açıklar.

## <a name="transform-modifiers"></a>Değiştiricileri dönüştürün

Dönüşümler rasgele değildir, ancak tüm dönüştürme değiştiriciler biçiminde olmalıdır özel sözdizimi\<ile sınırlıdır %(ItemMetaDataName>). Herhangi bir madde meta verileri dönüştürme değiştirici olarak kullanılabilir. Bu, oluşturulduğunda her öğeye atanan iyi bilinen öğe meta verilerini içerir. İyi bilinen öğe meta verilerinin listesi için [bkz.](../msbuild/msbuild-well-known-item-metadata.md)

Aşağıdaki örnekte, *.resx* dosyalarının listesi *.resources* dosyaları listesine dönüştürülür. %(filename) dönüştürme değiştirici, her *.resources* dosyasının karşılık gelen *.resx* dosyasıyla aynı dosya adı olduğunu belirtir.

```xml
@(RESXFile->'%(filename).resources')
```

Örneğin, @(RESXFile) öğe listesindeki öğeler *Form1.resx,* *Form2.resx*ve *Form3.resx*ise, dönüştürülen listedeki çıktılar *Form1.resources*, *Form2.resources*ve *Form3.resources*olacaktır.

> [!NOTE]
> Dönüştürülmüş madde listesi için, standart madde listesi için ayırıcı belirttiğiniz şekilde özel ayırıcı belirtebilirsiniz. Örneğin, varsayılan yarı nokta nokta (;) yerine virgül (,) kullanarak dönüştürülmüş madde listesini ayırmak için aşağıdaki XML'yi kullanın:`@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Birden çok değiştirici kullanma

 Dönüştürme ifadesi, herhangi bir sırada birleştirilebilir ve yinelenebilir birden çok değiştiriciler içerebilir. Aşağıdaki örnekte, dosyaları içeren dizin adı değiştirilir, ancak dosyalar özgün adı ve dosya adı uzantısını korur.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Örneğin, `RESXFile` madde listesinde yer alan öğeler *Project1\Form1.resx*, *Project1\Form2.resx*ve *Project1\Form3.text*ise, dönüştürülen listedeki çıktılar *Araç Seti\Form1.resx*, Araç *Seti\Form2.resx*ve *Araç Seti\Form3.text olacaktır.*

## <a name="dependency-analysis"></a>Bağımlılık analizi

 Dönüşümler, dönüştürülen madde listesi ile özgün madde listesi arasında bire bir eşleme garantisi sağlar. Bu nedenle, bir hedef girdidönüşümleri olan çıktılar oluşturursa, MSBuild girdi ve çıktıların zaman damgalarını çözümleyebilir ve bir hedefi atlayıp atlamayacağına, oluşturup oluşturmayacağına veya kısmen yeniden oluşturup oluşturmayacağına karar verebilir.

 Aşağıdaki örnekteki [Kopyala görevinde,](../msbuild/copy-task.md) `BuiltAssemblies` madde listesindeki her dosya, öznitelikteki bir dönüşüm kullanılarak belirtilen görevin hedef klasöründeki bir dosyayla `Outputs` eşlenir. Öğe listesindeki `BuiltAssemblies` bir dosya değişirse, `Copy` görev yalnızca değiştirilen dosya için çalışır ve diğer tüm dosyalar atlanır. Bağımlılık çözümlemesi ve dönüşümlerin nasıl kullanılacağı hakkında daha fazla bilgi için [bkz: Artımlı olarak oluşturun.](../msbuild/how-to-build-incrementally.md)

```xml
<Target Name="CopyOutputs"
    Inputs="@(BuiltAssemblies)"
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">

    <Copy
        SourceFiles="@(BuiltAssemblies)"
        DestinationFolder="$(OutputPath)"/>

</Target>
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

 Aşağıdaki örnekte, dönüşümleri kullanan bir MSBuild proje dosyası gösterilmektedir. Bu örnek, *c:\sub0\sub1\sub2\sub3* dizininde sadece bir *.xsd* dosyası olduğunu ve çalışma dizininin *c:\sub0*olduğunu varsayar.

### <a name="code"></a>Kod

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Schema Include="sub1\**\*.xsd"/>
    </ItemGroup>

    <Target Name="Messages">
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>
        <Message Text="identity: @(Schema->'%(identity)')"/>
        <Message Text="filename: @(Schema->'%(filename)')"/>
        <Message Text="directory: @(Schema->'%(directory)')"/>
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>
        <Message Text="extension: @(Schema->'%(extension)')"/>
    </Target>
</Project>
```

### <a name="comments"></a>Yorumlar

 Bu örnek, aşağıdaki çıktıyı üretir:

```
rootdir: C:\
fullpath: C:\sub0\sub1\sub2\sub3\myfile.xsd
rootdir + directory + filename + extension: C:\sub0\sub1\sub2\sub3\myfile.xsd
identity: sub1\sub2\sub3\myfile.xsd
filename: myfile
directory: sub0\sub1\sub2\sub3\
relativedir: sub1\sub2\sub3\
extension: .xsd
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Nasıl yapılsın: Artımlı olarak oluşturma](../msbuild/how-to-build-incrementally.md)
