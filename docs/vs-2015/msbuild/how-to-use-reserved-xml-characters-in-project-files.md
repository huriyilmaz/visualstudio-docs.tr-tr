---
title: 'Nasıl yapılır: proje dosyalarında ayrılmış XML karakterlerini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aba17e94486ca04e12055c7bf9959f927440c53d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178306"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Nasıl Yapılır: Proje Dosyalarında Ayrılmış XML Karakterlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje dosyalarını yazdığınızda, örneğin özellik değerlerinde veya görev parametresi değerlerinde ayrılmış XML karakterleri kullanmanız gerekebilir. Ancak, bazı ayrılmış karakterlerin, proje dosyasının ayrıştırılabilmesi için adlandırılmış bir varlıkla değiştirilmeleri gerekir.  
  
## <a name="using-reserved-characters"></a>Ayrılmış karakterler kullanma  
 Aşağıdaki tabloda, proje dosyasının ayrıştırılabilmesi için ilgili adlandırılmış varlıkla değiştirilmeleri gereken ayrılmış XML karakterleri açıklanmaktadır.  
  
|Ayrılmış karakter|Adlandırılmış varlık|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Bir proje dosyasında çift tırnakları kullanmak için  
  
- Çift tırnak işaretlerini karşılık gelen adlandırılmış varlıkla değiştirin, &quot; . Örneğin, öğe listesinin çevresine çift tırnak koymak için `EXEFile` şunu yazın:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, çift tırnak işareti, proje dosyası tarafından çıktı olan iletideki dosya adını vurgulamak için kullanılır.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)
