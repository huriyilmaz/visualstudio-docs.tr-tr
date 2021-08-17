---
title: 'Nasıl kullanılır: Project Dosyalarında Ayrılmış XML Karakterlerini | Microsoft Docs'
description: Ayrılmış XML karakterlerini proje dosyalarındaki karşılık gelen adlandırılmış varlıklarla MSBuild öğrenin.
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
ms.openlocfilehash: 202266e37be65486a7db0de33f0713842ff8e3c755fcd4c3cba6fe6c780a39da
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443509"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Nasıl kullanılır: Proje dosyalarında ayrılmış XML karakterlerini kullanma

Proje dosyaları yazarken, örneğin özellik değerlerde veya görev parametresi değerlerde ayrılmış XML karakterlerini kullanabilirsiniz. Ancak, proje dosyasının ayrıştırılana kadar bazı ayrılmış karakterlerin adlandırılmış bir varlıkla değiştirilmesi gerekir.

## <a name="use-reserved-characters"></a>Ayrılmış karakterler kullanma

 Aşağıdaki tabloda, proje dosyasının ayrıştırılana kadar karşılık gelen adlandırılmış varlıkla değiştirilmesi gereken ayrılmış XML karakterleri açıklandı.

|Ayrılmış karakter|Adlandırılmış varlık|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Proje dosyasında çift tırnak kullanmak için

- Çift tırnakları karşılık gelen adlandırılmış varlık olan &amp; quot; ile değiştirin. Örneğin, öğe listesinin etrafına çift tırnaklar `EXEFile` yer açmak için yazın:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Örnek

 Aşağıdaki kod örneğinde, proje dosyasının çıkışı olan iletide dosya adını vurgulamak için çift tırnak kullanılmıştır.

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
