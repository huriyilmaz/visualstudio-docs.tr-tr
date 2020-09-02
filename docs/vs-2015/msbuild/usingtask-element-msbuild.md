---
title: UsingTask öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf2882120f2e4c27e33b105585ba56261122055d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815407"
---
# <a name="usingtask-element-msbuild"></a>UsingTask Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir [görev](../msbuild/task-element-msbuild.md) öğesinde başvurulan görevi, görev uygulamasını içeren derlemeye eşler.  
  
 \<Project>  
 \<UsingTask>  
  
## <a name="syntax"></a>Syntax  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`AssemblyName`|`AssemblyName`Özniteliği ya da `AssemblyFile` özniteliği gereklidir.<br /><br /> Yüklenecek derlemenin adı. Öznitelik, güçlü `AssemblyName` adlandırılmış derlemeleri kabul eder, ancak güçlü adlandırma gerekli değildir. Bu özniteliğin kullanılması, .NET 'teki yöntemi kullanılarak bir derlemeyi yüklemeye eşdeğerdir <xref:System.Reflection.Assembly.Load%2A> .<br /><br /> Özniteliği kullanılırsa bu özniteliği kullanamazsınız `AssemblyFile` .|  
|`AssemblyFile`|Ya da `AssemblyName` `AssemblyFile` özniteliği gereklidir.<br /><br /> Derlemenin dosya yolu. Bu öznitelik, tam yolları veya göreli yolları kabul eder. Göreli yollar, öğenin bildirildiği proje dosyasının veya hedef dosyanın dizinine göre belirlenir `UsingTask` . Bu özniteliğin kullanılması, .NET 'teki yöntemi kullanılarak bir derlemeyi yüklemeye eşdeğerdir <xref:System.Reflection.Assembly.LoadFrom%2A> .<br /><br /> Özniteliği kullanılırsa bu özniteliği kullanamazsınız `AssemblyName` .|  
|`TaskFactory`|İsteğe bağlı öznitelik.<br /><br /> Derlemede, belirtilen adın örneklerini oluşturmaktan sorumlu sınıfı belirtir `Task` .  Kullanıcı, görev `TaskBody` fabrikasının görevi oluşturmak için aldığı ve kullandığı bir alt öğe olarak da belirtebilir. Öğesinin içeriği, `TaskBody` görev fabrikasına özeldir.|  
|`TaskName`|Gerekli öznitelik.<br /><br /> Bir derlemeden başvurulacak görevin adı. Belirsizlikleri mümkünse, bu öznitelik her zaman tam ad alanları belirtmelidir. Belirsizlikleri varsa, MSBuild rastgele bir eşleşme seçer ve bu beklenmedik sonuçlara neden olabilir.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Belirtilen tarafından oluşturulan görevde görüntülenen parametre kümesi `TaskFactory` .|  
|[Görev](../msbuild/task-element-msbuild.md)|`TaskFactory`Görevin bir örneğini oluşturmak için öğesine geçirilen veriler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Proje dosyasının gerekli kök öğesi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortam değişkenlerine, komut satırı özelliklerine ve proje düzeyi özelliklerine, `UsingTask` Proje dosyasında açıkça veya içeri aktarılan bir proje dosyası aracılığıyla görünürse, öğe içinde herhangi bir yerde başvurulabilir. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
> `UsingTask`Öğe, MSBuild altyapısına genel olarak kaydedilen. Tasks dosyalarından birinden geliyorsa proje düzeyi özellikleri anlamı yoktur. Proje düzeyi özellikleri MSBuild 'e Global değildir.  
  
 MSBuild 4,0 ' de, görevler kullanılarak. overridetask dosyaları yüklenebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `UsingTask` öğesinin bir özniteliğiyle nasıl kullanılacağını gösterir `AssemblyName` .  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `UsingTask` öğesinin bir özniteliğiyle nasıl kullanılacağını gösterir `AssemblyFile` .  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
