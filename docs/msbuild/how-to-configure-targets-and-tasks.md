---
title: 'Nasıl yapılır: hedefleri ve görevleri yapılandırma | Microsoft Docs'
description: Seçilen MSBuild görevlerinin, hedeflenen ortamda çalışması için geliştirme bilgisayarının ortamından bağımsız olarak nasıl ayarlanacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22dcb7a209b8a62aaeb3c036b1013e7ad3d21597
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914440"
---
# <a name="how-to-configure-targets-and-tasks"></a>Nasıl yapılır: hedefleri ve görevleri yapılandırma

Seçilen MSBuild görevleri, geliştirme bilgisayarının ortamından bağımsız olarak, hedefdukları ortamda çalışmak üzere ayarlanabilir. Örneğin, 32 bit mimarisini hedefleyen bir uygulama oluşturmak için 64 bitlik bir bilgisayar kullandığınızda, seçilen görevler 32-bit işlemde çalıştırılır.
Seçilen MSBuild görevleri, geliştirme bilgisayarının ortamından bağımsız olarak, hedefdukları ortamda çalışmak üzere ayarlanabilir. Örneğin, 32 bit mimarisini hedefleyen bir uygulama oluşturmak için 64 bitlik bir bilgisayar kullandığınızda, seçilen görevler 32-bit işlemde çalıştırılır.

> [!NOTE]
> Bir derleme görevi, Visual C# veya Visual Basic gibi bir .NET dilinde yazılmışsa ve yerel kaynakları veya araçları kullanmıyorsa, bu durumda herhangi bir hedef bağlamda uyarlama olmadan çalıştırılır.

## <a name="usingtask-attributes-and-task-parameters"></a>Görev özniteliklerini ve görev parametrelerini using

Aşağıdaki `UsingTask` öznitelikler belirli bir yapı işlemindeki bir görevin tüm işlemlerini etkiler:

- Varsa `Runtime` özniteliği, ortak dil çalışma zamanı (CLR) sürümünü ayarlar ve şu değerlerden herhangi birini alabilir: `CLR2` , `CLR4` , `CurrentRuntime` , veya `*` (herhangi bir çalışma zamanı).

- Varsa `Architecture` özniteliği, platformu ve bit boyutunu ayarlar ve şu değerlerden herhangi birini alabilir: `x86` , `x64` , `CurrentArchitecture` , veya `*` (herhangi bir mimari).

- Varsa `TaskFactory` özniteliği, görev örneğini oluşturan ve çalıştıran görev fabrikasını ayarlar ve yalnızca değeri alır `TaskHostFactory` . Daha fazla bilgi için bu belgede daha sonra [görev fabrikaları](#task-factories) bölümüne bakın.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Ayrıca, `MSBuildRuntime` `MSBuildArchitecture` tek bir görevin hedef bağlamını ayarlamak için ve parametrelerini de kullanabilirsiniz.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

MSBuild bir görevi çalıştırmadan önce, `UsingTask` aynı hedef bağlamına sahip bir eşleştirmeyi arar. `UsingTask`Buna karşılık gelen görevde belirtilen parametreler, eşleştirildiği kabul edilir. Görevde belirtilen ancak karşılık gelen parametreler `UsingTask` aynı zamanda eşleştirilecek olarak kabul edilir. Parametre değerleri `UsingTask` ya da görevde belirtilmemişse, değerler varsayılan olarak ' dir `*` (any parametresi).

> [!WARNING]
> Birden fazla varsa `UsingTask` ve tümü eşleşen `TaskName` , `Runtime` , ve `Architecture` niteliklerine sahip ise, değerlendirilecek son bir tane diğerleri tarafından değiştirilir.

 Görev üzerinde parametreler ayarlandıysa, MSBuild bu parametrelerle eşleşen bir a bulmaya çalışır `UsingTask` veya en azından, bunlarla çakışmaz. `UsingTask`Aynı görevin hedef bağlamını birden çok belirtebilir. Örneğin, farklı hedef ortamları için farklı yürütülebilir dosyaları olan bir görev şuna benzeyebilir:

```xml
<UsingTask TaskName="MyTool"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />

<UsingTask TaskName="MyTool"
    Runtime="CLR4"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />

<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>

```

## <a name="task-factories"></a>Görev fabrikaları

MSBuild, bir görev çalıştırmadan önce geçerli yazılım bağlamında çalışmak üzere belirlenmiş olup olmadığını denetler. Görev bu şekilde belirlendiyse, MSBuild onu geçerli işlemde çalıştıran AssemblyTaskFactory öğesine geçirir; Aksi halde, MSBuild, görevi hedef bağlamla eşleşen bir işlemde çalıştıran TaskHostFactory 'ye geçirir. Geçerli bağlam ve hedef bağlam eşleşse bile, ' ye ayarlayarak bir görevi işlem dışı çalıştırmaya (yalıtım, güvenlik veya diğer nedenler için) zorlayabilirsiniz `TaskFactory` `TaskHostFactory` .

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Hayalet görev parametreleri

Diğer görev parametreleri gibi, `MSBuildRuntime` `MSBuildArchitecture` derleme özelliklerinden de ayarlanabilir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <FrameworkVersion>3.0</FrameworkVersion>
    </PropertyGroup>
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Diğer görev parametrelerinin aksine, `MSBuildRuntime` ve `MSBuildArchitecture` görevin kendisi için görünür değildir. Çalıştırıldığı bağlamı algılayan bir görev yazmak için, .NET Framework çağırarak bağlamı test etmeniz veya yapı özelliklerini kullanarak bağlam bilgilerini diğer görev parametreleriyle geçirebilirsiniz.

> [!NOTE]
> `UsingTask` Öznitelikler, araç kümesi ve ortam özelliklerinden ayarlanabilir.

`MSBuildRuntime`Ve `MSBuildArchitecture` parametreleri, hedef bağlamını ayarlamak için en esnek yolu sağlar, aynı zamanda en sınırlı kapsam kapsamını da sunar. Tek seferde, görev örneği üzerinde ayarlandığı ve görev çalışmak üzere değerlendirilene kadar değerlendirilmediği için, her iki değerlendirme zamanı ve derleme zamanında kullanılabilen özelliklerin tam kapsamından değerlerini türetebilirler. Diğer taraftan, bu parametreler yalnızca belirli bir hedefteki bir görevin belirli bir örneği için geçerlidir.

> [!NOTE]
> Görev parametreleri, görev ana bilgisayarı bağlamında değil, üst düğüm bağlamında değerlendirilir. Çalışma zamanı veya mimariye bağımlı ( *Program dosyaları* konumu gibi) ortam değişkenlerine üst düğümle eşleşen değer değerlendirilir. Ancak, aynı ortam değişkeni doğrudan görev tarafından okunmalıdır, görev ana bilgisayarı bağlamında doğru olarak değerlendirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hedefleri ve görevleri yapılandırma](../msbuild/configuring-targets-and-tasks.md)
- [UsingTask öğesi](../msbuild/usingtask-element-msbuild.md)
