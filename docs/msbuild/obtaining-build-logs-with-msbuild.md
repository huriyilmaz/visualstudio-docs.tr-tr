---
title: MSBuild ile Yapı Günlükleri Edinme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f756d432d9ff4d3824c1f1165c63710e4d10c2e9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594896"
---
# <a name="obtain-build-logs-with-msbuild"></a>MSBuild ile yapı günlükleri edinin

MSBuild ile anahtarları kullanarak, gözden geçirmek istediğiniz ne kadar veri oluşturma ve bir veya daha fazla dosyaya yapı verilerini kaydetmek isteyip istemediğiniz belirtebilirsiniz. Yapı verilerini toplamak için özel bir logger da belirtebilirsiniz. Bu konunun kapsamadığı MSBuild komut satırı anahtarları hakkında bilgi için [Bkz.](../msbuild/msbuild-command-line-reference.md)

> [!NOTE]
> Visual Studio IDE'yi kullanarak projeler oluşturursanız, yapı günlüklerini gözden geçirerek bu yapılarda sorun giderebilirsiniz. Daha fazla bilgi için [bkz: Yapı günlüğü dosyalarını görüntülemek, kaydetmek ve yapılandırmak.](../ide/how-to-view-save-and-configure-build-log-files.md)

## <a name="set-the-level-of-detail"></a>Ayrıntı düzeyini ayarlama

 Bir ayrıntı düzeyi belirtmeden MSBuild kullanarak bir proje oluşturduğunuzda, çıktı günlüğünde aşağıdaki bilgiler görüntülenir:

- Son derece önemli olarak sınıflandırılan hatalar, uyarılar ve iletiler.

- Bazı durum olayları.

- Yapının bir özeti.

**-vebosity** (**-v**) anahtarını kullanarak, çıktı günlüğünde ne kadar veri görünebileceğini denetleyebilirsiniz. Sorun giderme için, en çok `detailed` bilgi`d`sağlayan `diagnostic` `diag`bir ayrıntılı bilgi düzeyi ( ) veya ( ) kullanın.

Yapı **işlemi, -verbosity'yi** `detailed` ayarladiğinizde daha yavaş ve **daha** da yavaş `diagnostic`olabilir.

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Ayrıntılı bilgi ayarları

Aşağıdaki tablo, günlük ayrıntılılığının (sütun değerleri) hangi ileti türlerini (satır değerleri) günlüğe kaydedildiğini nasıl etkilediğini gösterir.

|                                       | Quiet | En az | Normal | Ayrıntılı | Tanılama |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Hatalar                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Uyarılar                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Yüksek Öneme Sahip Mesajlar              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Normal öneme sahip Mesajlar           |       |         |    ✅   |     ✅    |      ✅     |
| Düşük Öneme Sahip Mesajlar              |       |         |        |     ✅    |      ✅     |
| Ek MSBuild-motor bilgileri |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Yapı günlüğünü bir dosyaya kaydetme

Yapı verilerini bir dosyaya kaydetmek için **-fileLogger** (**fl**) anahtarını kullanabilirsiniz. Aşağıdaki örnek, yapı verilerini *msbuild.log*adlı bir dosyaya kaydeder.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 Aşağıdaki örnekte, günlük dosyası *MyProjectOutput.log*olarak adlandırılır ve günlük çıktısının ayrıntılılığı `diagnostic`. **-filelogparametreleri** ( )`flp`anahtarını kullanarak bu iki ayarı belirtirsiniz.

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Daha fazla bilgi için [Komut satırı başvurusuna](../msbuild/msbuild-command-line-reference.md)bakın.

## <a name="save-the-log-output-to-multiple-files"></a>Günlük çıktısını birden çok dosyaya kaydetme

 Aşağıdaki örnek *msbuild1.log*için tüm günlük kaydeder , *JustErrors.log*sadece hataları , ve *JustWarnings.log*sadece uyarılar . Örnek, üç dosyanın her biri için dosya numaralarını kullanır. Dosya numaraları **-fl** ve **-flp** anahtarlarından hemen sonra `-fl1` belirtilir `-flp1`(örneğin, ve).

 **-filelogparametreleri** `flp`( ) dosyaları 2 ve 3 için anahtarları ne her dosya nın adını ve ne her dosyaya dahil belirtin. Dosya 1 için ad belirtilmedi, bu nedenle *msbuild1.log* varsayılan adı kullanılır.

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Daha fazla bilgi için [Komut satırı başvurusuna](../msbuild/msbuild-command-line-reference.md)bakın.

## <a name="save-a-binary-log"></a>İkili günlük kaydetme

**-binaryLogger** (**bl**) anahtarını kullanarak oturumu sıkıştırılmış, ikili formatta kaydedebilirsiniz. Bu günlük, yapı işleminin ayrıntılı bir açıklamasını içerir ve belirli günlük çözümleme araçları tarafından okunabilir.

Aşağıdaki örnekte, *binarylogfilename*adı ile bir ikili günlük dosyası oluşturulur.

```cmd
-bl:binarylogfilename.binlog
```

Daha fazla bilgi için [Komut satırı başvurusuna](../msbuild/msbuild-command-line-reference.md)bakın.

## <a name="use-a-custom-logger"></a>Özel bir logger kullanma

 <xref:Microsoft.Build.Framework.ILogger> Arabirimi uygulayan yönetilen bir tür yazarak kendi logger yazabilirsiniz. Örneğin, e-postadaki yapı hataları göndermek, bunları bir veritabanına günlüğe kaydetmek veya bir XML dosyasında günlüğe kaydetmek için özel bir kaydedici kullanabilirsiniz. Daha fazla bilgi için [bkz.](../msbuild/build-loggers.md)

 MSBuild komut satırında, **-logger** anahtarını kullanarak özel kaydediciyi belirtirsiniz. Varsayılan konsol **kaydedicisini** devre dışı kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Loggers oluşturun](../msbuild/build-loggers.md)
- [Çok işlemcili ortamda günlüğe kaydetme](../msbuild/logging-in-a-multi-processor-environment.md)
- [Yönlendirme kaydediciler oluşturma](../msbuild/creating-forwarding-loggers.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
