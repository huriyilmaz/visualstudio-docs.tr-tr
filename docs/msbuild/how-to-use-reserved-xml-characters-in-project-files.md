---
title: 'Nasıl Kullanılır: Proje Dosyalarında Ayrılmış XML Karakterlerini Kullanma | Microsoft Dokümanlar'
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
ms.openlocfilehash: a041802af1c2fe8cfa195990e6eda3e9b49d773a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633778"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Nasıl kullanılır: Proje dosyalarında ayrılmış XML karakterlerini kullanma

Proje dosyalarını yazarken, örneğin özellik değerlerinde veya görev parametre değerlerinde ayrılmış XML karakterlerini kullanmanız gerekebilir. Ancak, proje dosyasının ayrıştırılabilmeleri için bazı ayrılmış karakterlerin adlandırılmış bir varlık tarafından değiştirilmesi gerekir.

## <a name="use-reserved-characters"></a>Ayrılmış karakterleri kullanma

 Aşağıdaki tabloda, proje dosyasının ayrıştırılması için ilgili adlandırılmış varlık tarafından değiştirilmesi gereken ayrılmış XML karakterleri açıklanmaktadır.

|Ayrılmış karakter|Adlandırılmış varlık|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Proje dosyasında çift tırnak kullanmak için

- Çift tırnak işaretleri karşılık gelen &amp;adlandırılmış varlık, quot;. Örneğin, öğe listesinin `EXEFile` etrafına çift tırnak işareti yerleştirmek için şunları yazın:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Örnek

 Aşağıdaki kod örneğinde, proje dosyası tarafından çıktılanan iletideki dosya adını vurgulamak için çift tırnak işaretleri kullanılır.

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
- [Msbuild](../msbuild/msbuild.md)
