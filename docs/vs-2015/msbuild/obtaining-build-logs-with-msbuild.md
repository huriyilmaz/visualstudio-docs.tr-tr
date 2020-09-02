---
title: MSBuild ile derleme günlükleri alma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c88288a7bed453ca14e9c14fd43706b97be04044
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64789479"
---
# <a name="obtaining-build-logs-with-msbuild"></a>MSBuild ile Yapı Günlükleri Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild ile anahtarları kullanarak, ne kadar yapı verisi gözden geçirmek istediğinizi ve derleme verilerini bir veya daha fazla dosyaya kaydetmek isteyip istemediğinizi belirtebilirsiniz. Ayrıca, derleme verilerini toplamak için özel bir günlükçü belirtebilirsiniz. Bu konunun kapsamayan MSBuild komut satırı anahtarları hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> Visual Studio IDE kullanarak projeler oluşturuyorsanız, Derleme günlüklerini inceleyerek bu derlemeler için sorun giderebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Ayrıntı düzeyini ayarlama  
 Bir ayrıntı düzeyi belirtmeden MSBuild kullanarak bir proje oluşturduğunuzda, çıkış günlüğünde aşağıdaki bilgiler görüntülenir:  
  
- Yüksek oranda önemli olarak sınıflandırılan hatalar, uyarılar ve mesajlar.  
  
- Bazı durum olayları.  
  
- Yapı Özeti.  
  
  **/Ayrıntı düzeyi** (**/v**) anahtarını kullanarak, çıktı günlüğünde ne kadar veri göründüğünü denetleyebilirsiniz. Sorun giderme için, `detailed` `d` `diagnostic` `diag` en fazla bilgiyi sağlayan () veya () ayrıntı düzeyini kullanın.  
  
  /Ayrıntı **düzeyini olarak** ayarladığınızda, oluşturma işlemi daha yavaş olabilir `detailed` **/verbosity** `diagnostic` .  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Derleme günlüğünü bir dosyaya kaydetme  
 Derleme verilerini bir dosyaya kaydetmek için **/Filegünlükçü** (**fl**) anahtarını kullanabilirsiniz. Aşağıdaki örnek, derleme verilerini adlı bir dosyaya kaydeder `msbuild.log` .  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Aşağıdaki örnekte, günlük dosyasının adı `MyProjectOutput.log` ve günlük çıkışının ayrıntı düzeyi olarak ayarlanır `diagnostic` . Bu iki ayarı **/filelogparameters** ( `flp` ) anahtarını kullanarak belirtirsiniz.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Günlük çıktısını birden çok dosyaya kaydetme  
 Aşağıdaki örnek, tüm günlüğü `msbuild1.log` , yalnızca hataları `JustErrors.log` ve yalnızca uyarılarını kaydeder `JustWarnings.log` . Örnek, her üç dosyanın dosya numarasını kullanır. Dosya numaraları yalnızca **/fl** ve **/FLP** anahtarlarından sonra belirtilir (örneğin, `/fl1` ve `/flp1` ).  
  
 Dosyalar 2 ve 3 için **/filelogparameters** ( `flp` ) anahtarları her bir dosyanın ne şekilde ekleneceğini ve her dosyaya nelerin ekleneceğini belirtir. Dosya 1 için ad belirtilmedi, bu nedenle varsayılan adı `msbuild1.log` kullanılır.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Özel bir günlükçü kullanma  
 Arabirimini uygulayan bir yönetilen tür yazarak kendi günlüklerinizi yazabilirsiniz <xref:Microsoft.Build.Framework.ILogger> . Özel bir günlükçü, örneğin, e-postada derleme hataları göndermek, bunları bir veritabanına kaydetmek veya bir XML dosyasına kaydetmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [oluşturma Günlükçüler](../msbuild/build-loggers.md).  
  
 MSBuild komut satırında, **/günlükçü** anahtarını kullanarak özel günlükçü belirtirsiniz. Varsayılan konsol günlükçüsü 'yi devre dışı bırakmak için **/noconsolegünlükçü** anahtarını da kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Günlükçüler oluşturun](../msbuild/build-loggers.md)   
 [Çok Işlemcili bir ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)
