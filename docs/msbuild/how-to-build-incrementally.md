---
title: 'Nasıl Yapılışı: Artımlı Yapı | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4911bb131f5c5c878b82865b3dee61fd7bedbe1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634168"
---
# <a name="how-to-build-incrementally"></a>Nasıl yapılsın: Artımlı olarak oluşturma

Büyük bir proje oluşturduğunuzda, daha önce oluşturulmuş ve hala güncel olan bileşenlerin yeniden oluşturulmaması önemlidir. Tüm hedefler her seferinde oluşturulursa, her yapının tamamlanması uzun zaman alır. Artımlı yapılar etkinleştirmek için (yalnızca daha önce oluşturulmama veya güncel olmayan hedeflerin yeniden inşa edildiği yapılar), Microsoft Build Engine (MSBuild) giriş dosyalarının zaman damgalarını çıktı dosyalarının zaman damgalarıyla karşılayabilir ve bir hedefi atlayıp atlayacağını, oluşturup oluşturmayacağını veya kısmen yeniden oluşturup oluşturmayacağını belirleyin. Ancak, girişler ve çıktılar arasında bire bir eşleme olmalıdır. Bu doğrudan eşlemi tanımlamak için hedefleri etkinleştirmek için dönüşümleri kullanabilirsiniz. Dönüşümler hakkında daha fazla bilgi için [transformler'e](../msbuild/msbuild-transforms.md)bakın.

## <a name="specify-inputs-and-outputs"></a>Girdi ve çıktıları belirtin

Giriş ler ve çıktılar proje dosyasında belirtilmişse, hedef artımlı olarak oluşturulabilir.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Hedef için giriş ve çıktıları belirtmek için

- Öğenin `Inputs` `Outputs` özniteliklerini `Target` ve özniteliklerini kullanın. Örnek:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild, giriş dosyalarının zaman damgalarını çıktı dosyalarının zaman damgalarıyla karşılayabilir ve bir hedefi atlayıp atlayıp oluşturmayacağını veya kısmen yeniden oluşturup oluşturmayacağını belirleyebilir. Aşağıdaki örnekte, madde listesindeki `@(CSFile)` herhangi bir dosya *hello.exe* dosyasından daha yeniyse, MSBuild hedefi çalıştıracaktır; aksi takdirde atlanır:

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Giriş ler ve çıktılar bir hedefte belirtildiğinde, her çıktı yalnızca bir girişle eşlenebilir veya çıktılar ve girişler arasında doğrudan eşleme olamaz. Önceki [Csc görevinde](../msbuild/csc-task.md), örneğin, çıktı, *hello.exe*, herhangi bir tek giriş eşlenemez - hepsine bağlıdır.

> [!NOTE]
> Girişler ve çıktılar arasında doğrudan eşleme bulunmayan bir hedef, msbuild bazı girdiler değiştiyse hangi çıktıların yeniden oluşturulması gerektiğini belirleyemediğinden, her çıktının yalnızca bir girişle eşlenebileceği bir hedeften her zaman daha sık oluşturulur.

[LC görevi](../msbuild/lc-task.md)gibi çıktılar ve girişler arasında doğrudan eşleme tanımlayabileceğiniz görevler, [csc](../msbuild/csc-task.md) ve [Vbc](../msbuild/vbc-task.md)gibi sayıda girdiden bir çıktı derlemesi üreten görevlerin aksine, artımlı yapılar için en uygundur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, varsayımsal bir Yardım sistemi için Yardım dosyalarını oluşturan bir proje kullanır. Proje, kaynak *.txt* dosyalarını ara *.içerik* dosyalarına dönüştürerek çalışır ve bu dosyalar daha sonra Yardım sistemi tarafından kullanılan son *.yardım* dosyasını oluşturmak için XML meta veri dosyalarıyla birleştirilir. Proje aşağıdaki varsayımsal görevleri kullanır:

- `GenerateContentFiles`: *.txt* dosyalarını *.content* dosyalarına dönüştürür.

- `BuildHelp`: *.content* dosyalarını ve XML meta veri dosyalarını birleştirerek son *.help* dosyasını oluşturur.

Proje, `GenerateContentFiles` görevdeki girişler ve çıktılar arasında bire bir eşleme oluşturmak için dönüşümleri kullanır. Daha fazla bilgi için [Transforms'a](../msbuild/msbuild-transforms.md)bakın. Ayrıca, `Output` öğe, `GenerateContentFiles` `BuildHelp` görevin girdileri olarak görevden çıktıları otomatik olarak kullanacak şekilde ayarlanır.

Bu proje dosyası `Convert` hem `Build` hedefleri hem de hedefleri içerir. Ve `GenerateContentFiles` `BuildHelp` görevler, her `Convert` hedefin artımlı olarak oluşturulabilmesi için sırasıyla hedeflere yerleştirilir. `Build` `Output` Öğe kullanılarak, `GenerateContentFiles` görevin çıktıları `BuildHelp` madde listesine `ContentFile` yerleştirilir ve burada görev için giriş olarak kullanılabilirler. Öğeyi `Output` bu şekilde kullanmak, bir görevin çıktılarını otomatik olarak başka bir görevin girdileri olarak sağlar, böylece her görevde tek tek öğeleri veya madde listelerini el ile listelemeniz gerekmez.

> [!NOTE]
> `GenerateContentFiles` Hedef artımlı olarak oluşturabilse de, bu hedeften elde edilen `BuildHelp` tüm çıktılar her zaman hedef için girdi olarak gereklidir. `Output` MSBuild, öğeyi kullandığınızda, bir hedeften gelen tüm çıktıları başka bir hedef için giriş olarak otomatik olarak sağlar.

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

- [Hedef](../msbuild/msbuild-targets.md)
- [Hedef eleman (MSBuild)](../msbuild/target-element-msbuild.md)
- [Dönüştürmeler](../msbuild/msbuild-transforms.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)
