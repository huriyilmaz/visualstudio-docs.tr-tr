---
title: 'Nasıl yapılır: artımlı olarak derleme | Microsoft Docs'
description: artımlı olarak oluşturmak için MSBuild kullanmayı öğrenin, böylece daha önce güncel olan daha önce oluşturulmuş bileşenler yeniden oluşturulamaz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b35d9b24a6eee5cae588f6011e96bcb9ad922756bfa233d6f9598ec1a923f5f0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270724"
---
# <a name="how-to-build-incrementally"></a>Nasıl yapılır: Artımlı derleme

Büyük bir proje oluşturduğunuzda, daha önce, hala güncel olan bileşenlerin önceden oluşturulmaması önemlidir. Tüm hedefler her seferinde derlenmişse, her derleme tamamlanması uzun sürer. artımlı derlemeleri etkinleştirmek için (yalnızca önceden oluşturulmamış olan hedefleri veya güncel olmayan hedefleri yeniden oluşturur), Microsoft Build Engine (MSBuild), giriş dosyalarının zaman damgalarına çıkış dosyalarının zaman damgalarına göre karşılaştırabilir ve bir hedefi atlayıp atlaya, derlemeyi veya kısmen yeniden oluşturmayı belirleyebilirsiniz. Ancak, girişler ve çıktılar arasında bire bir eşleme olmalıdır. Bu doğrudan eşlemeyi belirlemek için hedefleri etkinleştirmek üzere dönüşümleri kullanabilirsiniz. Dönüşümler hakkında daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Girişleri ve çıkışları belirtin

Girdiler ve çıktılar proje dosyasında belirtilmişse bir hedef artımlı olarak oluşturulabilir.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Bir hedefin girişlerini ve çıkışlarını belirtmek için

- `Inputs` `Outputs` Öğesinin ve özniteliklerini kullanın `Target` . Örnek:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild, giriş dosyalarının zaman damgalarını, çıkış dosyalarının zaman damgalarına göre karşılaştırabilir ve bir hedefi atlayıp atlaya, derlemeyi veya kısmen yeniden derlemeyi belirleyebilirsiniz. aşağıdaki örnekte, öğe listesindeki herhangi bir dosya `@(CSFile)` *hello.exe* dosyadan daha yeniyse MSBuild hedefi çalıştırır; aksi takdirde atlanacak:

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Bir hedefte giriş ve çıkış belirtildiğinde her bir çıktı yalnızca bir girişle eşlenir ya da çıktılar ve girişler arasında doğrudan eşleme olmaz. Önceki [CSC görevinde](../msbuild/csc-task.md), örneğin çıkış, *hello.exe*, tek bir giriş ile eşlenemez; tümüne bağlıdır.

> [!NOTE]
> girişler ve çıktılar arasında doğrudan eşleme olmayan bir hedef, her zaman bir girişin bir kısmı değiştiyse MSBuild hangi çıktıların yeniden oluşturulması gerektiğini belirleyemediği için her zaman her çıktının yalnızca bir giriş ile eşleşebileceği bir hedeften daha fazla bilgi oluşturur.

Örneğin, [LC görevi](../msbuild/lc-task.md)gibi çıktılar ve girişler arasında doğrudan eşlemeyi tanımlayabilmeniz gereken görevler, bir dizi girişin bir çıkış derlemesini üreten [CSC](../msbuild/csc-task.md) ve [vbc](../msbuild/vbc-task.md)gibi görevlerden farklı olarak Artımlı derlemeler için uygundur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir kuramsal yardım sistemi için yardım dosyaları oluşturan bir proje kullanır. Proje, kaynak *.txt* dosyalarını Ara *. Content* dosyalarına dönüştürerek çalışarak, daha sonra, yardım sistemi tarafından kullanılan son *. help* dosyasını üretmek üzere XML meta veri dosyalarıyla birleştirilir. Proje aşağıdaki kuramsal görevleri kullanır:

- `GenerateContentFiles`: *.txt* dosyalarını *. Content* dosyalarına dönüştürür.

- `BuildHelp`: Son *. help* dosyasını derlemek için *. Content* dosyalarını ve xml meta veri dosyalarını birleştirir.

Proje, görevdeki girişler ve çıktılar arasında bire bir eşleme oluşturmak için dönüşümler kullanır `GenerateContentFiles` . Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md). Ayrıca, `Output` öğesi görevin girişleri olarak görevdeki çıktıları otomatik olarak kullanacak şekilde ayarlanır `GenerateContentFiles` `BuildHelp` .

Bu proje dosyası hem hem de `Convert` `Build` hedeflerini içerir. `GenerateContentFiles`Ve `BuildHelp` görevleri, `Convert` `Build` her hedefin artımlı olarak kullanılabilmesi için sırasıyla ve hedeflerine yerleştirilir. `Output`Öğesini kullanarak, görevin çıkışları, `GenerateContentFiles` `ContentFile` görev için giriş olarak kullanılabilecekleri öğe listesine yerleştirilir `BuildHelp` . `Output`Öğesinin bu şekilde kullanılması, her bir görevde tek tek öğeleri veya öğe listelerini el ile listelemebilmeniz için bir görevden alınan çıktıları otomatik olarak bir görevden verir.

> [!NOTE]
> `GenerateContentFiles`Hedef artımlı olarak derleyebilir olsa da, bu hedefin tüm çıkışları her zaman hedef için giriş olarak gereklidir `BuildHelp` . MSBuild, öğesini kullandığınızda, bir hedeften farklı bir hedefin giriş olarak tüm çıktıları otomatik olarak sağlar `Output` .

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

- [Targets](../msbuild/msbuild-targets.md)
- [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)
- [Dönüştürmeler](../msbuild/msbuild-transforms.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)
