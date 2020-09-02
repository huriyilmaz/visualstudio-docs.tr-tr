---
title: MSBuild Dönüşümleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f9a6f7985e3ebb3e77dcc605157f75e00a0842b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793892"
---
# <a name="msbuild-transforms"></a>MSBuild Dönüşümleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dönüşüm, bir öğe listesinin diğerine bire bir dönüştürmedir. Bir dönüşüm, öğe listelerini dönüştürmek üzere etkinleştirmenin yanı sıra, bir hedefin giriş ve çıkışları arasında doğrudan eşlemeyi belirlemesine olanak sağlar. Bu konu, dönüşümleri açıklar ve [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projeleri daha verimli bir şekilde derlemek için bunları nasıl kullanır.  
  
## <a name="transform-modifiers"></a>Dönüştürme değiştiricileri  
 Dönüşümler rastgele değildir, ancak tüm dönüştürme değiştiricilerin%(*ItemMetaDataName*) biçiminde olması gereken özel sözdizimi ile sınırlıdır. Herhangi bir öğe meta verisi, dönüştürme değiştiricisi olarak kullanılabilir. Bu, oluşturulduğunda her öğeye atanan iyi bilinen öğe meta verilerini içerir. İyi bilinen öğe meta verileri listesi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Aşağıdaki örnekte,. resx dosyalarının bir listesi. resources dosyaları listesine dönüştürülür. % (Filename) dönüştürme değiştiricisi her bir. resources dosyasının karşılık gelen. resx dosyasıyla aynı dosya adına sahip olduğunu belirtir.  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
> Dönüştürülmüş öğe listesi için bir özel ayırıcı, bir standart öğe listesi için ayırıcı belirttiğiniz şekilde belirtebilirsiniz. Örneğin, varsayılan noktalı virgül (;) yerine virgül (,) kullanarak dönüştürülmüş bir öğe listesini ayırmak için aşağıdaki XML 'yi kullanın.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 Örneğin, @ (RESXFile) öğe listesindeki öğeler `Form1.resx` , ve ise, `Form2.resx` `Form3.resx` dönüştürülmüş listedeki çıktılar `Form1.resources` , `Form2.resources` ve olur `Form3.resources` .  
  
## <a name="using-multiple-modifiers"></a>Çoklu değiştiriciler kullanma  
 Bir Transform ifadesi, herhangi bir sırada birleştirilebilen ve yinelenebilir olabilen birden çok değiştirici içerebilir. Aşağıdaki örnekte, dosyaları içeren dizinin adı değiştirilir, ancak dosyalar özgün adı ve dosya adı uzantısını korurlar.  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Örneğin, `RESXFile` öğe listesinde bulunan öğeler `Project1\Form1.resx` , ve ise, `Project1\Form2.resx` `Project1\Form3.text` dönüştürülmüş listedeki çıktılar `Toolset\Form1.resx` , ve olur `Toolset\Form2.resx` `Toolset\Form3.text` .  
  
## <a name="dependency-analysis"></a>Bağımlılık Analizi  
 Dönüşümler, dönüştürülmüş öğe listesi ve özgün öğe listesi arasında bire bir eşleme garantisi. Bu nedenle, bir hedef, girişlerin dönüştürmeleri olan çıktılar oluşturursa, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] girişlerin ve çıktıların zaman damgalarını çözümleyebilir ve bir hedefi atlamaya, oluşturmaya veya kısmen yeniden oluşturmaya karar verebilirsiniz.  
  
 [Kopyalama görevinde](../msbuild/copy-task.md) aşağıdaki örnekte, öğe listesindeki her dosya, `BuiltAssemblies` özniteliğinde bir dönüşüm kullanılarak belirtilen, görevin hedef klasöründeki bir dosyayla eşlenir `Outputs` . `BuiltAssemblies`Öğe listesindeki bir dosya değişirse, `Copy` görev yalnızca değiştirilen dosya için çalıştırılır ve diğer tüm dosyalar atlanır. Bağımlılık Analizi ve dönüştürmeleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Artımlı derleme](../msbuild/how-to-build-incrementally.md).  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dönüşümler kullanan bir proje dosyası gösterir. Bu örnekte, c:\sub0\sub1\alt 2\sub3 dizininde yalnızca bir. xsd dosyasının olduğunu ve çalışma dizininin c:\sub0olduğunu varsaymaktadır.  
  
### <a name="code"></a>Kod  
  
```  
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
 Bu örnek aşağıdaki çıktıyı üretir.  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Nasıl Yapılır: Artımlı Olarak Derleme](../msbuild/how-to-build-incrementally.md)
