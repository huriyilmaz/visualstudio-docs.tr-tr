---
title: Task öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6683aac3c5a4314df6fde3d72dd9085b6608d8a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202262"
---
# <a name="task-element-msbuild"></a>Görev Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir görevin örneğini oluşturur ve yürütür [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Öğe adı, oluşturulmakta olan görevin adına göre belirlenir.  
  
 \<Project>  
 \<Target>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı öznitelik. Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|İsteğe bağlı öznitelik. , Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir.<br />-   **Errportadcontinue**. Bir görev başarısız olduğunda, öğedeki sonraki görevler `Target` ve derleme yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.<br />-   **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğe ve yapı içindeki kalan görevler `Target` yürütülmez ve tüm `Target` öğe ve derleme başarısız olarak kabul edilir.<br /><br /> 4,5 ' den önceki .NET Framework sürümleri yalnızca `true` ve değerlerini destekliyordu `false` .<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Görev sınıfı, özniteliğiyle etiketlenmiş bir veya daha fazla özellik içeriyorsa gereklidir `[Required]` .<br /><br /> Değer olarak parametre değerini içeren Kullanıcı tanımlı bir görev parametresi. `Task`Her öznitelik, görev sınıfındaki bir .NET özelliği ile eşlenmesiyle, öğesinde herhangi bir sayıda parametre olabilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Çıktı](../msbuild/output-element-msbuild.md)|Projedeki çıkışları proje dosyasında depolar. Bir görevde sıfır veya daha fazla `Output` öğe olabilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Hedef](../msbuild/target-element-msbuild.md)|Görevler için kapsayıcı öğesi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="remarks"></a>Açıklamalar  
 `Task`Proje dosyasındaki bir öğe bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görevin örneğini oluşturur, üzerinde özellikleri ayarlar ve yürütür. `Output`Öğesi, proje dosyasında başka bir yerde kullanılacak olan özellikler veya öğelerde çıkış parametrelerini depolar.  
  
 Görevin üst öğesinde herhangi [bir](../msbuild/onerror-element-msbuild.md) IO öğesi varsa `Target` , görev başarısız olursa ve değeri varsa bunlar yine de değerlendirilir `ContinueOnError` `false` . Görevler hakkında daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, [Csc görev](../msbuild/csc-task.md) sınıfının bir örneğini oluşturur, özelliklerin altıyı ayarlar ve görevi yürütür. Yürütmeden sonra, `OutputAssembly` nesnesinin özelliğinin değeri adlı bir öğe listesine yerleştirilir `FinalAssemblyName` .  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
