---
title: MSBuild Görev | Microsoft Docs
description: MSBuild görevinin, başka bir MSBuild projeden alt proje oluşturmak için aynı MSBuild öğrenin.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 97ebe6c55754ae3759a28c6df65eadaa11604ad63244f0fdc0aed22802b571b9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397468"
---
# <a name="msbuild-task"></a>MSBuild görevi

Başka bir MSBuild projeden bir MSBuild derlemesi.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `MSBuild` almaktadır.

| Parametre | Açıklama |
|-----------------------------------| - |
| `BuildInParallel` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` parametresinde belirtilen `Projects` projeler mümkünse paralel olarak yerleşiktir. `false` varsayılan değerdir. |
| `Projects` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Derlemek için proje dosyalarını belirtir. |
| `Properties` | İsteğe `String` bağlı parametre.<br /><br /> Alt projeye genel özellikler olarak uygulanacak özellik adı/değer çiftlerinin noktalı virgülle ayrılmış listesi. Bu parametreyi belirttiğinizde, bu işlev, ile derlemesi yapılan **-property** anahtarına sahip özellikleri ayarlamaya [*eşdeğer*](../msbuild/msbuild-command-line-reference.md)MSBuild.exe. Örnek:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Özellikleri projeye parametresi aracılığıyla iletirken, MSBuild dosyası zaten yüklenmiş olsa bile projenin yeni bir örneğini `Properties` oluşturabilirsiniz. MSBuild bir proje yolu için tek bir proje örneği ve benzersiz bir genel özellikler kümesi oluşturur. Örneğin, bu davranış Configuration=Release ile *myproject.proj* çağıran birden çok MSBuild görevi oluşturmanıza olanak sağlar ve *tek bir myproject.proj* örneği alırsınız (görevde benzersiz bir özellik belirtilmezse). MSBuild tarafından henüz görülemeyen bir özellik belirtir MSBuild, projenin diğer örneklerine paralel olarak inşa edilen yeni bir örnek oluşturur. Örneğin, Bir Yayın yapılandırması bir Hata Ayıklama yapılandırmasıyla aynı anda derlemek için kullanılabilir.|
| `RebaseOutputs` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, yerleşik projelerden hedef çıkış öğelerinin göreli yolları, çağıran projeye `true` göre ayarlanmıştır. `false` varsayılan değerdir. |
| `RemoveProperties` | İsteğe `String` bağlı parametre.<br /><br /> Kaldır eklenecek genel özellikler kümesi belirtir. |
| `RunEachTargetSeparately` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, MSBuild görev, listede geçirilen her hedefi MSBuild yerine tek tek `true` çağırır. Bu `true` parametreyi, daha önce çağrılan hedefler başarısız olsa bile sonraki hedeflerin çağrılmalarını garanti etmek için olarak ayarlama. Aksi takdirde, bir derleme hatası sonraki tüm hedeflerin çağrılmalarını durdurur. `false` varsayılan değerdir. |
| `SkipNonexistentProjects` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` diskte mevcut olmayan proje dosyaları atlanır. Aksi takdirde, bu tür projeler hataya neden olur. |
|`SkipNonexistentTargets`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` mevcut olan ancak adlandırılmış dosya içermeen proje dosyaları `Targets` atlanır. Aksi takdirde, bu tür projeler hataya neden olur. 15.5 MSBuild tanıtıldı.|
| `StopOnFirstFailure` | İsteğe `Boolean` bağlı parametre.<br /><br /> Projelerden `true` biri derleme başarısız olursa, başka proje derlemez. Şu anda bu, paralel olarak (birden çok işlemci ile) derlerken desteklenmiyor. |
| `TargetAndPropertyListSeparators` | İsteğe `String[]` bağlı parametre.<br /><br /> Öğe meta verileri olarak hedeflerin ve özelliklerin listesini `Project` belirtir). İşlemeden önce ayırıcılar kaçağın kaçmayacak. Örn. %3B (';'), ';' olarak ele alınmıştır. |
| `TargetOutputs` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Tüm proje dosyalarından yerleşik hedeflerin çıkışlarını döndürür. Yalnızca belirtilen hedeflerden gelen çıkışlar döndürülür; bu hedeflerin bağımlı olduğu hedeflerde mevcut olan çıkışlar döndürülz.<br /><br /> parametresi `TargetOutputs` aşağıdaki meta verileri de içerir:<br /><br /> -   `MSBuildSourceProjectFile`: MSBuild ayar hedefini içeren bir proje dosyasıdır.<br />-   `MSBuildSourceTargetName`: Çıkışları ayar alan hedef. **Not:**  Her proje dosyasından veya hedeften gelen çıkışları ayrı olarak tanımlamak için, görevi her proje dosyası veya hedef `MSBuild` için ayrı olarak çalıştırın. Görevi yalnızca bir kez çalıştırarak tüm proje dosyalarını oluşturursanız, tüm `MSBuild` hedeflerin çıkışları tek bir dizide toplanır. |
| `Targets` | İsteğe `String` bağlı parametre.<br /><br /> Proje dosyalarında derlemek için hedefi veya hedefleri belirtir. Hedef adların listesini ayırmak için noktalı virgül kullanın. Görevde herhangi bir hedef `MSBuild` belirtilmezse, proje dosyalarında belirtilen varsayılan hedefler yerleşiktir. **Not:**  Hedeflerin tüm proje dosyalarında gerçekleşmesi gerekir. Yoksa bir derleme hatası oluşur. |
| `ToolsVersion` | İsteğe `String` bağlı parametre.<br /><br /> Bu göreve `ToolsVersion` geçirilen projelerin ne zaman kullanıcalarını belirtir.<br /><br /> Bir MSBuild, projenin projesinde belirtilenden farklı bir sürümünü .NET Framework proje derlemesini sağlar. Geçerli değerler `2.0` , ve `3.0` `3.5` değerleridir. Varsayılan değer `3.5` olarak belirlenmiştir. |

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

 Exec görevini [kullanarak](../msbuild/exec-task.md)MSBuild.exe *aksine,* bu görev alt projeleri derlemek MSBuild aynı işlemden kullanır. Atlanabilir zaten yerleşik hedeflerin listesi, üst ve alt derlemeler arasında paylaşılır. Bu görev daha hızlıdır çünkü yeni bir MSBuild işlemi oluşturulmaz.

 Bu görev yalnızca proje dosyalarını değil, çözüm dosyalarını da işleyebilirsiniz.

 MSBuild tarafından projelerin aynı anda derlemeye olanak sağlamak için gerekli olan tüm yapılandırmalar, yapılandırma uzak altyapı (örneğin, bağlantı noktaları, protokoller, zaman aşımı, yeniden denemeler vb.) içeriyor olsa bile, yapılandırma dosyası kullanılarak yapılandırılabilir hale gel gerekir. Mümkün olduğunda, yapılandırma öğelerinin görev parametresi olarak belirtilebilir `MSBuild` olması gerekir.

 3 MSBuild 3.5'te çözüm projeleri artık tüm alt projelerden TargetOutputs'ları ortaya çıkarıyor.

## <a name="pass-properties-to-projects"></a>Özellikleri projelere iletir

 MSBuild 3.5'MSBuild önceki sürümlerinde, farklı özellik kümelerinin, MSBuild öğesinde listelenen farklı projelere geçirmesi zorlayıcıydı. [MSBuild](../msbuild/msbuild-task.md)görevinin Properties özniteliğini kullandıysanız, bu ayar, [MSBuild](../msbuild/msbuild-task.md) görevini toplu olarak toplu olarak düzenlemedikçe ve öğe listesinde her proje için koşullu olarak farklı özellikler sağladığınız sürece, bu ayar, yapılandıran tüm projelere uygulanmıştır.

 MSBuild 3.5'te ise özellikler ve AdditionalProperties olmak üzere iki yeni ayrılmış meta veri MSBuild sağlar. Bu özellik, yeni görevi kullanılarak farklı projeler için farklı özellikler [MSBuild sağlar.](../msbuild/msbuild-task.md)

> [!NOTE]
> Bu yeni meta veri öğeleri yalnızca MSBuild görevinin Projects [özniteliğinde geçirilen öğeler için geçerlidir.](../msbuild/msbuild-task.md)

## <a name="multi-processor-build-benefits"></a>Çok işlemcili derleme avantajları

 Bu yeni meta verileri kullanmanın başlıca avantajlarından biri, projelerinizi çok işlemcili bir sistemde paralel olarak derlemeniz sırasında ortaya çıkar. Meta veriler, herhangi bir toplu işlem veya koşullu görev [MSBuild](../msbuild/msbuild-task.md) gerek kalmadan tüm projeleri tek bir görev çağrısında MSBuild sağlar. Yalnızca tek bir MSBuild [çağırsanız,](../msbuild/msbuild-task.md)Projeler özniteliğinde listelenen tüm projeler paralel olarak yerleşik olur. (Ancak, özniteliği MSBuild `BuildInParallel=true` [görevdir.)](../msbuild/msbuild-task.md) Daha fazla bilgi için [bkz. Paralel olarak birden çok proje derleme.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="properties-metadata"></a>Özellikler meta verileri

 Belirtilen, Özellikler meta verileri görevin Properties parametresini geçersiz kılarken [AdditionalProperties](#additionalproperties-metadata) meta verileri parametrenin tanımlarına eklenir.

 Yaygın senaryolardan biri, yalnızca farklı derleme [](../msbuild/msbuild-task.md)yapılandırmaları kullanarak MSBuild çözüm dosyası derlemektir. Sürüm yapılandırmasını kullanarak Hata Ayıklama yapılandırmasını ve çözüm a2'nini kullanarak a1 çözümünü oluşturmak istiyor olabilirsiniz. Bu MSBuild 2.0'da bu proje dosyası aşağıdaki gibi olabilir:

> [!NOTE]
> Aşağıdaki örnekte , "..." ek çözüm dosyalarını temsil eder.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Ancak Özellikler meta verilerini kullanarak, aşağıdaki gibi tek bir MSBuild [görevi](../msbuild/msbuild-task.md)kullanmak için basitleştirebilirsiniz:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <Properties>Configuration=Debug</Properties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"/>
    </Target>
</Project>
```

 \- veya -

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln..."/>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Debug"/>
    </Target>
</Project>
```

## <a name="additionalproperties-metadata"></a>AdditionalProperties meta verileri

 Hem Yayın yapılandırmasını hem de x86 [mimarisini,](../msbuild/msbuild-task.md)diğerini ia64 mimarisini kullanarak MSBuild görevini kullanarak iki çözüm dosyası inşa ediyorsanız aşağıdaki senaryoyu göz önünde bulundurabilirsiniz. MSBuild 2.0'da, [MSBuild](../msbuild/msbuild-task.md)görevinin birden çok örneğini oluşturmanız gerekir: biri x86 Mimarisi ile Yayın yapılandırmasını, diğeri de ia64 mimarisiyle Sürüm yapılandırmasını kullanarak projeyi derlemek. Proje dosyanız aşağıdaki gibi olabilir:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;
          Architecture=x86"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;
          Architecture=ia64"/>
    </Target>
</Project>
```

 additionalproperties meta verilerini kullanarak, aşağıdakileri kullanarak tek bir [MSBuild görevi](../msbuild/msbuild-task.md) kullanmak için bunu basitleştirebilirsiniz:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <AdditionalProperties>Architecture=x86
              </AdditionalProperties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <AdditionalProperties>Architecture=ia64
              </AdditionalProperties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Release"/>
    </Target>
</Project>
```

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `MSBuild` öğe koleksiyonu tarafından belirtilen projeleri oluşturmak için görevini kullanır `ProjectReferences` . Elde edilen hedef çıktıları, `AssembliesBuiltByChildProjects` öğe koleksiyonunda depolanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ProjectReferences Include="*.*proj" />
    </ItemGroup>

    <Target Name="BuildOtherProjects">
        <MSBuild
            Projects="@(ProjectReferences)"
            Targets="Build">
            <Output
                TaskParameter="TargetOutputs"
                ItemName="AssembliesBuiltByChildProjects" />
        </MSBuild>
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
