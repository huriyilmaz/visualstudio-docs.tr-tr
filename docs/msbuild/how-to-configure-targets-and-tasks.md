---
title: 'Nasıl Yapılandırılır: Hedefleri ve Görevleri Yapılandırma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe2955feb50a28e5ba631cdeddd169973a42ed25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633895"
---
# <a name="how-to-configure-targets-and-tasks"></a>Nasıl yapilir: Hedefleri ve görevleri yapılandırma

Seçili MSBuild görevleri, geliştirme bilgisayarının ortamından bağımsız olarak hedefledikleri ortamda çalışacak şekilde ayarlanabilir. Örneğin, 32 bitlik bir mimariyi hedefleyen bir uygulama oluşturmak için 64 bit lik bir bilgisayar kullandığınızda, seçili görevler 32 bit lik bir işlemle çalıştırılır.
Seçili MSBuild görevleri, geliştirme bilgisayarının ortamından bağımsız olarak hedefledikleri ortamda çalışacak şekilde ayarlanabilir. Örneğin, 32 bitlik bir mimariyi hedefleyen bir uygulama oluşturmak için 64 bit lik bir bilgisayar kullandığınızda, seçili görevler 32 bit lik bir işlemle çalıştırılır.

> [!NOTE]
> Bir yapı görevi Visual C# veya Visual Basic gibi bir .NET dilinde yazılmışsa ve yerel kaynakları veya araçları kullanmıyorsa, uyarlama olmadan herhangi bir hedef bağlamda çalışır.

## <a name="usingtask-attributes-and-task-parameters"></a>Görev özniteliklerini ve görev parametrelerini kullanma

Aşağıdaki `UsingTask` öznitelikler, belirli bir yapı işleminde görevin tüm işlemlerini etkiler:

- Öznitelik, `Runtime` varsa, ortak dil çalışma zamanı (CLR) sürümünü ayarlar ve bu `CLR2`değerlerden herhangi birini alabilir: , `CLR4` `CurrentRuntime`, veya `*` (herhangi bir çalışma zamanı).

- Öznitelik, `Architecture` varsa, platformu ve bitness ayarlar ve bu değerlerden `x86`herhangi `x64` `CurrentArchitecture`birini `*` alabilir: , , veya (herhangi bir mimari).

- Öznitelik, `TaskFactory` varsa, görev örneğini oluşturan ve çalıştıran görev fabrikasını ayarlar `TaskHostFactory`ve yalnızca değeri alır. Daha fazla bilgi için, bu belgede daha sonra [Görev fabrikalarına](#task-factories) bakın.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Ayrıca, tek `MSBuildRuntime` bir `MSBuildArchitecture` görevin hedef bağlamını ayarlamak için parametreleri ve parametreleri de kullanabilirsiniz.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

MSBuild bir görevi çalıştırmadan önce, `UsingTask` aynı hedef içeriğe sahip bir eşlemi arar. İlgili görevde belirtilmeyen `UsingTask` ancak belirtilen parametreler eşleştirilmiş olarak kabul edilir. Görevde belirtilen ancak karşılık gelen `UsingTask` parametrelerde olmayan parametreler de eşlenmiş olarak kabul edilir. Parametre değerleri görevde `UsingTask` veya görevde belirtilmemişse, `*` varsayılan değerler (herhangi bir parametre).

> [!WARNING]
> Birden `UsingTask` fazla var ve tüm `TaskName` `Runtime`eşleşen `Architecture` varsa , , ve öznitelikleri, değerlendirilecek son bir diğerleri yerini alır.

 Görevde parametreler ayarlanmışsa, MSBuild bu `UsingTask` parametrelerle eşleşen veya en azından onlarla çakışmayan bir tane bulmaya çalışır. Aynı görevin hedef bağlamını birden `UsingTask` fazla kişi belirtebilir. Örneğin, farklı hedef ortamlar için farklı yürütülebilir leri olan bir görev buna benzeyebilir:

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

Bir görevi çalıştırmadan önce, MSBuild geçerli yazılım bağlamında çalışacak şekilde atanıp atanmadığını denetlemek için denetler. Görev bu kadar atanmışsa, MSBuild bu görevi geçerli işlemde çalıştıran AssemblyTaskFactory'ye geçirir; aksi takdirde, MSBuild görevi hedef bağlamla eşleşen bir işlemde görevi çalıştıran TaskHostFactory'ye geçirir. Geçerli bağlam ve hedef bağlam eşleşse bile, bir görevi işlemi (yalıtım, güvenlik veya diğer nedenlerle) olarak ayarlayarak `TaskFactory` çalıştırmaya `TaskHostFactory`zorlayabilirsiniz.

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Hayalet görev parametreleri

Diğer görev parametreleri `MSBuildRuntime` `MSBuildArchitecture` gibi ve yapı özelliklerinden ayarlanabilir.

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

Diğer görev parametrelerinden farklı olarak görev `MSBuildRuntime` `MSBuildArchitecture` in kendisi tarafından belirgin değildir. Çalıştığı bağlamın farkında olan bir görev yazmak için,.NET Framework'ü çağırarak bağlamı sınamanız veya bağlam bilgilerini diğer görev parametrelerinden geçirmek için yapı özelliklerini kullanmanız gerekir.

> [!NOTE]
> `UsingTask`öznitelikleri araç kümesi ve ortam özelliklerinden ayarlanabilir.

Ve `MSBuildRuntime` `MSBuildArchitecture` parametreler, hedef bağlamı ayarlamak için en esnek yolu sağlar, ancak aynı zamanda kapsamı en sınırlı. Bir yandan, görev örneğinin kendisi üzerinde ayarlandıkları ve görev çalışma kaynırına kadar değerlendirilmedikleri için, değerlerini hem değerlendirme zamanı hem de yapı zamanında kullanılabilen özelliklerin tam kapsamından elde edebilirler. Diğer taraftan, bu parametreler yalnızca belirli bir hedefteki bir görevin belirli bir örneğine uygulanır.

> [!NOTE]
> Görev parametreleri, görev ana bilgisayarı bağlamında değil, üst düğüm bağlamında değerlendirilir. Çalışma zamanı veya mimariye bağımlı olan ortam değişkenleri *(Program Dosyaları* konumu gibi) üst düğümle eşleşen değere göre değerlendirilir. Ancak, aynı ortam değişkeni doğrudan görev tarafından okunursa, görev ana bilgisayarı bağlamında doğru bir şekilde değerlendirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hedefleri ve görevleri yapılandırma](../msbuild/configuring-targets-and-tasks.md)
