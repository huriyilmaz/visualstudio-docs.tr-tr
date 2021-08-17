---
title: ToolTaskExtension Temel Sınıf | Microsoft Docs
description: Microsoft.Build.Tasks.ToolTaskExtension temel sınıfının bundan devralınan görevlere eklemiş olduğu parametreler hakkında bilgi edinebilirsiniz.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 19a0f89ca19776c32efdc5594aae170c251cde30c7fde7046bcd3e5fdd0893e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369741"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension temel sınıfı

Birçok görev sınıfından <xref:Microsoft.Build.Tasks.ToolTaskExtension> devralınır ve kendisi <xref:Microsoft.Build.Utilities.ToolTask> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu devralma zinciri, görevlerden türetilen görevlere birkaç parametre ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda temel sınıfların parametreleri açıkmektedir.

| Parametre | Açıklama |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | İsteğe <xref:Microsoft.Build.Framework.IBuildEngine> bağlı parametre.<br /><br /> Görevler için kullanılabilir derleme altyapısı arabirimini belirtir. Derleme altyapısı, görevlerin bu parametreye geri çağrılmalarına izin vermek için bu parametreyi otomatik olarak ayarlar. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | İsteğe <xref:Microsoft.Build.Framework.IBuildEngine2> bağlı parametre.<br /><br /> Görevler için kullanılabilir derleme altyapısı arabirimini belirtir. Derleme altyapısı, görevlerin bu parametreye geri çağrılmalarına izin vermek için bu parametreyi otomatik olarak ayarlar.<br /><br /> Bu özellik kolaylık sağlar, böylece bu sınıftan devralan görev yazarlarının değerinden değerine türe türetir. `IBuildEngine` `IBuildEngine2` |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | İsteğe <xref:Microsoft.Build.Framework.IBuildEngine3> bağlı parametre.<br /><br /> Konak tarafından sağlanan derleme altyapısı arabirimini belirtir. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | İsteğe `bool` bağlı parametre.<br /><br /> olarak `true` ayarlanırsa, bu görev **/Q'cmd.exe** komut satırına  iletir; böylece komut satırı stdout'a kopyalanmaz. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | İsteğe `String` bağlı dizi parametresi.<br /><br /> Ortam değişkenlerinin eşit işaretlerle ayrılmış çiftleri dizisi. Bu değişkenler, normal ortam bloğuna ek olarak veya seçmeli olarak geçersiz kılmanın yanı sıra, ortaya çıktı yürütülebilir dosyaya geçirildi. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | İsteğe `Int32` bağlı çıkış salt okunur parametresi.<br /><br /> Yürütülen komut tarafından sağlanan çıkış kodunu belirtir. Görev herhangi bir hata günlüğe kaydedse ama işlemde çıkış kodu 0 (başarılı) varsa, bu -1 olarak ayarlanır. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | İsteğe <xref:Microsoft.Build.Framework.ITaskHost> bağlı parametre.<br /><br /> Konak nesne örneğini belirtir (null olabilir). Konak IDE'nin bu belirli görevle bir konak nesnesi ilişkilendirilmişse, derleme altyapısı bu özelliği ayarlar. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | İsteğe <xref:Microsoft.Build.Utilities.TaskLoggingHelper> bağlı salt okunur parametre.<br /><br /> Görev günlüğü yöntemlerini <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> içeren bir sınıfın örneğini alır. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Seçenek `bool` parametresi.<br /><br /> ise, `true` standart hata akışında alınan tüm iletiler hata olarak kaydedilir. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | İsteğe `String` bağlı parametre.<br /><br /> Standart çıkış akışından metin günlüğe hangi önemle kaydedilir? |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | İsteğe `String` bağlı parametre.<br /><br /> Standart çıkış akışından metin günlüğe hangi önemle kaydedilir? |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Sanal isteğe bağlı `Int32` parametresi.<br /><br /> Görev yürütülebilir dosyasının sonlandırılma süresini milisaniye cinsinden belirtir. Varsayılan değer, `Int.MaxValue` zaman dışında nokta olmadığını gösteren değeridir. Zaman out milisaniye cinsindendir. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Sanal isteğe bağlı `string` parametresi.<br /><br /> Projeler bir ToolName'i geçersiz kılmak için bunu gerçekleştirebilirsiniz. Görevler ToolName'i korumak için bunu geçersiz kabilirsiniz. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | İsteğe `string` bağlı parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı yükleme konumunu belirtir. Bu parametre belirtilmezse, görev çalışan çerçevenin sürümüne karşılık gelen SDK yükleme yolunu MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | İsteğe `bool` bağlı parametre.<br /><br /> olarak ayarlanırsa, bu görev komut satırı için bir toplu iş dosyası oluşturur ve komutu doğrudan yürütmek yerine komut `true` işlemcisini kullanarak yürütür. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | İsteğe `bool` bağlı parametre.<br /><br /> olarak `true` ayarlanırsa, bu görev görevi yürütücü olduğunda düğümü sağlar. |

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
