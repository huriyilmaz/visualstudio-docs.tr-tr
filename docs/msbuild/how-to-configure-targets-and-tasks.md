---
title: 'Nasıl yapılır: hedefleri ve görevleri yapılandırma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe2955feb50a28e5ba631cdeddd169973a42ed25
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633895"
---
# <a name="how-to-configure-targets-and-tasks"></a>Nasıl yapılır: hedefleri ve görevleri yapılandırma

Seçilen MSBuild görevleri, geliştirme bilgisayarının ortamından bağımsız olarak, hedefdukları ortamda çalışmak üzere ayarlanabilir. Örneğin, 32 bit mimarisini hedefleyen bir uygulama oluşturmak için 64 bitlik bir bilgisayar kullandığınızda, seçilen görevler 32-bit işlemde çalıştırılır.
Seçilen MSBuild görevleri, geliştirme bilgisayarının ortamından bağımsız olarak, hedefdukları ortamda çalışmak üzere ayarlanabilir. Örneğin, 32 bit mimarisini hedefleyen bir uygulama oluşturmak için 64 bitlik bir bilgisayar kullandığınızda, seçilen görevler 32-bit işlemde çalıştırılır.

> [!NOTE]
> Bir derleme görevi görsel C# veya Visual Basic gibi bir .net dilinde yazılmışsa ve yerel kaynakları veya araçları kullanmıyorsa, bu durumda herhangi bir hedef bağlamda uyarlama olmadan çalıştırılır.

## <a name="usingtask-attributes-and-task-parameters"></a>Görev özniteliklerini ve görev parametrelerini using

Aşağıdaki `UsingTask` öznitelikleri, belirli bir yapı işlemindeki bir görevin tüm işlemlerini etkiler:

- Varsa `Runtime` özniteliği, ortak dil çalışma zamanı (CLR) sürümünü ayarlar ve şu değerlerden herhangi birini gerçekleştirebilir: `CLR2`, `CLR4`, `CurrentRuntime`veya `*` (herhangi bir çalışma zamanı).

- Varsa `Architecture` özniteliği, platformu ve bit boyutunu ayarlar ve şu değerlerden herhangi birini gerçekleştirebilir: `x86`, `x64`, `CurrentArchitecture`veya `*` (herhangi bir mimari).

- Varsa `TaskFactory` özniteliği, görev örneğini oluşturan ve çalıştıran görev fabrikasını ayarlar ve yalnızca `TaskHostFactory`değerini alır. Daha fazla bilgi için bu belgede daha sonra [görev fabrikaları](#task-factories) bölümüne bakın.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Tek bir görevin hedef bağlamını ayarlamak için `MSBuildRuntime` ve `MSBuildArchitecture` parametrelerini de kullanabilirsiniz.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

MSBuild bir görevi çalıştırmadan önce, aynı hedef bağlamına sahip eşleşen bir `UsingTask` arar. `UsingTask` belirtilen ancak karşılık gelen görevde olmayan parametreler eşleştirildiği kabul edilir. Görevde belirtilen ancak karşılık gelen `UsingTask` olmayan parametreler de eşleştirildiği kabul edilir. Parametre değerleri `UsingTask` veya görevde belirtilmemişse, değerler varsayılan olarak `*` (herhangi bir parametre).

> [!WARNING]
> Birden fazla `UsingTask` varsa ve tümü eşleşen `TaskName`, `Runtime`ve `Architecture` özniteliklerine sahip olursa, değerlendirilecek son, diğerleri tarafından değiştirilir.

 Görev üzerinde parametreler ayarlandıysa MSBuild, bu parametrelerle eşleşen bir `UsingTask` bulmaya çalışır veya en azından, bunlarla çakışmaz. Birden fazla `UsingTask` aynı görevin hedef bağlamını belirtebilir. Örneğin, farklı hedef ortamları için farklı yürütülebilir dosyaları olan bir görev şuna benzeyebilir:

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

MSBuild, bir görev çalıştırmadan önce geçerli yazılım bağlamında çalışmak üzere belirlenmiş olup olmadığını denetler. Görev bu şekilde belirlendiyse, MSBuild onu geçerli işlemde çalıştıran AssemblyTaskFactory öğesine geçirir; Aksi halde, MSBuild, görevi hedef bağlamla eşleşen bir işlemde çalıştıran TaskHostFactory 'ye geçirir. Geçerli bağlam ve hedef bağlam eşleşse bile, `TaskFactory` `TaskHostFactory`ayarlayarak bir görevi işlem dışı (yalıtım, güvenlik veya diğer nedenlerle) çalıştırmaya zorlayabilirsiniz.

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Hayalet görev parametreleri

Diğer görev parametreleri gibi `MSBuildRuntime` ve `MSBuildArchitecture` derleme özelliklerinden de ayarlanabilir.

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

Diğer görev parametrelerinden farklı olarak, `MSBuildRuntime` ve `MSBuildArchitecture` görevin kendisi için görünür değildir. Çalıştırıldığı bağlamı algılayan bir görev yazmak için, .NET Framework çağırarak bağlamı test etmeniz veya yapı özelliklerini kullanarak bağlam bilgilerini diğer görev parametreleriyle geçirebilirsiniz.

> [!NOTE]
> `UsingTask` öznitelikleri, araç kümesi ve ortam özelliklerinden ayarlanabilir.

`MSBuildRuntime` ve `MSBuildArchitecture` parametreleri, hedef bağlamını ayarlamak için en esnek yolu ve aynı zamanda en sınırlı kapsamı sağlar. Tek seferde, görev örneği üzerinde ayarlandığı ve görev çalışmak üzere değerlendirilene kadar değerlendirilmediği için, her iki değerlendirme zamanı ve derleme zamanında kullanılabilen özelliklerin tam kapsamından değerlerini türetebilirler. Diğer taraftan, bu parametreler yalnızca belirli bir hedefteki bir görevin belirli bir örneği için geçerlidir.

> [!NOTE]
> Görev parametreleri, görev ana bilgisayarı bağlamında değil, üst düğüm bağlamında değerlendirilir. Çalışma zamanı veya mimariye bağımlı ( *Program dosyaları* konumu gibi) ortam değişkenlerine üst düğümle eşleşen değer değerlendirilir. Ancak, aynı ortam değişkeni doğrudan görev tarafından okunmalıdır, görev ana bilgisayarı bağlamında doğru olarak değerlendirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hedefleri ve görevleri yapılandırma](../msbuild/configuring-targets-and-tasks.md)
