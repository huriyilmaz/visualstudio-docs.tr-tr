---
title: MSBuild | ile Derleme Günlüklerini Alma Microsoft Docs
description: Ne kadar derleme verisi gözden geçir MSBuild ve derleme verilerini bir veya daha fazla dosyada kaydedip kaydetmey kararlarını belirtmek için anahtarlarla anahtarları kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: bf812a6c6bb77c2a831fce932dd0b36832d3d66b101f60c27e765d371841a1fd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121257699"
---
# <a name="obtain-build-logs-with-msbuild"></a>Derleme günlüklerini MSBuild

Anahtarlarla anahtarları MSBuild, ne kadar derleme verisini gözden geçirmek ve derleme verilerini bir veya daha fazla dosyaya kaydetmek isteyip istemediklerini belirtebilirsiniz. Derleme verilerini toplamak için özel bir günlükleyici de belirtebilirsiniz. Bu konu başlığında MSBuild komut satırı anahtarları hakkında bilgi için bkz. [Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

> [!NOTE]
> Visual Studio IDE kullanarak proje Visual Studio, derleme günlüklerini gözden geçirerek bu derlemelerin sorunlarını giderebilirsiniz. Daha fazla bilgi için [bkz. Nasıl yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma.](../ide/how-to-view-save-and-configure-build-log-files.md)

## <a name="set-the-level-of-detail"></a>Ayrıntı düzeyini ayarlama

 Bir ayrıntı düzeyi belirtmeden MSBuild kullanarak bir proje derlemeniz, çıktı günlüğünde aşağıdaki bilgiler görünür:

- Son derece önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler.

- Bazı durum olayları.

- Derlemenin özeti.

**-verbosity** (**-v**) anahtarını kullanarak, çıkış günlüğünde ne kadar veri görüntülendiğinden kontrol etmek için. Sorun giderme için en fazla bilgi sağlayan `detailed` ( ) veya ( ) ayrıntılı düzeyini `d` `diagnostic` `diag` kullanın.

-verbosity'i olarak ayarlıyor ve **-verbosity'i** olarak ayarlıyorken derleme işlemi `detailed` **daha yavaş** `diagnostic` olabilir.

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Ayrıntılılık ayarları

Aşağıdaki tabloda günlük ayrıntılılığı (sütun değerleri) hangi ileti türlerinin (satır değerleri) günlüğe kaydedileceğini nasıl etkileyeceğini gösterir.

| İleti türü / Ayrıntılılık              | Quiet | En az | Normal | Ayrıntılı | Tanılama |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Hatalar                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Uyarılar                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Yüksek Öneme Sahip İletiler              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Normal öneme sahip İletiler           |       |         |    ✅   |     ✅    |      ✅     |
| Düşük Öneme Sahip İletiler              |       |         |        |     ✅    |      ✅     |
| Ek MSBuild altyapısı bilgileri |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Derleme günlüğünü bir dosyaya kaydetme

Derleme verilerini bir **dosyaya kaydetmek için -fileLogger** (**fl**) anahtarını kullanabilirsiniz. Aşağıdaki örnek, derleme verilerini *msbuild.log* adlı bir dosyaya kaydeder.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 Aşağıdaki örnekte, günlük dosyası *MyProjectOutput.log* olarak adlandırılmıştır ve günlük çıkışının ayrıntılılığı olarak `diagnostic` ayarlanmıştır. **-fileLoggerParameters** ( ) anahtarını kullanarak bu iki `flp` ayarı belirtirsiniz.

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Daha fazla bilgi için [bkz. Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

## <a name="save-the-log-output-to-multiple-files"></a>Günlük çıktısını birden çok dosyaya kaydetme

 Aşağıdaki örnek günlüğün tamamını *msbuild1.log* dosyasına, yalnızca hataları *JustErrors.log* dosyasına ve yalnızca *JustWarnings.log* dosyasına yapılan uyarıları kaydeder. Örnekte üç dosyanın her biri için dosya numaraları kullanılır. Dosya numaraları -fl ve **-flp** anahtarlardan hemen sonra belirtilir (örneğin, ve  `-fl1` `-flp1` ).

 2. ve 3. dosyalar için **-fileLoggerParameters** ( ) anahtarları, her bir dosyanın adının ne olduğunu ve her bir dosyaya `flp` nelerin ekli olduğunu belirtir. Dosya 1 için bir ad belirtilmedi, bu nedenle *varsayılan msbuild1.log* adı kullanılır.

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Daha fazla bilgi için [bkz. Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

## <a name="save-a-binary-log"></a>İkili günlük kaydetme

**-binaryLogger** (**bl**) anahtarını kullanarak günlüğü sıkıştırılmış, ikili biçimde kaydedebilirsiniz. Bu günlük derleme işleminin ayrıntılı bir açıklamasını içerir ve belirli günlük analizi araçları tarafından okunabilir.

Aşağıdaki örnekte, *binarylogfilename* adıyla bir ikili günlük dosyası oluşturulur.

```cmd
-bl:binarylogfilename.binlog
```

Daha fazla bilgi için [bkz. Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

## <a name="use-a-custom-logger"></a>Özel günlükleyici kullanma

 Arabirimi uygulayan bir yönetilen tür yazarak kendi günlük dosyanızı <xref:Microsoft.Build.Framework.ILogger> yazabilirsiniz. Örneğin, derleme hatalarını e-postayla göndermek, bunları bir veritabanına günlüğe almak veya bir XML dosyasında günlüğe almak için özel bir günlükleyici kullanabilirsiniz. Daha fazla bilgi için [bkz. Derleme günlükçileri.](../msbuild/build-loggers.md)

 Komut **MSBuild-logger** anahtarını kullanarak özel günlükleyiciyi belirtirsiniz. Varsayılan konsol günlükleyicisini **devre dışı bırakmak için -noconsolelogger** anahtarını da kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Günlükçüleri derleme](../msbuild/build-loggers.md)
- [Birden çok işlemcili ortamda oturum açma](../msbuild/logging-in-a-multi-processor-environment.md)
- [İletme günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
