---
title: MSBuild görevi | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d0b2b0c4cee2a372bccb8ad461ed195fc5519d7
ms.sourcegitcommit: 0554b59a2a251661e56824fb9cd6e9b1f326cef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71831862"
---
# <a name="msbuild-task"></a>MSBuild görevi

Başka bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projesinden [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projelerini oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, `MSBuild` görevin parametrelerini açıklar.

| Parametre | Açıklama |
|-----------------------------------| - |
| `BuildInParallel` | İsteğe `Boolean` bağlı parametre.<br /><br /> @No__t-0 ise, `Projects` parametresinde belirtilen projeler, mümkünse paralel olarak oluşturulur. `false` varsayılan değerdir. |
| `Projects` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulacak proje dosyalarını belirtir. |
| `Properties` | İsteğe `String` bağlı parametre.<br /><br /> Alt projeye genel özellikler olarak uygulanacak Özellik adı/değer çiftleri için noktalı virgülle ayrılmış bir liste. Bu parametreyi belirttiğinizde, [*MSBuild. exe*](../msbuild/msbuild-command-line-reference.md)ile oluşturduğunuzda **-Property** anahtarına sahip özellikleri ayarlamaya işlevsel olarak eşdeğerdir. Örneğin:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> @No__t-0 parametresi aracılığıyla projeye Özellikler geçirdiğinizde, proje dosyası zaten yüklenmiş olsa da, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projenin yeni bir örneğini oluşturabilir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], belirli bir proje yolu ve benzersiz bir genel özellikler kümesi için tek bir proje örneği oluşturur. Örneğin, bu davranış, Configuration = sürümü ile *MyProject. proj*' i çağıran birden çok MSBuild görevi oluşturmanıza olanak sağlar ve *MyProject. proj* ' in tek bir örneğini alırsınız (görevde benzersiz özellikler belirtilmemişse). Henüz [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tarafından görülmemiş bir özellik belirtirseniz, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projenin diğer örneklerine paralel olarak oluşturulan yeni bir örneğini oluşturur. Örneğin, bir sürüm yapılandırması hata ayıklama yapılandırması ile aynı anda derleyebilir.|
| `RebaseOutputs` | İsteğe `Boolean` bağlı parametre.<br /><br /> @No__t-0 ise, derleme projelerinin hedef çıkış öğelerinin göreli yolları çağıran projeye göreli olacak şekilde ayarlanır. `false` varsayılan değerdir. |
| `RemoveProperties` | İsteğe `String` bağlı parametre.<br /><br /> Kaldırılacak genel özellikler kümesini belirtir. |
| `RunEachTargetSeparately` | İsteğe `Boolean` bağlı parametre.<br /><br /> @No__t-0 ise, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevi aynı anda yerine [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 1 ' e aktarılan listedeki her hedefi çağırır. Bu parametrenin `true` olarak ayarlanması, daha önce çağrılan hedefler başarısız olsa bile sonraki hedeflerin çağrılmasını garanti eder. Aksi takdirde, bir yapı hatası sonraki tüm hedeflerin çağrılmasını durdurur. `false` varsayılan değerdir. |
| `SkipNonexistentProjects` | İsteğe `Boolean` bağlı parametre.<br /><br /> @No__t-0 ise, diskte bulunmayan proje dosyaları atlanır. Aksi takdirde, bu tür projeler hataya neden olur. |
| `StopOnFirstFailure` | İsteğe `Boolean` bağlı parametre.<br /><br /> @No__t-0 ise, projelerden biri derlenmediğinde daha fazla proje derlenmeyecektir. Şu anda paralel olarak (birden çok işlemciyle) oluşturulurken bu desteklenmez. |
| `TargetAndPropertyListSeparators` | İsteğe `String[]` bağlı parametre.<br /><br /> @No__t-0 öğe meta verileri olarak hedeflerin ve özelliklerin bir listesini belirtir. Ayırıcıların işlenmeden önce önüne atlanacaktır. örn.% 3B (kaçan '; '), kaçışsız bir '; ' gibi değerlendirilir. |
| `TargetOutputs` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> @ no__t-1 salt okunurdur çıkış parametresi.<br /><br /> Tüm proje dosyalarından oluşturulan hedeflerin çıkışlarını döndürür. Yalnızca belirtilen hedeflerden gelen çıktılar döndürülür, bu hedeflerin bağımlı olduğu hedeflerde mevcut olabilecek hiçbir çıktı değildir.<br /><br /> @No__t-0 parametresi aşağıdaki meta verileri de içerir:<br /><br /> -   `MSBuildSourceProjectFile`: Çıkışları belirten hedefi içeren [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası.<br />-   `MSBuildSourceTargetName`: Çıkışları ayarlama hedefi. **Not:**  Her bir proje dosyası veya hedefi için çıktıları ayrı ayrı tanımlamak istiyorsanız, her proje dosyası veya hedefi için `MSBuild` görevini ayrı olarak çalıştırın. Tüm proje dosyalarını derlemek için `MSBuild` görevini yalnızca bir kez çalıştırırsanız, tüm hedeflerin çıktıları tek bir dizide toplanır. |
| `Targets` | İsteğe `String` bağlı parametre.<br /><br /> Proje dosyalarında oluşturulacak hedef veya hedefleri belirtir. Bir hedef adları listesini ayırmak için noktalı virgül kullanın. @No__t-0 görevinde bir hedef belirtilmemişse, proje dosyalarında belirtilen varsayılan hedefler oluşturulur. **Not:**  Hedefler tüm proje dosyalarında gerçekleşmelidir. Aksi takdirde, bir derleme hatası oluşur. |
| `ToolsVersion` | İsteğe `String` bağlı parametre.<br /><br /> Bu göreve geçirilen projeler oluşturulurken kullanılacak `ToolsVersion` belirtir.<br /><br /> @No__t-0 görevinin, projede belirtilenden farklı bir .NET Framework sürümünü hedefleyen bir proje oluşturmasını sağlar. Geçerli değerler `2.0`, `3.0` ve `3.5` ' dir. Varsayılan değer `3.5`. |

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

 *MSBuild. exe*' yi başlatmak için [Exec görevini](../msbuild/exec-task.md) kullanmaktan farklı olarak, bu görev alt projeleri oluşturmak için aynı [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] işlemini kullanır. Atlanmak üzere önceden oluşturulmuş hedeflerin listesi, üst ve alt derlemeler arasında paylaşılır. Yeni [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] işlemi oluşturulmadığından bu görev da daha hızlıdır.

 Bu görev yalnızca proje dosyalarını değil, çözüm dosyalarını da işleyebilir.

 Projelerin aynı anda oluşturulmasını sağlamak için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tarafından gerekli olan herhangi bir yapılandırma, yapılandırma uzak altyapıyı (örneğin, bağlantı noktaları, protokoller, zaman aşımları, yeniden denemeler vb.) içerse de, bir yapılandırma dosyası. Mümkün olduğunda yapılandırma öğelerinin `MSBuild` görevinde görev parametreleri olarak belirtibilmeleri gerekir.

 @No__t-0 3,5 ' den başlayarak, çözüm projeleri artık oluşturduğu tüm alt projelerdeki Targetoutkoyar.

## <a name="pass-properties-to-projects"></a>Özellikleri projelere geçir

 @No__t-0 ' dan önceki [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 ' den önce, farklı özellik kümelerinin [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] öğesinde listelenen farklı projelere geçirilmesi zor oldu. [MSBuild görevinin](../msbuild/msbuild-task.md)Properties özniteliğini kullandıysanız, bu ayar, [MSBuild görevini](../msbuild/msbuild-task.md) toplu olarak ve öğe listesindeki her proje için koşullu olarak farklı özellikler sağladıkça oluşturulan tüm projelere uygulandı.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 ancak, [MSBuild görevi](../msbuild/msbuild-task.md)kullanılarak oluşturulan farklı projelere yönelik farklı özellikleri geçirmek için esnek bir yol sağlayan, iki yeni ayrılmış meta veri öğesi, özellik ve additionalproperties sağlar.

> [!NOTE]
> Bu yeni meta veri öğeleri yalnızca [MSBuild görevinin](../msbuild/msbuild-task.md)Projects özniteliğinde geçirilen öğeler için geçerlidir.

## <a name="multi-processor-build-benefits"></a>Çok işlemcili derleme avantajları

 Bu yeni meta verileri kullanmanın önemli avantajlarından biri, projelerinizi çok işlemcili bir sistemde paralel olarak oluşturduğunuzda oluşur. Meta veriler, tüm projeleri toplu işleme veya koşullu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevleri gerçekleştirmek zorunda kalmadan tek bir [MSBuild görev](../msbuild/msbuild-task.md) çağrısında birleştirmenize olanak tanır. Yalnızca tek bir [MSBuild görevini](../msbuild/msbuild-task.md)çağırdığınızda, projeler özniteliğinde listelenen tüm projeler paralel olarak oluşturulur. (Ancak, `BuildInParallel=true` özniteliği [MSBuild görevinde](../msbuild/msbuild-task.md)varsa.) Daha fazla bilgi için bkz. [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Özellikler meta verileri

 Belirtildiğinde, Özellikler meta verileri görevin Özellikler parametresini geçersiz kılar, ancak [Additionalproperties](#additionalproperties-metadata) meta verileri parametrenin tanımlarına eklenir.

 Yaygın bir senaryo, [MSBuild görevini](../msbuild/msbuild-task.md)kullanarak yalnızca farklı derleme yapılandırması kullanarak birden çok çözüm dosyası derlerken olur. Hata ayıklama yapılandırması ve, sürüm yapılandırması kullanılarak a2 çözümünü kullanarak a1 çözümü oluşturmak isteyebilirsiniz. @No__t-0 2,0 ' de, bu proje dosyası aşağıdaki gibi görünür:

> [!NOTE]
> Aşağıdaki örnekte, "..." ek çözüm dosyalarını temsil eder.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Ancak, Özellikler meta verilerini kullanarak, aşağıdaki şekilde gösterildiği gibi tek bir [MSBuild görevi](../msbuild/msbuild-task.md)kullanmak için bunu basitleştirebilirsiniz:

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

 Hem sürüm yapılandırması hem de x86 mimarisini ve diğerini ia64 mimarisini kullanarak bir [MSBuild görevini](../msbuild/msbuild-task.md)kullanarak iki çözüm dosyası oluşturduğunuz aşağıdaki senaryoyu göz önünde bulundurun. @No__t-0 2,0 ' de, [MSBuild görevinin](../msbuild/msbuild-task.md)birden çok örneğini oluşturmanız gerekir: bir tane, sürüm yapılandırmasını kullanarak x86 mimarisi ile sürüm yapılandırması kullanarak projeyi derlemek için, diğer bir deyişle, sürüm yapılandırmasını IA64 mimarisiyle kullanın. Proje dosyanız şu şekilde görünür:

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

 AdditionalProperties meta verilerini kullanarak, aşağıdakileri kullanarak tek bir [MSBuild görevi](../msbuild/msbuild-task.md) kullanmak için bunu basitleştirebilirsiniz:

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

 Aşağıdaki örnek, `ProjectReferences` öğe koleksiyonu tarafından belirtilen projeleri oluşturmak için `MSBuild` görevini kullanır. Elde edilen hedef çıktıları `AssembliesBuiltByChildProjects` öğe koleksiyonunda depolanır.

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
