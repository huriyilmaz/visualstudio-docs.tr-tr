---
title: 'Nasıl yap: Artımlı olarak | Microsoft Docs'
description: MSBuild kullanarak artımlı olarak derlemeyi öğrenin. Böylece, daha önce oluşturulmuş ve hala güncel olan bileşenler yeniden oluşturulur.
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
ms.openlocfilehash: 41e4ae9e1c174f95c36c05c50d3d7e88e2bd369f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085084"
---
# <a name="how-to-build-incrementally"></a>Nasıl yap: Artımlı olarak derleme

Büyük bir proje derlemeniz durumunda, önceden oluşturulmuş ve hala güncel olan bileşenlerin yeniden oluşturması önemlidir. Tüm hedefler her zaman uzıyorsa, her derlemenin tamamlanması uzun sürer. Artımlı derlemeleri (yalnızca daha önce oluşturulmuş olan hedeflerin veya eski hedeflerin yeniden oluşturulmuş olduğu derlemeler) etkinleştirmek için Microsoft Build Engine (MSBuild) giriş dosyalarının zaman damgasını çıkış dosyalarının zaman damgasıyla karşılaştırarak bir hedefi atlayıp atlamayacak, derleme veya kısmen yeniden derlemeyi belirleyecek. Ancak, girişler ve çıkışlar arasında bire bir eşleme olması gerekir. Bu doğrudan eşlemeyi tanımlamak üzere hedefleri etkinleştirmek için dönüşümleri kullanabilirsiniz. Dönüşümler hakkında daha fazla bilgi için bkz. [Dönüşümler.](../msbuild/msbuild-transforms.md)

## <a name="specify-inputs-and-outputs"></a>Girişleri ve çıkışları belirtme

Girişler ve çıkışlar proje dosyasında belirtilirse, hedef artımlı olarak inşa edilecektir.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Bir hedefin giriş ve çıkışlarını belirtmek için

- öğesinin `Inputs` `Outputs` ve özniteliklerini `Target` kullanın. Örnek:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild dosyalarının zaman damgasını çıkış dosyalarının zaman damgasıyla karşılaştırarak bir hedefin atlayıp atlanama, derleme veya kısmen yeniden derleme ile ilgili karar ve olabilir. Aşağıdaki örnekte, öğe listesinde yer alan herhangi bir dosyahello.exedosyadan daha yeni MSBuild hedefi çalıştıracak; aksi takdirde `@(CSFile)` atlanır: 

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Girişler ve çıkışlar bir hedefte belirtilirse, her çıkış yalnızca bir girişle eşilebilir veya çıkışlar ile girişler arasında doğrudan eşleme olmaz. Önceki [Csc görevsinde](../msbuild/csc-task.md), örneğin, *hello.exe* çıkışı tek bir girişle eş olamaz; bunların tamamlarına bağlıdır.

> [!NOTE]
> Girişler ve çıkışlar arasında doğrudan eşlemenin mevcut olduğu bir hedef, her zaman her çıkışın tek bir girişle eşlene bir hedeften daha sık oluşturulur çünkü MSBuild bazı girişlerin değişmesi durumunda hangi çıkışların yeniden yapılması gerektirdiğini belirleyelamaz.

Çıkışlar ve girişler arasında doğrudan eşleme belirleyebilirsiniz, örneğin [LC](../msbuild/lc-task.md)görevi , bir dizi girişten bir çıkış derlemesi üreten [Csc](../msbuild/csc-task.md) ve [Vbc](../msbuild/vbc-task.md)gibi görevlerden farklı olarak artımlı derlemeler için en uygundur.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, kuramsal Bir Yardım sistemi için Yardım dosyaları derlemek bir proje kullanılır. Proje, kaynak.txt dosyalarını ara .content dosyalarına dönüştürerek çalışır. Bu dosyalar xml meta veri dosyalarıyla birleştirerek Yardım sistemi tarafından kullanılan *son .help* dosyasını üretir.  Proje aşağıdaki varsayımsal görevleri kullanır:

- `GenerateContentFiles`: Dosya *.txt* *.content dosyalarına* dönüştürür.

- `BuildHelp`: Son *.help dosyasını* oluşturmak için .content dosyalarını ve XML meta veri dosyalarını *birleştirir.*

Proje, görev içinde girişler ve çıkışlar arasında bire bir eşleme oluşturmak için dönüşümleri `GenerateContentFiles` kullanır. Daha fazla bilgi için bkz. [Dönüşümler.](../msbuild/msbuild-transforms.md) Ayrıca, `Output` öğesi, görevin girişleri olarak görev çıkışlarını `GenerateContentFiles` otomatik olarak kullanmak üzere `BuildHelp` ayarlanır.

Bu proje dosyası hem hem `Convert` de `Build` hedeflerini içerir. ve `GenerateContentFiles` `BuildHelp` görevleri sırasıyla `Convert` ve `Build` hedeflerine yerleştirilir, böylece her hedef artımlı olarak bir şekilde inşa edilecektir. öğesi kullanılarak, görevin çıkışları öğe listesine yerleştirilir ve burada görev için giriş `Output` `GenerateContentFiles` olarak `ContentFile` `BuildHelp` kullanılabilirler. öğesini bu şekilde kullanmak, her bir görevdeki tek tek öğeleri veya öğe listelerini el ile listeleye gerek zorunda olmadığınız için bir görevin çıkışlarını otomatik olarak başka bir görevin `Output` girdisi olarak sağlar.

> [!NOTE]
> Hedef `GenerateContentFiles` artımlı olarak yapılsa da, bu hedeften gelen tüm çıkışlar her zaman hedef için giriş olarak `BuildHelp` gereklidir. MSBuild, öğesini kullanırken bir hedeften gelen tüm çıkışları otomatik olarak başka bir hedef için giriş olarak `Output` sağlar.

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
- [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)
- [Dönüştürmeler](../msbuild/msbuild-transforms.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)
