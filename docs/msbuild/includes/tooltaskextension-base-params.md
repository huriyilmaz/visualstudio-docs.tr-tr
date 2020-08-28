---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 6fd0fc6fd4f2e54c0d15f649139b649797f8336f
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2020
ms.locfileid: "89042909"
---
### <a name="tooltaskextension-parameters"></a>ToolTaskExtension parametreleri

Bu görev, sınıfından devralan sınıfından devralan sınıfından devralır <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> <xref:Microsoft.Build.Utilities.Task> . Bu devralma zinciri, bunlardan türetilen görevlere birkaç parametre ekler.

Aşağıdaki tabloda temel sınıfların parametreleri açıklanmaktadır:

| Parametre | Açıklama |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | İsteğe bağlı `bool` parametre.<br /><br /> Olarak ayarlandığında `true` , bu görev **/q** komutunu komut satırı stdout 'a kopyalanmaması için *cmd.exe* komut satırına geçirir. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | İsteğe bağlı `String` dizi parametresi.<br /><br /> Noktalı virgülle ayrılmış ortam değişkeni tanımlarının dizisi. Her tanım bir ortam değişkeni adı ve eşittir işaretiyle ayrılmış bir değer belirtmelidir. Bu değişkenler, normal ortam bloğunu seçerek veya seçmeli olarak geçersiz kılmanın yanı sıra oluşturulan yürütülebilir dosyaya geçirilir. Örneğin, `Variable1=Value1;Variable2=Value2`. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | İsteğe bağlı `Int32` Çıkış salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından belirtilen çıkış kodunu belirtir. Görev herhangi bir hata günlüğe açtıysa, ancak işlem 0 (başarılı) çıkış koduna sahipse bu,-1 ' e ayarlanır. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Seçenek `bool` parametresi.<br /><br /> İse `true` , standart hata akışında alınan tüm iletiler hata olarak günlüğe kaydedilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | İsteğe bağlı `bool` parametre.<br /><br /> İse `true` , standart hata akışında alınan tüm iletiler hata olarak günlüğe kaydedilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | İsteğe bağlı `String` parametre.<br /><br /> Standart çıkış akışından metnin günlüğe kaydedileceği önem. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | İsteğe bağlı `String` parametre.<br /><br /> Standart çıkış akışından metnin günlüğe kaydedileceği önem. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue` , zaman aşımı süresi olmadığını gösterir. Zaman aşımı süresi milisaniyedir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | İsteğe bağlı `string` parametre.<br /><br /> Projeler, bir ToolName 'yi geçersiz kılmak için bunu uygulayabilir. Görevler, ToolName 'yi korumak için bunu geçersiz kılabilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | İsteğe bağlı `string` parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı yüklediği konumu belirtir. Bu parametre belirtilmezse, görev MSBuild 'i çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | İsteğe bağlı `bool` parametre.<br /><br /> Olarak ayarlandığında `true` , bu görev komut satırı için bir toplu iş dosyası oluşturur ve komutu doğrudan yürütmek yerine komut işlemcisini kullanarak yürütür. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | İsteğe bağlı `bool` parametre.<br /><br /> Olarak ayarlandığında `true` , bu görev, görevi çalıştırıldığında düğümü verir. |
