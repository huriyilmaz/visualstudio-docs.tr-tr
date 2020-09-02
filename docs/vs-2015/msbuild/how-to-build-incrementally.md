---
title: 'Nasıl yapılır: artımlı olarak derleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4b2e6dd825cfcf67ffffd9ace27017c8d01aa33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835880"
---
# <a name="how-to-build-incrementally"></a>Nasıl Yapılır: Artımlı Olarak Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Büyük bir proje oluşturduğunuzda, daha önce, hala güncel olan bileşenlerin önceden oluşturulmaması önemlidir. Tüm hedefler her seferinde derlenmişse, her derleme tamamlanması uzun sürer. Artımlı derlemeleri etkinleştirmek için (yalnızca öncesinde veya güncel olmayan hedeflerin oluşturulduğu derlemeler yeniden oluşturulur), [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ) giriş dosyalarının zaman damgalarını, çıkış dosyalarının zaman damgalarına göre karşılaştırabilir ve bir hedefi atlayıp atlaya, derlemeyi veya kısmen yeniden oluşturmayı belirleyebilirsiniz. Ancak, girişler ve çıktılar arasında bire bir eşleme olmalıdır. Bu doğrudan eşlemeyi belirlemek için hedefleri etkinleştirmek üzere dönüşümleri kullanabilirsiniz. Dönüşümler hakkında daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).  
  
## <a name="specifying-inputs-and-outputs"></a>Girişleri ve çıkışları belirtme  
 Girdiler ve çıktılar proje dosyasında belirtilmişse bir hedef artımlı olarak oluşturulabilir.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Bir hedefin girişlerini ve çıkışlarını belirtmek için  
  
- `Inputs` `Outputs` Öğesinin ve özniteliklerini kullanın `Target` . Örneğin:  
  
  ```  
  <Target Name="Build"  
      Inputs="@(CSFile)"  
      Outputs="hello.exe">  
  ```  
  
  [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , giriş dosyalarının zaman damgalarını çıkış dosyalarının zaman damgalarına göre karşılaştırabilir ve bir hedefi atlayıp atlaya, derlemeyi veya kısmen yeniden oluşturmayı belirleyebilirsiniz. Aşağıdaki örnekte, öğe listesindeki herhangi bir dosya `@(CSFile)` hello.exe dosyasından daha yeniyse, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] hedefi çalıştıracaktır; Aksi takdirde atlanacak:  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Bir hedefte giriş ve çıkış belirtildiğinde her bir çıktı yalnızca bir girişle eşlenir ya da çıktılar ve girişler arasında doğrudan eşleme olmaz. Önceki [CSC görevinde](../msbuild/csc-task.md), örneğin çıkış, hello.exe, tek bir giriş ile eşlenemez; bunların tümüne bağlıdır.  
  
> [!NOTE]
> Girişler ve çıktılar arasında doğrudan eşleme olmayan bir hedef, her zaman bir girişin bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kısmı değiştiyse hangi çıktıların yeniden oluşturulması gerektiğini belirleyemediği için her zaman her çıktının yalnızca bir giriş ile eşleşebileceği bir hedeften daha fazla bilgi oluşturur.  
  
 Örneğin, [LC görevi](../msbuild/lc-task.md)gibi çıktılar ve girişler arasında doğrudan eşlemeyi tanımlayabilmeniz gereken görevler, `Csc` bir dizi girişin bir çıkış derlemesini üreten ve [vbc](../msbuild/vbc-task.md)gibi görevlerden farklı olarak Artımlı derlemeler için uygundur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir kuramsal yardım sistemi için yardım dosyaları oluşturan bir proje kullanır. Proje, kaynak. txt dosyalarını, daha sonra, yardım sistemi tarafından kullanılan son. help dosyasını oluşturmak üzere XML meta veri dosyalarıyla birlikte bulunan ara. content dosyalarına dönüştürerek işe yarar. Proje aşağıdaki kuramsal görevleri kullanır:  
  
- `GenerateContentFiles`:. Txt dosyalarını. content dosyalarına dönüştürür.  
  
- `BuildHelp`: Son. help dosyasını derlemek için. Content dosyalarını ve XML meta veri dosyalarını birleştirir.  
  
  Proje, görevdeki girişler ve çıktılar arasında bire bir eşleme oluşturmak için dönüşümler kullanır `GenerateContentFiles` . Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md). Ayrıca, `Output` öğesi görevin girişleri olarak görevdeki çıktıları otomatik olarak kullanacak şekilde ayarlanır `GenerateContentFiles` `BuildHelp` .  
  
  Bu proje dosyası hem hem de `Convert` `Build` hedeflerini içerir. `GenerateContentFiles`Ve `BuildHelp` görevleri, `Convert` `Build` her hedefin artımlı olarak kullanılabilmesi için sırasıyla ve hedeflerine yerleştirilir. `Output`Öğesini kullanarak, görevin çıkışları, `GenerateContentFiles` `ContentFile` görev için giriş olarak kullanılabilecekleri öğe listesine yerleştirilir `BuildHelp` . `Output`Öğesinin bu şekilde kullanılması, her bir görevde tek tek öğeleri veya öğe listelerini el ile listelemebilmeniz için bir görevden alınan çıktıları otomatik olarak bir görevden verir.  
  
> [!NOTE]
> `GenerateContentFiles`Hedef artımlı olarak derleyebilir olsa da, bu hedefin tüm çıkışları her zaman hedef için giriş olarak gereklidir `BuildHelp` . [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , öğesini kullandığınızda, bir hedeften farklı bir hedefin giriş olarak tüm çıktıları otomatik olarak sağlar `Output` .  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
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
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lerden](../msbuild/msbuild-targets.md)   
 [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Dönüşümler](../msbuild/msbuild-transforms.md)   
 [Csc görevi](../msbuild/csc-task.md)   
 [Vbc görevi](../msbuild/vbc-task.md)
