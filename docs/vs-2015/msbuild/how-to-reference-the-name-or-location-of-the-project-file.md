---
title: 'Nasıl yapılır: proje dosyasının adına veya konumuna başvurma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eae8a32d4587b71f238c023d08a1328ce83ba37d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64818203"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Nasıl Yapılır: Proje Dosyasının Adına veya Konumuna Başvurma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projenin adını veya konumunu, kendi özelliğini oluşturmak zorunda kalmadan proje dosyasında kullanabilirsiniz. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyası adına ve proje ile ilgili diğer özelliklere başvuran ayrılmış özellikler sağlar. Ayrılmış özellikler hakkında daha fazla bilgi için bkz. [MSBuild ayrılmış ve Iyi bilinen Özellikler](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>MSBuildProjectName özelliğini kullanma  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , her seferinde proje dosyalarınızda kullanabileceğiniz bazı ayrılmış özellikleri sağlar. Örneğin, ayrılmış özelliği `MSBuildProjectName` Proje dosyası adına bir başvuru sağlar.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>MSBuildProjectName özelliğini kullanmak için  
  
- Herhangi bir özellikle yaptığınız gibi, proje dosyasındaki özelliğine $ () gösterimiyle başvurun. Örneğin:  
  
  ```  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```  
  
  Ayrılmış bir özellik kullanmanın bir avantajı, proje dosya adında yapılan tüm değişikliklerin otomatik olarak eklenmesine olanak sağlar. Projeyi bir sonraki oluşturduğunuzda, çıkış dosyası, sizin bölüminizdeki başka bir eylemde bulunması gereken yeni bir ada sahip olacaktır.  
  
> [!NOTE]
> Ayrılmış Özellikler proje dosyasında yeniden tanımlanamaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek proje dosyası, çıkış için adı belirtmek üzere bir ayrılmış özellik olarak proje adına başvurur.  
  
```  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[MSBUILD](msbuild.md)  
 [MSBuild ayrılmış ve Iyi bilinen Özellikler](../msbuild/msbuild-reserved-and-well-known-properties.md)
