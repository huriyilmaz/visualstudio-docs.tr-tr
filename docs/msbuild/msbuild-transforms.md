---
title: MSBuild Dönüşümler | Microsoft Docs
description: MSBuild projeleri daha verimli bir şekilde derlemek için, bir öğe listesini diğerine dönüştürmeleri, bire bir dönüşümleri nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0fd47ef85bd1789a8ff8ccad52709405ed38c4c78e9e8efbc462aa86d02a2ced
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370027"
---
# <a name="msbuild-transforms"></a>MSBuild dönüşümleri

Dönüşüm, bir öğe listesinin diğerine bire bir dönüştürmedir. Bir dönüşüm, öğe listelerini dönüştürmek üzere etkinleştirmenin yanı sıra, bir hedefin giriş ve çıkışları arasında doğrudan eşlemeyi belirlemesine olanak sağlar. bu konu, dönüşümleri ve MSBuild projeleri daha verimli bir şekilde derlemek için nasıl kullandığını açıklar.

## <a name="transform-modifiers"></a>Dönüştürme değiştiricileri

Dönüşümler rastgele değildir, ancak tüm dönüştürme değiştiricilerin%() biçiminde olması gereken özel sözdizimi ile sınırlıdır \<ItemMetaDataName> . Herhangi bir öğe meta verisi, dönüştürme değiştiricisi olarak kullanılabilir. Bu, oluşturulduğunda her öğeye atanan iyi bilinen öğe meta verilerini içerir. İyi bilinen öğe meta verileri listesi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).

Aşağıdaki örnekte, *. resx* dosyalarının bir listesi *. resources* dosyaları listesine dönüştürülür. % (Filename) dönüştürme değiştiricisi her bir *. resources* dosyasının karşılık gelen *. resx* dosyasıyla aynı dosya adına sahip olduğunu belirtir.

```xml
@(RESXFile->'%(filename).resources')
```

Örneğin, @ (RESXFile) öğe listesindeki öğeler *Form1. resx*, *Form2. resx* ve *Form3. resx* ise, dönüştürülmüş listedeki çıktılar *Form1. resources*, *Form2. resources* ve *Form3. resources* olur.

> [!NOTE]
> Dönüştürülmüş öğe listesi için bir özel ayırıcı, bir standart öğe listesi için ayırıcı belirttiğiniz şekilde belirtebilirsiniz. Örneğin, varsayılan noktalı virgül (;) yerine virgül (,) kullanarak dönüştürülmüş bir öğe listesini ayırmak için aşağıdaki XML 'i kullanın: `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Çoklu değiştiriciler kullanın

 Bir Transform ifadesi, herhangi bir sırada birleştirilebilen ve yinelenebilir olabilen birden çok değiştirici içerebilir. Aşağıdaki örnekte, dosyaları içeren dizinin adı değiştirilir, ancak dosyalar özgün adı ve dosya adı uzantısını korurlar.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Örneğin, öğe listesinde yer alan öğeler `RESXFile` *Project1\Form1.resx*, *Project1\Form2.resx* ve *Project1\Form3.Text* ise, dönüştürülmüş listedeki çıktılar *Toolset\Form1.resx*, *Toolset\Form2.resx* ve *Toolset\Form3.Text* olur.

## <a name="dependency-analysis"></a>Bağımlılık Analizi

 Dönüşümler, dönüştürülmüş öğe listesi ve özgün öğe listesi arasında bire bir eşleme garantisi. bu nedenle, bir hedef girişlerin dönüştürmeleri olan çıktılar oluşturursa, MSBuild giriş ve çıkışların zaman damgalarını çözümleyebilir ve bir hedefi atlayıp atlamaya, derlemenize veya kısmen yeniden oluşturmaya karar verebilirsiniz.

 [Kopyalama görevinde](../msbuild/copy-task.md) aşağıdaki örnekte, öğe listesindeki her dosya, `BuiltAssemblies` özniteliğinde bir dönüşüm kullanılarak belirtilen, görevin hedef klasöründeki bir dosyayla eşlenir `Outputs` . `BuiltAssemblies`Öğe listesindeki bir dosya değişirse, `Copy` görev yalnızca değiştirilen dosya için çalışır ve diğer tüm dosyalar atlanır. Bağımlılık Analizi ve dönüştürmeleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Artımlı derleme](../msbuild/how-to-build-incrementally.md).

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

 aşağıdaki örnek, dönüşümler kullanan bir MSBuild proje dosyası gösterir. Bu örnekte, *c:\sub0\sub1\alt 2\sub3* dizininde yalnızca bir *. xsd* dosyasının olduğu ve çalışma dizininin *c:\sub0* olduğu varsayılır.

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

 Bu örnek aşağıdaki çıktıyı üretir:

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
- [Nasıl yapılır: Artımlı derleme](../msbuild/how-to-build-incrementally.md)
