---
title: MSBuild Dönüşümleri | Microsoft Docs
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
ms.openlocfilehash: 5c4262ed1a7b92170565f7006c9ed06ed884f928
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593778"
---
# <a name="msbuild-transforms"></a>MSBuild Dönüşümleri
Dönüşüm, bir öğe listesinin diğerine bire bir dönüştürmedir. Bir dönüşüm, öğe listelerini dönüştürmek üzere etkinleştirmenin yanı sıra, bir hedefin giriş ve çıkışları arasında doğrudan eşlemeyi belirlemesine olanak sağlar. Bu konu, dönüşümleri ve [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projeleri daha verimli bir şekilde derlemek için nasıl kullandığını açıklar.

## <a name="transform-modifiers"></a>Dönüştürme değiştiricileri
Dönüşümler rastgele değildir, ancak tüm dönüştürme değiştiricilerin%(\<ItemMetaDataName > biçiminde olması gereken özel sözdizimi ile sınırlıdır). Herhangi bir öğe meta verisi, dönüştürme değiştiricisi olarak kullanılabilir. Bu, oluşturulduğunda her öğeye atanan iyi bilinen öğe meta verilerini içerir. İyi bilinen öğe meta verileri listesi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).

Aşağıdaki örnekte, *. resx* dosyalarının bir listesi *. resources* dosyaları listesine dönüştürülür. % (Filename) dönüştürme değiştiricisi her bir *. resources* dosyasının karşılık gelen *. resx* dosyasıyla aynı dosya adına sahip olduğunu belirtir.

```xml
@(RESXFile->'%(filename).resources')
```

Örneğin, @ (RESXFile) öğe listesindeki öğeler *Form1. resx*, *Form2. resx*ve *Form3. resx*ise, dönüştürülmüş listedeki çıktılar *Form1. resources*, *Form2. resources*ve *Form3. resources*olur.

> [!NOTE]
> Dönüştürülmüş öğe listesi için bir özel ayırıcı, bir standart öğe listesi için ayırıcı belirttiğiniz şekilde belirtebilirsiniz. Örneğin, varsayılan noktalı virgül (;) yerine virgül (,) kullanarak dönüştürülmüş bir öğe listesini ayırmak için aşağıdaki XML 'i kullanın: `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Çoklu değiştiriciler kullanın
 Bir Transform ifadesi, herhangi bir sırada birleştirilebilen ve yinelenebilir olabilen birden çok değiştirici içerebilir. Aşağıdaki örnekte, dosyaları içeren dizinin adı değiştirilir, ancak dosyalar özgün adı ve dosya adı uzantısını korurlar.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Örneğin, `RESXFile` öğe listesinde yer alan öğeler *Project1\Form1.resx*, *Project1\Form2.resx*ve *Project1\Form3.Text*ise, dönüştürülmüş listedeki çıktılar *Toolset\Form1.resx*, *Toolset\Form2.resx*ve *Toolset\Form3.Text*olur.

## <a name="dependency-analysis"></a>Bağımlılık Analizi
 Dönüşümler, dönüştürülmüş öğe listesi ve özgün öğe listesi arasında bire bir eşleme garantisi. Bu nedenle, bir hedef girişlerin dönüştürmeleri olan çıktılar oluşturursa, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] giriş ve çıkışların zaman damgalarını çözümleyebilir ve bir hedefi atlayıp atlamaya, derlemenize veya kısmen yeniden oluşturmaya karar verebilirsiniz.

 [Kopyalama görevinde](../msbuild/copy-task.md) aşağıdaki örnekte, `BuiltAssemblies` öğesi listesindeki her dosya, `Outputs` özniteliğinde bir dönüşüm kullanılarak belirtilen görevin hedef klasöründeki bir dosyayla eşlenir. `BuiltAssemblies` öğesi listesindeki bir dosya değişirse, `Copy` görevi yalnızca değiştirilen dosya için çalışır ve diğer tüm dosyalar atlanır. Bağımlılık Analizi ve dönüştürmeleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Artımlı derleme](../msbuild/how-to-build-incrementally.md).

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
 Aşağıdaki örnek, dönüşümler kullanan bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası gösterir. Bu örnekte, *c:\sub0\sub1\alt 2\sub3* dizininde yalnızca bir *. xsd* dosyasının olduğu ve çalışma dizininin *c:\sub0*olduğu varsayılır.

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

### <a name="comments"></a>Açıklamalar
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
