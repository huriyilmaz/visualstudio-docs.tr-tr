---
title: 'nasıl yapılır: Project dosyalarında ayrılmış XML karakterlerini kullanma | Microsoft Docs'
description: ayrılmış XML karakterlerinin MSBuild proje dosyalarında karşılık gelen adlandırılmış varlıklarla nasıl değiştirileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f307143c89f36c62e45a08a98c78a7c9ba03d1ae
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625676"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Nasıl yapılır: proje dosyalarında ayrılmış XML karakterlerini kullanma

Proje dosyalarını yazdığınızda, örneğin özellik değerlerinde veya görev parametresi değerlerinde ayrılmış XML karakterleri kullanmanız gerekebilir. Ancak, bazı ayrılmış karakterlerin, proje dosyasının ayrıştırılabilmesi için adlandırılmış bir varlıkla değiştirilmeleri gerekir.

## <a name="use-reserved-characters"></a>Ayrılmış karakterleri kullan

 Aşağıdaki tabloda, proje dosyasının ayrıştırılabilmesi için ilgili adlandırılmış varlıkla değiştirilmeleri gereken ayrılmış XML karakterleri açıklanmaktadır.

|Ayrılmış karakter|Adlandırılmış varlık|
|------------------------|------------------|
|\<|&amp;itme|
|>|&amp;>|
|&|&amp;amp|
|"|&amp;quot;|
|'|&amp;apos|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Bir proje dosyasında çift tırnakları kullanmak için

- Çift tırnak işaretlerini karşılık gelen adlandırılmış varlık, &amp; quot; ile değiştirin. Örneğin, öğe listesinin çevresine çift tırnak koymak için `EXEFile` şunu yazın:

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
