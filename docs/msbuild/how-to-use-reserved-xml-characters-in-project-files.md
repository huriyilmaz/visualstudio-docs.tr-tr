---
title: 'Nasıl yapılır: proje dosyalarında ayrılmış XML karakterlerini kullanma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f60b7d2c0de74743c021feee56a3d9f3c8f3eb5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574333"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Nasıl yapılır: proje dosyalarında ayrılmış XML karakterlerini kullanma
Proje dosyalarını yazdığınızda, örneğin özellik değerlerinde veya görev parametresi değerlerinde ayrılmış XML karakterleri kullanmanız gerekebilir. Ancak, bazı ayrılmış karakterlerin, proje dosyasının ayrıştırılabilmesi için adlandırılmış bir varlıkla değiştirilmeleri gerekir.

## <a name="use-reserved-characters"></a>Ayrılmış karakterleri kullan
 Aşağıdaki tabloda, proje dosyasının ayrıştırılabilmesi için ilgili adlandırılmış varlıkla değiştirilmeleri gereken ayrılmış XML karakterleri açıklanmaktadır.

|Ayrılmış karakter|Adlandırılmış varlık|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Bir proje dosyasında çift tırnakları kullanmak için

- Çift tırnak işaretlerini karşılık gelen adlandırılmış varlıkla değiştirin, &amp;quot;. Örneğin, `EXEFile` öğe listesinin çevresine çift tırnak koymak için şunu yazın:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde, çift tırnak işareti, proje dosyası tarafından çıktı olan iletideki dosya adını vurgulamak için kullanılır.

```xml
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
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
