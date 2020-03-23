---
title: ToolTaskExtension Taban Sınıfı | Microsoft Dokümanlar
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
ms.openlocfilehash: 9aa052a0fd2216d5f3d85e99794d9ac883a09e2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631698"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension taban sınıfı

Birçok görev, <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıftan devralınan <xref:Microsoft.Build.Utilities.ToolTask> ve kendisi <xref:Microsoft.Build.Utilities.Task> sınıftan devralan sınıftan devralır. Bu devralma zinciri, bunlardan türeyen görevlere çeşitli parametreler ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda temel sınıfların parametreleri açıklanmaktadır.

| Parametre | Açıklama |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine> parametre.<br /><br /> Görevlerin kullanabileceği yapı altyapısı arabirimini belirtir. Yapı motoru, görevlerin geri çağrılmasını sağlamak için bu parametreyi otomatik olarak ayarlar. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine2> parametre.<br /><br /> Görevlerin kullanabileceği yapı altyapısı arabirimini belirtir. Yapı motoru, görevlerin geri çağrılmasını sağlamak için bu parametreyi otomatik olarak ayarlar.<br /><br /> Bu, bu sınıftan devralan görev yazarlarının değeri 'den ' `IBuildEngine` `IBuildEngine2`e ' ye dökmek zorunda kalmaması için bir kolaylık özelliğidir. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | İsteğe bağlı <xref:Microsoft.Build.Framework.IBuildEngine3> parametre.<br /><br /> Ana bilgisayar tarafından sağlanan yapı motoru arabirimini belirtir. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | İsteğe bağlı `bool` parametre.<br /><br /> Ayarlandığında `true`, bu görev *cmd.exe* komut satırına **/Q** geçer, böylece komut satırı stdout kopyalanmaz. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | İsteğe bağlı `String` dizi parametresi.<br /><br /> Eşit işaretlerle ayrılmış ortam değişkenleri dizilimi. Bu değişkenler, normal ortam bloğuna ek olarak veya seçici olarak geçersiz kılınan yürütülebilir çalıştırılabilir e aktarılır. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | İsteğe bağlı `Int32` çıktı salt okunur parametresi.<br /><br /> Çalıştırılan komut tarafından sağlanan çıkış kodunu belirtir. Görev herhangi bir hata günlüğe kaydetmişse, ancak işlem 0 (başarı) çıkış koduna sahipse, bu -1 olarak ayarlanır. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskHost> parametre.<br /><br /> Ana bilgisayar nesnesi örneğini belirtir (null olabilir). Ana bilgisayar IDE bu özel görevle bir ana bilgisayar nesnesi ilişkilendirmişse yapı altyapısı bu özelliği ayarlar. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | İsteğe bağlı <xref:Microsoft.Build.Utilities.TaskLoggingHelper> salt okunur parametresi.<br /><br /> Görev günlüğe <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> kaydetme yöntemlerini içeren bir sınıfın örneğini alır. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Seçenek `bool` parametresi.<br /><br /> Standart `true`hata akışında alınan tüm iletiler hata olarak günlüğe kaydedilirse. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | İsteğe bağlı `String` parametre.<br /><br /> Standart akıştan metin günlüğe kaydetmenin önemi. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | İsteğe bağlı `String` parametre.<br /><br /> Standart akıştan metin günlüğe kaydetmenin önemi. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Sanal `Int32` isteğe bağlı parametre.<br /><br /> Görev yürütülebilir sonlandırıldıktan sonra milisaniye cinsinden süreyi belirtir. Varsayılan `Int.MaxValue`değer, zaman dışında bir dönem olmadığını gösterir. Zaman-zaman milisaniye cinsinden. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Sanal `string` isteğe bağlı parametre.<br /><br /> Projeler, bir Araç Adı geçersiz kılmak için bunu uygulayabilir. Görevler, Araç Adını korumak için bunu geçersiz kılabilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | İsteğe bağlı `string` parametre.<br /><br /> Görevin temel yürütülebilir dosyayı yüklendiği konumu belirtir. Bu parametre belirtilmemişse, görev MSBuild çalıştıran çerçevenin sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | İsteğe bağlı `bool` parametre.<br /><br /> `true`Ayarlandığında, bu görev komut satırı için bir toplu iş dosyası oluşturur ve komutu doğrudan yürütmek yerine komut işlemcisini kullanarak çalıştırır. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | İsteğe bağlı `bool` parametre.<br /><br /> `true`Ayarlandığında, bu görev, görevi yürütüldüğünde düğümü verir. |

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
