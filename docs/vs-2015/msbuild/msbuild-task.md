---
title: MSBuild görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2349c21d55c20bcb3bcd50ab96f383a9afcc00b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64826933"
---
# <a name="msbuild-task"></a>MSBuild Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Başka bir projeden projeler oluşturur [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `MSBuild` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`BuildInParallel`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , parametresinde belirtilen projeler `Projects` Mümkünse paralel olarak oluşturulur. `false` varsayılan değerdir.|  
|`Projects`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Oluşturulacak proje dosyalarını belirtir.|  
|`Properties`|İsteğe bağlı `String` parametre.<br /><br /> Alt projeye genel özellikler olarak uygulanacak Özellik adı/değer çiftleri için noktalı virgülle ayrılmış bir liste. Bu parametreyi belirttiğinizde, [MSBuild.exe](../msbuild/msbuild-command-line-reference.md)ile oluşturduğunuzda **/Property** anahtarına sahip özellikleri ayarlamaya işlevsel olarak eşdeğerdir. Örneğin:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Parametreleri parametre aracılığıyla projeye geçirdiğinizde `Properties` , [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyası zaten yüklenmiş olsa bile projenin yeni bir örneğini oluşturur. Projenin yeni bir örneği oluşturulduğunda, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] farklı genel özelliklerine sahip olan ve projenin diğer örnekleriyle paralel olarak oluşturulabilen farklı bir proje olarak değerlendirir. Örneğin, bir sürüm yapılandırması hata ayıklama yapılandırmasıyla aynı anda oluşturabilir.|  
|`RebaseOutputs`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` , derleme projelerinin hedef çıkış öğelerinin göreli yollarının, çağıran projeye göreli olarak ayarlanmış yolları vardır. `false` varsayılan değerdir.|  
|`RemoveProperties`|İsteğe bağlı `String` parametre.<br /><br /> Kaldırılacak genel özellikler kümesini belirtir.|  
|`RunEachTargetSeparately`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu durumda, `true` [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görev [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aynı anda değil, her bir hedefi aynı anda birer birer bir kez çağırır. Bu parametre, `true` daha önce çağrılan hedefler başarısız olsa bile sonraki hedeflerin çağrılmasını güvence altına almak için ayarlanıyor. Aksi takdirde, bir yapı hatası sonraki tüm hedeflerin çağrılmasını durdurur. `false` varsayılan değerdir.|  
|`SkipNonexistentProjects`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , diskte bulunmayan proje dosyaları atlanır. Aksi takdirde, bu tür projeler hataya neden olur.|  
|`StopOnFirstFailure`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Projelerden biri derlenmediğinde, daha fazla proje derlenmeyecektir. Şu anda paralel olarak (birden çok işlemciyle) oluşturulurken bu desteklenmez.|  
|`TargetAndPropertyListSeparators`|İsteğe bağlı `String[]` parametre.<br /><br /> Bir hedef ve Özellik listesini `Project` öğe meta verileri olarak belirtir). Ayırıcıların işlenmeden önce önüne atlanacaktır. örn .% 3B (kaçan '; '), kaçışsız bir '; ' gibi değerlendirilir.|  
|`TargetOutputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Tüm proje dosyalarından oluşturulan hedeflerin çıkışlarını döndürür. Yalnızca belirtilen hedeflerden gelen çıktılar döndürülür, bu hedeflerin bağımlı olduğu hedeflerde mevcut olabilecek hiçbir çıktı değildir.<br /><br /> `TargetOutputs`Parametresi aşağıdaki meta verileri de içerir:<br /><br /> -   `MSBuildSourceProjectFile`: [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Çıkışları belirten hedefi içeren proje dosyası.<br />-   `MSBuildSourceTargetName`: Çıkışları oluşturan hedef. **Note:**  Her bir proje dosyası veya hedefi için çıktıları ayrı ayrı tanımlamak istiyorsanız, `MSBuild` görevi her proje dosyası veya hedefi için ayrı olarak çalıştırın. `MSBuild`Tüm proje dosyalarını derlemek için görevi yalnızca bir kez çalıştırırsanız, tüm hedeflerin çıktıları tek bir dizide toplanır.|  
|`Targets`|İsteğe bağlı `String` parametre.<br /><br /> Proje dosyalarında oluşturulacak hedef veya hedefleri belirtir. Bir hedef adları listesini ayırmak için noktalı virgül kullanın. Görevde hiçbir hedef belirtilmemişse `MSBuild` , proje dosyalarında belirtilen varsayılan hedefler oluşturulur. **Note:**  Hedefler tüm proje dosyalarında gerçekleşmelidir. Aksi takdirde, bir derleme hatası oluşur.|  
|`ToolsVersion`|İsteğe bağlı `String` parametre.<br /><br /> `ToolsVersion`Bu göreve geçirilen projeleri oluştururken kullanılacak öğesini belirtir.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Görevin, projede belirtilenden farklı bir sürümünü hedefleyen bir proje oluşturmasını sağlar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Geçerli değerler `2.0` , ve ' dir `3.0` `3.5` . Varsayılan değer `3.5` .|  
|`UnloadProjectsOnCompletion`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , işlem tamamlandıktan sonra proje kaldırılır.|  
|`UseResultsCache`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , önbelleğe alınmış sonuç, varsa döndürülür. MSBuild görevi çalıştırıldığında, sonucu bir kapsamda önbelleğe alınır (ProjectFileName, GlobalProperties) [TargetNames]<br /><br /> yapı öğelerinin listesi olarak|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
 MSBuild.exe başlatmak için [Exec görevi](../msbuild/exec-task.md) kullanmaktan farklı olarak, bu görev [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] alt projeleri oluşturmak için aynı işlemi kullanır. Atlanmak üzere önceden oluşturulmuş hedeflerin listesi, üst ve alt derlemeler arasında paylaşılır. Yeni bir işlem oluşturulmadığından bu görev da daha hızlıdır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
 Bu görev yalnızca proje dosyalarını değil, çözüm dosyalarını da işleyebilir.  
  
 Bir yapılandırma, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] uzak altyapıyı (örneğin, bağlantı noktaları, protokoller, zaman aşımları, yeniden denemeler vb.) içerse bile, projelerin aynı anda oluşturulmasını sağlamak için gereken tüm yapılandırmalar, bir yapılandırma dosyası kullanılarak yapılandırılabilir hale getirilmelidir. Mümkün olduğunda yapılandırma öğelerinin görevde görev parametreleri olarak belirtibilmeleri gerekir `MSBuild` .  
  
 3,5 ' den başlayarak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , çözüm projeleri artık oluşturduğu tüm alt projelerdeki Targetoutkoyar.  
  
## <a name="passing-properties-to-projects"></a>Projelere Özellikleri Geçirme  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]3,5 ' den önceki sürümlerinde [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , farklı özellik kümelerini öğede listelenen farklı projelere geçirme [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zor oldu. [MSBuild görevinin](../msbuild/msbuild-task.md)Properties özniteliğini kullandıysanız, bu ayar, [MSBuild görevini](../msbuild/msbuild-task.md) toplu olarak ve öğe listesindeki her proje için koşullu olarak farklı özellikler sağladıkça oluşturulan tüm projelere uygulandı.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Ancak, [MSBuild görevi](../msbuild/msbuild-task.md)kullanılarak oluşturulan farklı projelere yönelik farklı özellikleri geçirmek için esnek bir yol sağlayan iki yeni ayrılmış meta veri öğesi, özellik ve additionalproperties sağlar. 3,5  
  
> [!NOTE]
> Bu yeni meta veri öğeleri yalnızca [MSBuild görevinin](../msbuild/msbuild-task.md)Projects özniteliğinde geçirilen öğeler için geçerlidir.  
  
## <a name="multi-processor-build-benefits"></a>Birden Çok İşlemcili Derlemenin Avantajları  
 Bu yeni meta verileri kullanmanın önemli avantajlarından biri, projelerinizi çok işlemcili bir sistemde paralel olarak oluşturduğunuzda oluşur. Meta veriler, tüm projeleri toplu işlem veya koşullu görevler gerçekleştirmek zorunda kalmadan tek bir [MSBuild görev](../msbuild/msbuild-task.md) çağrısında birleştirmenize olanak tanır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Yalnızca tek bir [MSBuild görevini](../msbuild/msbuild-task.md)çağırdığınızda, projeler özniteliğinde listelenen tüm projeler paralel olarak oluşturulur. (Ancak, `BuildInParallel=true` özniteliği [MSBuild görevinde](../msbuild/msbuild-task.md)varsa.) Daha fazla bilgi için bkz. [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="properties-metadata"></a>Özellikler Meta Verisi  
 Yaygın bir senaryo, [MSBuild görevini](../msbuild/msbuild-task.md)kullanarak yalnızca farklı derleme yapılandırması kullanarak birden çok çözüm dosyası derlerken olur. Hata ayıklama yapılandırması ve, sürüm yapılandırması kullanılarak a2 çözümünü kullanarak a1 çözümü oluşturmak isteyebilirsiniz. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]2,0 ' de, bu proje dosyası aşağıdaki gibi görünür:  
  
> [!NOTE]
> Aşağıdaki örnekte, "..." ek çözüm dosyalarını temsil eder.  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Ancak, Özellikler meta verilerini kullanarak, aşağıdaki şekilde gösterildiği gibi tek bir [MSBuild görevi](../msbuild/msbuild-task.md)kullanmak için bunu basitleştirebilirsiniz:  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
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
  
 \- veya  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
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
  
## <a name="additionalproperties-metadata"></a>AdditionalProperties Meta Verisi  
 Hem sürüm yapılandırması hem de x86 mimarisini ve diğerini ia64 mimarisini kullanarak bir [MSBuild görevini](../msbuild/msbuild-task.md)kullanarak iki çözüm dosyası oluşturduğunuz aşağıdaki senaryoyu göz önünde bulundurun. 2,0 ' de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , bir tane Için [MSBuild görevinin](../msbuild/msbuild-task.md)birden çok örneğini oluşturmanız gerekir: bir tane, sürüm yapılandırmasını kullanarak x86 mimarisiyle, diğeri de IA64 mimarisine sahip olan yayın yapılandırmasını kullanarak projeyi oluşturmak için. Proje dosyanız şu şekilde görünür:  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 AdditionalProperties meta verilerini kullanarak, aşağıdakileri kullanarak tek bir [MSBuild görevi](../msbuild/msbuild-task.md) kullanmak için bunu basitleştirebilirsiniz:  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
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
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
