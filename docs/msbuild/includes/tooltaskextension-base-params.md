---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 38ac6925e98f4eb17b57d083c45977cb3f0f29ea
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167311"
---
### <a name="tooltaskextension-parameters"></a>ToolTaskExtension parametreleri

Bu görev <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> <xref:Microsoft.Build.Utilities.Task> , sınıfından devralan sınıfından devralan sınıfından devralır. Bu devralma zinciri, bunlardan türetilen görevlere birkaç parametre ekler.

Aşağıdaki tabloda temel sınıfların parametreleri açıklanmaktadır:

| Parametre | Açıklama |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | İsteğe `bool` bağlı parametre.<br /><br /> Olarak `true`ayarlandığında, bu görev **/q** komutunu komut satırı stdout 'a kopyalanmaması gibi *cmd. exe* komut satırına geçirir. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | İsteğe `String` bağlı dizi parametresi.<br /><br /> Ortam değişkenlerinin çiftler dizisi, eşittir işaretleriyle ayrılmıştır. Bu değişkenler, normal ortam bloğunu seçerek veya seçmeli olarak geçersiz kılmanın yanı sıra oluşturulan yürütülebilir dosyaya geçirilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | İsteğe `Int32` bağlı çıkış salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından belirtilen çıkış kodunu belirtir. Görev herhangi bir hata günlüğe açtıysa, ancak işlem 0 (başarılı) çıkış koduna sahipse bu,-1 ' e ayarlanır. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Seçenek `bool` parametresi.<br /><br /> İse `true`, standart hata akışında alınan tüm iletiler hata olarak günlüğe kaydedilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | İsteğe `bool` bağlı parametre.<br /><br /> İse `true`, standart hata akışında alınan tüm iletiler hata olarak günlüğe kaydedilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | İsteğe `String` bağlı parametre.<br /><br /> Standart çıkış akışından metnin günlüğe kaydedileceği önem. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | İsteğe `String` bağlı parametre.<br /><br /> Standart çıkış akışından metnin günlüğe kaydedileceği önem. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | İsteğe `Int32` bağlı parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue`, zaman aşımı süresi olmadığını gösterir. Zaman aşımı süresi milisaniyedir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | İsteğe `string` bağlı parametre.<br /><br /> Projeler, bir ToolName 'yi geçersiz kılmak için bunu uygulayabilir. Görevler, ToolName 'yi korumak için bunu geçersiz kılabilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | İsteğe `string` bağlı parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı yüklediği konumu belirtir. Bu parametre belirtilmezse, görev MSBuild 'i çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | İsteğe `bool` bağlı parametre.<br /><br /> Olarak `true`ayarlandığında, bu görev komut satırı için bir toplu iş dosyası oluşturur ve komutu doğrudan yürütmek yerine komut işlemcisini kullanarak yürütür. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | İsteğe `bool` bağlı parametre.<br /><br /> Olarak `true`ayarlandığında, bu görev, görevi çalıştırıldığında düğümü verir. |
