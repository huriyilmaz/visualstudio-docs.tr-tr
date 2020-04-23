---
title: MSBuild Görevi | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab54c5c523c833be60ef4b5d5088b6217a3111a5
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072586"
---
# <a name="msbuild-task"></a>MSBuild görevi

Başka bir MSBuild projesinden MSBuild projeleri oluşturur.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `MSBuild` açıklanmaktadır.

| Parametre | Açıklama |
|-----------------------------------| - |
| `BuildInParallel` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Eğer , `Projects` parametrede belirtilen projeler mümkünse paralel olarak inşa edilirse. `false` varsayılan değerdir. |
| `Projects` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturmak için proje dosyalarını belirtir. |
| `Properties` | İsteğe bağlı `String` parametre.<br /><br /> Alt projeye genel özellik olarak uygulanacak özellik adı/değer çiftleri yarı sütunlu sınırlı bir liste. Bu parametreyi belirttiğiniz zaman, [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md)ile oluşturduğunuzda **özellik** anahtarıolan özellikleri ayarlamaya işlevsel olarak eşdeğerdir. Örneğin:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Özellikleri `Properties` parametre üzerinden projeye geçtiğinde, MSBuild proje dosyası zaten yüklenmiş olsa bile projenin yeni bir örneğini oluşturabilir. MSBuild, belirli bir proje yolu ve benzersiz bir genel özellik kümesi için tek bir proje örneği oluşturur. Örneğin, bu davranış, configuration=Release ile *myproject.proj*adını veren birden çok MSBuild görevi oluşturmanıza olanak tanır ve *myproject.proj'un* tek bir örneğini alırsınız (görevde benzersiz özellikler belirtilmemişse). MSBuild tarafından henüz görülmemiş bir özellik belirtirseniz, MSBuild projenin diğer örneklerine paralel olarak oluşturulabilen yeni bir proje örneği oluşturur. Örneğin, Bir Sürüm yapılandırması hata ayıklama yapılandırması ile aynı anda inşa edilebilir.|
| `RebaseOutputs` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Yapılan projelerdeki hedef çıktı öğelerinin göreli yolları çağrı projesine göre ayarlanmışsa. `false` varsayılan değerdir. |
| `RemoveProperties` | İsteğe bağlı `String` parametre.<br /><br /> Kaldırılacak genel özellikler kümesini belirtir. |
| `RunEachTargetSeparately` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`MSBuild görevi, listedeki her hedefi aynı anda yerine teker teker MSBuild'e geçerse çağırırsa. Daha önce çağrılan `true` hedefler başarısız olsa bile sonraki hedeflerin çağrılmasını garanti etmek için bu parametreyi ayarlama. Aksi takdirde, bir yapı hatası sonraki tüm hedeflerin çağrılmasını durdurur. `false` varsayılan değerdir. |
| `SkipNonexistentProjects` | İsteğe bağlı `Boolean` parametre.<br /><br /> Diskte `true`bulunmayan proje dosyaları atlanırsa. Aksi takdirde, bu tür projeler bir hataya neden olur. |
|`SkipNonexistentTargets`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa, `true`proje dosyaları var ama adlı `Targets` içermeyen atlanır. Aksi takdirde, bu tür projeler bir hataya neden olur. MSBuild 15.5 ile tanıtıldı.|
| `StopOnFirstFailure` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Projelerden biri oluşturulamazsa, başka proje oluşturulmayacak. Şu anda bu paralel (birden çok işlemci ile) bina desteklenmez. |
| `TargetAndPropertyListSeparators` | İsteğe bağlı `String[]` parametre.<br /><br /> Hedef ve özelliklerin listesini madde `Project` meta verileri olarak belirtir). Ayırıcılar işleme girmeden önce kaçmış olacak. örneğin%3B (kaçan bir ';') kaçak olmayan bir ';'miş gibi muamele göreceksiniz. |
| `TargetOutputs` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> Tüm proje dosyalarından oluşturulan hedeflerin çıktılarını verir. Yalnızca belirtilen hedeflerin çıktıları döndürülür, bu hedeflerin bağlı olduğu hedeflerde var olabilecek çıktılar değil.<br /><br /> `TargetOutputs` Parametre aynı zamanda aşağıdaki meta verileri de içerir:<br /><br /> -   `MSBuildSourceProjectFile`: Çıktıları ayarlayan hedefi içeren MSBuild proje dosyası.<br />-   `MSBuildSourceTargetName`: Çıktıları belirleyen hedef. **Not:**  Her proje dosyasıveya hedefteki çıktıları ayrı ayrı tanımlamak `MSBuild` istiyorsanız, görevi her proje dosyası veya hedef için ayrı ayrı çalıştırın. Tüm proje `MSBuild` dosyalarını oluşturmak için görevi yalnızca bir kez çalıştırıyorsanız, tüm hedeflerin çıktıları tek bir dizide toplanır. |
| `Targets` | İsteğe bağlı `String` parametre.<br /><br /> Proje dosyalarında oluşturmak için hedef veya hedefleri belirtir. Hedef adların listesini ayırmak için bir yarı nokta kullanın. `MSBuild` Görevde hedef belirtilmemişse, proje dosyalarında belirtilen varsayılan hedefler oluşturulur. **Not:**  Hedefler tüm proje dosyalarında oluşmalıdır. Yoksa, bir yapı hatası oluşur. |
| `ToolsVersion` | İsteğe bağlı `String` parametre.<br /><br /> Bu göreve `ToolsVersion` geçilen proje ler kullanılırken kullanılacakları belirtir.<br /><br /> .NET Framework'ün projede belirtilenden farklı bir sürümünü hedefleyen bir proje oluşturmak için bir MSBuild görevinin oluşturulmasını sağlar. Geçerli değerler `2.0` `3.0` ve `3.5`. Varsayılan değer. `3.5` |

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

 *MSBuild.exe*başlatmak için [Exec görevi](../msbuild/exec-task.md) kullanarak aksine, bu görev alt projeler oluşturmak için aynı MSBuild işlemini kullanır. Atlanabilecek zaten oluşturulmuş hedeflerin listesi üst ve alt yapılar arasında paylaşılır. Yeni MSBuild işlemi oluşturulmadı, çünkü bu görev de daha hızlıdır.

 Bu görev yalnızca proje dosyalarını değil, çözüm dosyalarını da işleyebilir.

 Yapılandırma uzak altyapı (örneğin, bağlantı noktaları, protokoller, zaman ekinleri, yeniden denemeler vb.) içerse bile, msbuild tarafından projelerin aynı anda oluşturulmasını sağlamak için gereken tüm yapılandırmalar, bir yapılandırma dosyası kullanılarak yapılandırılabilir hale getirilmelidir. Mümkün olduğunda, yapılandırma öğeleri `MSBuild` görevdeki görev parametreleri olarak belirtilmelidir.

 MSBuild 3.5'ten başlayarak, Çözüm projeleri artık oluşturduğu tüm alt projelerden TargetOutputs'ı yüzeye çıkar.

## <a name="pass-properties-to-projects"></a>Özellikleri projelere aktarma

 MSBuild 3.5'ten önceki MSBuild sürümlerinde, MSBuild öğesinde listelenen farklı projelere farklı özellik kümelerini aktarmak zordu. [MSBuild görevinin](../msbuild/msbuild-task.md)Özellikler özniteliğini kullandıysanız, [MSBuild görevini](../msbuild/msbuild-task.md) toplu olarak oluşturmadığınız ve madde listesindeki her proje için koşullu olarak farklı özellikler sağlamadığınız sürece, ayarı yapılan tüm projelere uygulanmıştır.

 Ancak MSBuild 3.5, [MSBuild görevi](../msbuild/msbuild-task.md)kullanılarak oluşturulmuş farklı projeler için farklı özellikleri geçirmeniz için esnek bir yol sağlayan iki yeni ayrılmış meta veri öğesi, Özellikler ve Ek Özellikler sağlar.

> [!NOTE]
> Bu yeni meta veri öğeleri yalnızca [MSBuild görevinin](../msbuild/msbuild-task.md)Projeler özniteliğinde geçirilen öğeler için geçerlidir.

## <a name="multi-processor-build-benefits"></a>Çok işlemcili yapı avantajları

 Bu yeni meta verileri kullanmanın en önemli avantajlarından biri, projelerinizi çok işlemcili bir sistemde paralel olarak oluşturduğunuzda oluşur. Meta veriler, herhangi bir toplu iş veya koşullu MSBuild görevlerini gerçekleştirmek zorunda kalmadan tüm projeleri tek bir [MSBuild görev](../msbuild/msbuild-task.md) çağrısında birleştirmenize olanak tanır. Yalnızca tek bir [MSBuild görevi](../msbuild/msbuild-task.md)çağırdığınızda, Projeler özniteliğinde listelenen tüm projeler paralel olarak oluşturulur. (Ancak, `BuildInParallel=true` öznitelik [MSBuild görevinde](../msbuild/msbuild-task.md)mevcutsa .) Daha fazla bilgi için [bkz.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="properties-metadata"></a>Özellikler meta veri

 Belirtildiğinde, Özellikler meta verileri görevin Özellikler parametresini geçersiz kılarken, [Ek Özellikler](#additionalproperties-metadata) meta verileri parametrenin tanımlarına eklenir.

 Yaygın bir senaryo, yalnızca farklı yapı yapılandırmaları kullanarak [MSBuild görevini](../msbuild/msbuild-task.md)kullanarak birden çok çözüm dosyası oluştururken olur. Sürüm yapılandırmasını kullanarak Hata Ayıklama yapılandırmasını ve çözüm a2'yi kullanarak çözüm a1 oluşturmak isteyebilirsiniz. MSBuild 2.0'da, bu proje dosyası aşağıdaki gibi görünür:

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

 Ancak Özellikler meta verilerini kullanarak, aşağıdakilerde gösterildiği gibi tek bir [MSBuild görevi](../msbuild/msbuild-task.md)kullanmak için bunu basitleştirebilirsiniz:

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

 \-veya -

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

## <a name="additionalproperties-metadata"></a>EkÖzellikler meta verileri

 [MSBuild görevini](../msbuild/msbuild-task.md)kullanarak iki çözüm dosyası oluşturduğunuz, hem Release yapılandırmasını kullanarak, hem de biri x86 mimarisini, diğeri ia64 mimarisini kullanarak aşağıdaki senaryoyu düşünün. MSBuild 2.0'da, [MSBuild görevinin](../msbuild/msbuild-task.md)birden çok örneğini oluşturmanız gerekir: biri x86 Mimarisi ile Sürüm yapılandırmasını kullanarak projeyi oluşturmak için, diğeri ise ia64 mimarisiyle Release yapılandırmasını kullanarak. Proje dosyanız aşağıdaki gibi görünür:

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

 AdditionalProperties meta verilerini kullanarak, aşağıdakileri kullanarak tek bir [MSBuild görevini](../msbuild/msbuild-task.md) kullanmak için bunu basitleştirebilirsiniz:

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

 Aşağıdaki örnek, `MSBuild` `ProjectReferences` madde koleksiyonu tarafından belirtilen projeleri oluşturmak için görevi kullanır. Elde edilen hedef çıktılar madde koleksiyonunda `AssembliesBuiltByChildProjects` depolanır.

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
