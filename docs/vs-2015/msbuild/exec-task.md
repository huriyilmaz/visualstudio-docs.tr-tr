---
title: Exec görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a69fc64c3371a2970c03ec0129d4c733f5ae9cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201760"
---
# <a name="exec-task"></a>Yürütme Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen bağımsız değişkenleri kullanarak belirtilen programı veya komutu çalıştırır.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda, görevi için parametreler açıklanmaktadır `Exec` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Command`|Gerekli `String` parametre.<br /><br /> Çalıştırılacak komut (lar). Bunlar, attrib gibi sistem komutları veya program.exe, runprogram.bat veya setup.msi gibi yürütülebilir bir dosya olabilir.<br /><br /> Bu parametre, birden çok komut satırı içerebilir. Alternatif olarak, birden fazla komutu bir toplu iş dosyasına yerleştirebilir ve bu parametreyi kullanarak çalıştırabilirsiniz.|  
|`CustomErrorRegularExpression`|İsteğe bağlı `String` parametre.<br /><br /> Araç çıkışında hata çizgilerini belirlemek için kullanılan bir normal ifade belirtir. Bu, olağandışı biçimli çıkış üreten araçlar için kullanışlıdır.|  
|`CustomWarningRegularExpression`|İsteğe bağlı `String` parametre.<br /><br /> Araç çıkışında uyarı çizgilerini belirlemek için kullanılan bir normal ifade belirtir. Bu, olağandışı biçimli çıkış üreten araçlar için kullanışlıdır.|  
|`ExitCode`|İsteğe bağlı `Int32` Çıkış salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından belirtilen çıkış kodunu belirtir.|  
|`IgnoreExitCode`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev yürütülen komutu tarafından belirtilen çıkış kodunu yoksayar. Aksi takdirde, `false` çalıştırılan komutun sıfır olmayan bir çıkış kodu döndürmesi durumunda görev döndürülür.|  
|`IgnoreStandardErrorWarningFormat`|İsteğe bağlı `Boolean` parametre.<br /><br /> `false`, Çıkışta standart hata/uyarı biçimiyle eşleşen satırları seçer ve bunları hata/uyarı olarak günlüğe kaydeder. Varsa `true` , bu davranışı devre dışı bırakın.|  
|`Outputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Görevden çıkış öğelerini içerir. `Exec`Görev bunları kendisi yapmaz. Bunun yerine, daha sonra projede kullanılabilmesi için bunları ayarlamış gibi sağlayabilirsiniz.|  
|`StdErrEncoding`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yakalanan görev standart hata akışının kodlamasını belirtir. Varsayılan değer geçerli konsol çıkış kodlamasında bulunur.|  
|`StdOutEncoding`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yakalanan görev standart çıkış akışının kodlamasını belirtir. Varsayılan değer geçerli konsol çıkış kodlamasında bulunur.|  
|`WorkingDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Komutun çalıştırılacağı dizini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu görev [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , gerçekleştirmek istediğiniz iş için belirli bir görev kullanılabilir olmadığında yararlıdır. Ancak, `Exec` daha özel bir görevden farklı olarak görev, çalıştırdığı araç veya komuttan çıktı toplayamaz.  
  
 `Exec`Görev, doğrudan bir işlemi çağırmak yerine cmd.exe çağırır.  
  
 Bu belgede listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Exec` bir komutu çalıştırmak için görevini kullanır.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
