---
title: ToolTaskExtension temel sınıfı | Microsoft Docs
description: Microsoft. Build. Tasks. ToolTaskExtension temel sınıfının, ondan devraldığı görevlere eklediği parametreler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4b0148a7c42b359906cd316b45dfdf2898e6313
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047832"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension temel sınıfı

Birçok görev, sınıfından devralan sınıfından devralan sınıfından devralır <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> <xref:Microsoft.Build.Utilities.Task> . Bu devralma zinciri, bunlardan türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda temel sınıfların parametreleri açıklanmaktadır.

| Parametre | Açıklama |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine> parametre.<br /><br /> Görevler için kullanılabilen derleme altyapısı arabirimini belirtir. Yapı altyapısı bu parametreyi otomatik olarak ayarlar ve görevlere geri çağrı yapmasına izin verir. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine2> parametre.<br /><br /> Görevler için kullanılabilen derleme altyapısı arabirimini belirtir. Yapı altyapısı bu parametreyi otomatik olarak ayarlar ve görevlere geri çağrı yapmasına izin verir.<br /><br /> Bu bir kullanışlı özelliktir. bu sınıftan devralan görev yazarlarının değeri ' dan ' a dönüştürmek zorunda değildir `IBuildEngine` `IBuildEngine2` . |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine3> parametre.<br /><br /> Konak tarafından belirtilen derleme altyapısı arabirimini belirtir. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | İsteğe bağlı `bool` parametre.<br /><br /> Olarak ayarlandığında `true` , bu görev **/q** komutunu komut satırı stdout 'a kopyalanmaması için *cmd.exe* komut satırına geçirir. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | İsteğe bağlı `String` dizi parametresi.<br /><br /> Ortam değişkenlerinin çiftler dizisi, eşittir işaretleriyle ayrılmıştır. Bu değişkenler, normal ortam bloğunu seçerek veya seçmeli olarak geçersiz kılmanın yanı sıra oluşturulan yürütülebilir dosyaya geçirilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | İsteğe bağlı `Int32` Çıkış salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından belirtilen çıkış kodunu belirtir. Görev herhangi bir hata günlüğe açtıysa, ancak işlem 0 (başarılı) çıkış koduna sahipse bu,-1 ' e ayarlanır. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskHost> parametre.<br /><br /> Ana bilgisayar nesne örneğini belirtir (null olabilir). Konak IDE, bu görevle bir ana bilgisayar nesnesi ilişkilendirirse, derleme altyapısı bu özelliği ayarlar. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | İsteğe bağlı <xref:Microsoft.Build.Utilities.TaskLoggingHelper> salt okunurdur parametresi.<br /><br /> <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension>Görev günlüğü yöntemlerini içeren bir sınıfın örneğini alır. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Seçenek `bool` parametresi.<br /><br /> İse `true` , standart hata akışında alınan tüm iletiler hata olarak günlüğe kaydedilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | İsteğe bağlı `String` parametre.<br /><br /> Standart çıkış akışından metnin günlüğe kaydedileceği önem. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | İsteğe bağlı `String` parametre.<br /><br /> Standart çıkış akışından metnin günlüğe kaydedileceği önem. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Sanal isteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue` , zaman aşımı süresi olmadığını gösterir. Zaman aşımı süresi milisaniyedir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Sanal isteğe bağlı `string` parametre.<br /><br /> Projeler, bir ToolName 'yi geçersiz kılmak için bunu uygulayabilir. Görevler, ToolName 'yi korumak için bunu geçersiz kılabilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | İsteğe bağlı `string` parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı yüklediği konumu belirtir. Bu parametre belirtilmezse, görev MSBuild 'i çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | İsteğe bağlı `bool` parametre.<br /><br /> Olarak ayarlandığında `true` , bu görev komut satırı için bir toplu iş dosyası oluşturur ve komutu doğrudan yürütmek yerine komut işlemcisini kullanarak yürütür. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | İsteğe bağlı `bool` parametre.<br /><br /> Olarak ayarlandığında `true` , bu görev, görevi çalıştırıldığında düğümü verir. |

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
