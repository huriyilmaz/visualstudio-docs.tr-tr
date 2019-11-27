---
title: 'Nasıl yapılır: artımlı olarak derleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d2bf2f8a45618e8b1f7540479a02c1a5f91b9bf
ms.sourcegitcommit: b04c603ce73b993d042ebdf7f3722cf4fe2ef7f4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74316479"
---
# <a name="how-to-build-incrementally"></a>Nasıl yapılır: Artımlı derleme
Büyük bir proje oluşturduğunuzda, daha önce, hala güncel olan bileşenlerin önceden oluşturulmaması önemlidir. Tüm hedefler her seferinde derlenmişse, her derleme tamamlanması uzun sürer. Artımlı derlemeleri etkinleştirmek için (yalnızca önceden oluşturulmamış olan hedefleri veya güncel olmayan hedefleri yeniden oluşturur), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), giriş dosyalarının zaman damgalarına çıkış dosyalarının zaman damgalarına göre karşılaştırabilir ve bir hedefi atlayıp atlaya, derlemeyi veya kısmen yeniden oluşturmayı belirleyebilirsiniz. Ancak, girişler ve çıktılar arasında bire bir eşleme olmalıdır. Bu doğrudan eşlemeyi belirlemek için hedefleri etkinleştirmek üzere dönüşümleri kullanabilirsiniz. Dönüşümler hakkında daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Girişleri ve çıkışları belirtin
Girdiler ve çıktılar proje dosyasında belirtilmişse bir hedef artımlı olarak oluşturulabilir.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Bir hedefin girişlerini ve çıkışlarını belirtmek için

- `Target` öğesinin `Inputs` ve `Outputs` özniteliklerini kullanın. Örneğin:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], giriş dosyalarının zaman damgalarını, çıkış dosyalarının zaman damgalarına göre karşılaştırabilir ve bir hedefi atlayıp atlaya, derlemeyi veya kısmen yeniden derlemeyi belirleyebilirsiniz. Aşağıdaki örnekte, `@(CSFile)` öğesi listesindeki herhangi bir dosya *Hello. exe* dosyasından daha yeniyse, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hedef çalışacaktır; Aksi takdirde, atlanacak:

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Bir hedefte giriş ve çıkış belirtildiğinde her bir çıktı yalnızca bir girişle eşlenir ya da çıktılar ve girişler arasında doğrudan eşleme olmaz. Önceki [CSC görevinde](../msbuild/csc-task.md), örneğin, *Hello. exe*çıkışı tek bir giriş ile eşlenemez; bunların tümüne bağlıdır.

> [!NOTE]
> Girişler ve çıktılar arasında doğrudan eşleme olmayan bir hedef, her zaman bir girişin bir kısmı değiştiyse [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hangi çıktıların yeniden oluşturulması gerektiğini belirleyemediği için her zaman her çıktının yalnızca bir giriş ile eşleşebileceği bir hedeften daha fazla bilgi oluşturur.

Örneğin, [LC görevi](../msbuild/lc-task.md)gibi çıktılar ve girişler arasında doğrudan eşlemeyi tanımlayabilmeniz gereken görevler, bir dizi girişin bir çıkış derlemesini üreten [CSC](../msbuild/csc-task.md) ve [vbc](../msbuild/vbc-task.md)gibi görevlerden farklı olarak Artımlı derlemeler için uygundur.

## <a name="example"></a>Örnek
Aşağıdaki örnek, bir kuramsal yardım sistemi için yardım dosyaları oluşturan bir proje kullanır. Proje, kaynak *. txt* dosyalarını, daha sonra, yardım sistemi tarafından kullanılan son *. help* dosyasını oluşturmak üzere XML meta veri dosyalarıyla birlikte bulunan ara *. Content* dosyalarına dönüştürerek işe yarar. Proje aşağıdaki kuramsal görevleri kullanır:

- `GenerateContentFiles`: *. txt* dosyalarını *. Content* dosyalarına dönüştürür.

- `BuildHelp`: son *. help* dosyasını derlemek için *. Content* dosyalarını ve xml meta veri dosyalarını birleştirir.

Proje, `GenerateContentFiles` görevindeki girişler ve çıktılar arasında bire bir eşleme oluşturmak için dönüşümler kullanır. Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md). Ayrıca, `Output` öğesi, `BuildHelp` görevin girişleri olarak `GenerateContentFiles` görevindeki çıktıları otomatik olarak kullanacak şekilde ayarlanır.

Bu proje dosyası hem `Convert` hem de `Build` hedeflerini içerir. `GenerateContentFiles` ve `BuildHelp` görevleri, her hedefin artımlı olarak oluşturulması için sırasıyla `Convert` ve `Build` hedeflerine yerleştirilir. `Output` öğesini kullanarak, `GenerateContentFiles` görevinin çıktıları `ContentFile` öğe listesine yerleştirilir ve burada `BuildHelp` görevi için giriş olarak kullanılabilirler. `Output` öğesinin bu şekilde kullanılması, her bir görevde ayrı ayrı öğeleri veya öğe listelerini el ile listelemebilmeniz için bir görevden alınan çıktıları otomatik olarak başka bir görevin girişleri olarak sağlar.

> [!NOTE]
> `GenerateContentFiles` hedefi artımlı olarak derleyebilir olsa da, bu hedefin tüm çıkışları her zaman `BuildHelp` hedefinin girdileri olarak gereklidir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], `Output` öğesini kullandığınızda bir hedeften gelen tüm çıktıları otomatik olarak başka bir hedef için giriş olarak sağlar.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
    </ItemGroup>

    <Target Name = "Convert"
        Inputs="@(TXTFile)"
        Outputs="@(TXTFile->'%(Filename).content')">

        <GenerateContentFiles
            Sources = "@(TXTFile)">
            <Output TaskParameter = "OutputContentFiles"
                ItemName = "ContentFiles"/>
        </GenerateContentFiles>
    </Target>

    <Target Name = "Build" DependsOnTargets = "Convert"
        Inputs="@(ContentFiles);@(XMLFiles)"
        Outputs="$(MSBuildProjectName).help">

        <BuildHelp
            ContentFiles = "@(ContentFiles)"
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Hedefler](../msbuild/msbuild-targets.md)
- [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)
- [Dönüşümler](../msbuild/msbuild-transforms.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)
