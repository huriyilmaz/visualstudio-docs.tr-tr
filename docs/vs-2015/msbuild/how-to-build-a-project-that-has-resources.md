---
title: 'Nasıl yapılır: kaynakları olan bir proje derleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb77db891e824f5f2900ef191049e65cb2c89a98
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686526"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Nasıl Yapılır: Kaynaklara Sahip Olan Bir Projeyi Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir projenin yerelleştirilmiş sürümlerini oluşturuyorsanız, tüm Kullanıcı arabirimi öğelerinin farklı diller için kaynak dosyalarına ayrılması gerekir. Proje yalnızca dizeleri kullanıyorsa, kaynak dosyaları metin dosyalarını kullanabilir. Alternatif olarak,. resx dosyalarını kaynak dosyaları olarak da kullanabilirsiniz.  
  
## <a name="compiling-resources-with-msbuild"></a>MSBuild ile kaynakları derleme  
 İle birlikte sunulan ortak görevlerin kitaplığı, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] `GenerateResource` . resx veya metin dosyalarında kaynak derlemek için kullanabileceğiniz bir görevi içerir. Bu görev, `Sources` derlenecek kaynak dosyalarını ve `OutputResources` çıkış kaynak dosyalarının adlarını belirtmek için parametresini belirten parametresini içerir. Görev hakkında daha fazla bilgi için `GenerateResource` bkz. [GenerateResource Task](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>MSBuild ile kaynakları derlemek için  
  
1. Projenin kaynak dosyalarını belirleyip `GenerateResource` , öğe listeleri olarak veya dosya adları olarak görevlere geçirin.  
  
2. `OutputResources` `GenerateResource` Çıkış kaynak dosyaları için adları ayarlamanıza olanak sağlayan görevin parametresini belirtin.  
  
3. `Output` `OutputResources` Parametresinin değerini bir öğe içinde depolamak için görevin öğesini kullanın.  
  
4. Öğesinden oluşturulan öğeyi `Output` başka bir görevde giriş olarak kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `Output` öğesinin `OutputResources` `GenerateResource` görev özniteliğinin derlenmiş kaynak dosyalarını içereceği ve `alpha.resources` `beta.resources` Bu iki dosyanın `Resources` öğe listesi içine yerleştirileceği yöntemi gösterir. Bu. resources dosyalarını aynı ada sahip öğelerin bir koleksiyonu olarak tanımlayarak, onları [CSC](../msbuild/csc-task.md) görevi gibi başka bir görevin girişleri olarak kolayca kullanabilirsiniz.  
  
 Bu görev, [Resgen.exe](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)için **/Compile** anahtarını kullanma ile eşdeğerdir:  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek proje iki görev içerir: `GenerateResource` kaynakları derlemek için görev ve `Csc` hem kaynak kodu dosyalarını hem de derlenen kaynak dosyalarını derlemek için görev. Görev tarafından derlenen kaynak dosyaları `GenerateResource` , `Resources` öğede depolanır ve `Csc` göreve geçirilir.  
  
```  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[MSBUILD](msbuild.md)  
 [GenerateResource Görevi](../msbuild/generateresource-task.md)   
 [Csc görevi](../msbuild/csc-task.md)   
 [Resgen.exe (kaynak dosya Oluşturucu)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)
