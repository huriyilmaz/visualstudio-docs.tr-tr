---
title: 'Nasıl yapılandırılır: Hedefleri ve Görevleri Yapılandırma | Microsoft Docs'
description: Geliştirme bilgisayarının ortamından MSBuild bakılmaksızın, seçilen görev ve görevleri hedeflenin ortamında çalıştıracak şekilde ayarlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 724e187d00c977feada2412e9e3445f2c6db1ea6
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130212227"
---
# <a name="how-to-configure-targets-and-tasks"></a>Nasıl yapılandırılır: Hedefleri ve görevleri yapılandırma

Seçilen MSBuild görevleri, geliştirme bilgisayarının ortamından bağımsız olarak hedeflenin ortamında çalıştıracak şekilde ayarlanmış olabilir. Örneğin, 32 bit mimariyi hedef alan bir uygulama oluşturmak için 64 bit bir bilgisayar kullanırsanız, seçilen görevler 32 bit bir işlemde kullanılır.

> [!NOTE]
> Bir derleme görevi Visual C# veya Visual Basic gibi bir .NET dilinde yazılmışsa ve yerel kaynakları veya araçları kullanmayacaksa, uyarlama olmadan herhangi bir hedef bağlamda çalıştıracak.

## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask öznitelikleri ve görev parametreleri

Aşağıdaki `UsingTask` öznitelikler belirli bir derleme sürecindeki bir görevin tüm işlemlerini etkiler:

- Varsa özniteliği ortak dil çalışma zamanı (CLR) sürümünü ayarlar ve şu değerlerden birini `Runtime` alır: `CLR2` , , veya `CLR4` `CurrentRuntime` `*` (herhangi bir çalışma zamanı).

- Varsa özniteliği, platformu ve bitliği ayarlar ve şu değerlerden herhangi birini `Architecture` alır: `x86` , , veya `x64` `CurrentArchitecture` `*` (herhangi bir mimari).

- Varsa `TaskFactory` özniteliği, görev örneğini oluşturan ve çalıştıran görev fabrikasını ayarlar ve yalnızca değerini `TaskHostFactory` alır. Daha fazla bilgi için bu [belgenin devamlarında](#task-factories) yer alan Görev fabrikaları'ne bakın.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Tek bir görev `MSBuildRuntime` `MSBuildArchitecture` çağrılarının hedef bağlamını ayarlamak için ve parametrelerini de kullanabilirsiniz.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Bir MSBuild çalıştırmadan önce, aynı hedef bağlama `UsingTask` sahip bir eşleştirmeyi çalıştırır. içinde belirtilen ancak karşılık `UsingTask` gelen görevde olmayan parametrelerin eş olduğu kabul edilir. Görevde belirtilen ancak karşılık gelen parametrelerin `UsingTask` eşleşmesi de kabul edilir. veya görevsinde parametre değerleri `UsingTask` belirtilmezse, değerler varsayılan olarak (herhangi bir `*` parametre) olur.

> [!WARNING]
> Birden fazla varsa ve hepsi eşleşen , ve özniteliklerine sahipse, değerlendirilecek son öznitelik `UsingTask` `TaskName` diğerlerini `Runtime` `Architecture` değiştirir.

 Görev üzerinde parametreler ayarlanırsa, MSBuild bu parametrelerle eşleşen bir bulmaya çalışır veya en azından `UsingTask` bu parametrelerle çakışmaz. Aynı görevin `UsingTask` hedef bağlamını birden fazla kişi belirtebilirsiniz. Örneğin, farklı hedef ortamlar için farklı yürütülebilir dosyaları olan bir görev aşağıdakine benzer olabilir:

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

Bir görevi çalıştırmadan önce, MSBuild yazılım bağlamında çalışması için atanıp atanmay olmadığını denetler. Görev bu kadar belirlenmişse, MSBuild assemblyTaskFactory'ye iletir ve bu da onu geçerli işlemde çalıştırır; aksi MSBuild, görevi hedef bağlamla eşleşen bir işlemde çalıştıran TaskHostFactory'ye iletir. Geçerli bağlam ve hedef bağlam eşlese bile, ayarını olarak ayarerek bir görevi işlem dışı (yalıtım, güvenlik veya diğer nedenlerle) çalıştırmaya `TaskFactory` `TaskHostFactory` zorlarsiniz.

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Görev parametreleri

Diğer görev parametreleri gibi ve `MSBuildRuntime` `MSBuildArchitecture` de derleme özelliklerinden ayarlanır.

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

Diğer görev parametrelerinin aksine `MSBuildRuntime` `MSBuildArchitecture` ve, görevin kendisine açık değildir. Çalıştırılan bağlamın farkında olan bir görev yazmak için, .NET Framework çağırarak bağlamı test edin veya diğer görev parametreleri aracılığıyla bağlam bilgilerini geçmek için derleme özelliklerini kullanın.

> [!NOTE]
> `UsingTask` öznitelikleri, araç takımı ve ortam özelliklerinden ayarlanabilirsiniz.

ve `MSBuildRuntime` `MSBuildArchitecture` parametreleri, hedef bağlamı ayarlamak için en esnek yolu sağlar, ancak aynı zamanda en sınırlı kapsamdır. Bir yandan, görev örneğinde ayarlandıklarından ve görev çalıştırılana kadar değerlendirilmemiş olduğundan, değerlerini hem değerlendirme zamanında hem de derleme zamanında kullanılabilen özelliklerin tam kapsamından türetirler. Öte yandan, bu parametreler yalnızca belirli bir hedefte görevin belirli bir örneği için geçerlidir.

> [!NOTE]
> Görev parametreleri, görev ana bilgisayarı bağlamında değil üst düğüm bağlamında değerlendirilir. Çalışma zamanı veya mimariye bağımlı ortam değişkenleri *(Program Dosyaları* konumu gibi) üst düğümle eşleşen değeri değerlendirir. Ancak, aynı ortam değişkeni görev tarafından doğrudan okunursa, görev ana bilgisayarı bağlamında doğru şekilde değerlendirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hedefleri ve görevleri yapılandırma](../msbuild/configure-tasks.md)
- [UsingTask öğesi](../msbuild/usingtask-element-msbuild.md)
