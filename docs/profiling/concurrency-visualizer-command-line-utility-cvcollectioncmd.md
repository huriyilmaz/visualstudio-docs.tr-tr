---
title: Eşzamanlılık görselleştirici komut satırı yardımcı programı
description: Eşzamanlılık Görselleştiricisi'nde CVCollectionCmd.exe izlemeleri toplamak için komut satırı yardımcı programını kullanın. Uygulamanın yüklü olması Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5f7472046b6c8ac675d2fb0cc92856e3996f380f751d825613cb59b39c785d7b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396844"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Eşzamanlılık Görselleştirici komut satırı yardımcı programı (CVCollectionCmd)
Eşzamanlılık Görselleştiricisi komut satırı yardımcı programını (*CVCollectionCmd.exe*) kullanarak komut satırı izlemelerini toplayabilirsiniz. Böylece, komut satırı için Eşzamanlılık Görselleştiricisi'nde Visual Studio. Araçlar, yüklü yüklü Visual Studio kullanılabilir.

> [!NOTE]
> Bu Visual Studio 2013 eşzamanlılık Görselleştiricisi isteğe bağlı bir uzantıdır. (Daha önce bu, Visual Studio.) [Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) için Eşzamanlılık Görselleştiricisi koleksiyon araçlarını İndirme Merkezi'nde indirebilirsiniz.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Eşzamanlılık Görselleştiricisi komut satırı yardımcı programını indirin
 Komut satırı yardımcı programını indirip yüklemek için, [Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) için Eşzamanlılık Görselleştiricisi Koleksiyon Araçları'na gidin ve yönergeleri izleyin. Varsayılan olarak *CVCollectionCmd.exe,* x64 bilgisayarlarda %ProgramFiles%\Microsoft Eşzamanlılık Görselleştiricisi Koleksiyon Araçları\ (%ProgramFiles(x86)%\Microsoft Eşzamanlılık Görselleştiricisi Koleksiyon Araçları\ dizinine yüklenir.

## <a name="collect-a-trace-with-cvcollectioncmd"></a>CVCollectionCmd ile izleme toplama
 Uygulamayı CVCollectionCmd ile başlatarak veya buna eklayarak bir izleme toplayabilirsiniz. Seçenekleriniz için aşağıdaki komut başvurusuna bakın. Örneğin:

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Komutlar ve parametreler
 Komut satırı yardımcı programında komutlar ve parametreler hakkında yardım almak için komut istemine şu komutu yazın:

 **CvCollectionCmd /?**

|Seçenek|Açıklama|Parametreler|Dönüş değerleri|
|------------|-----------------|----------------|-------------------|
|Sorgu|Koleksiyonun başlatılap başlatılanamayrı döndürür.|Hiçbiri|Koleksiyon başlamaya hazırsa 0.<br /><br /> Koleksiyon devam ediyorsa 1.<br /><br /> Koleksiyon devam etmese ama gerekli [ETW](/dotnet/framework/wcf/samples/etw-tracing) oturumlarından biri veya daha fazlası zaten etkinse 2.|
|Başlat|Belirtilen işlemi Eşzamanlılık Görselleştiricisi altında çalıştırır.|Yürütülebilir dosyanın yolu.|Çalıştırma başarılı olursa 0.<br /><br /> Hedef uygulama başlatılamadı nedeniyle çalıştırma başarısız olursa 1.<br /><br /> CVCollectionCmd belirtilen çıkış dizinine yazmak için yeterli izinlere sahip olmaması nedeniyle çalıştırma başarısız olursa 13.|
|İliştir|Sistem genelinde izleme toplamaya başlar; aksi takdirde, belirtilirse bir işleme iliştirer.|Yok.|Ek başarılı olursa 0.<br /><br /> Belirtilen işlem geçersiz veya belirsiz olduğundan ek başarısız olursa 1.<br /><br /> CVCollectionCmd belirtilen çıkış dizinine yazma izni yetersiz olduğundan ek başarısız olursa 13.|
|Ayır|Koleksiyonu durdurur.|Yok.|Ayırma başarılı olursa 0.<br /><br /> Koleksiyon şu anda devam eden bir durumda olduğundan ayırma başarısız olursa 1.<br /><br /> Koleksiyon durdurulamadı nedeniyle ayırma başarısız olursa 2.|
|Analiz|Belirtilen izlemeyi analiz eder.|CVTrace dosyasının tam yolu.|Analiz başarılı olursa 0.<br /><br /> Belirtilen izleme sistem genelinde olduğu için analiz başlatılamasa da hedef işlem belirtilmemişse 1.<br /><br /> İzleme sistem genelinde değil ve bir işlem belirtilmiş olduğundan analiz başlatılamaysa 2.<br /><br /> Belirtilen işlem geçersiz olduğundan analiz başarısız olursa 3.<br /><br /> Belirtilen CVTrace dosyası geçersiz olduğundan analiz başarısız olursa 4.|
|LaunchArgs|Hedef yürütülebilir bağımsız değişkenleri belirtir. Bu seçenek yalnızca Başlat komutu için geçerlidir.|Uygulamanın komut satırı bağımsız değişkenleri.|Yok.|
|Outdir|İzleme dosyalarının kaydedil olduğu dizini belirtir. Başlatma ve Ekleme komutları için geçerlidir.|Dizin yolu veya göreli yol.|Yok.|
|İşleme|Ekle komutu yürütülürken eklenecek işlemi veya Analiz komutu yürütülürken analiz edilecek bir izleme işlemini belirtir. Ekle ve Çözümle komutları için geçerlidir.|PID veya sürecin adı.|Yok.|
|Config|Varsayılanlar dışında koleksiyon ayarlarına sahip olmak için yapılandırma dosyasının yolunu belirtir.   Launch, Attach ve Analyze komutları için geçerlidir.|XML yapılandırma dosyasının dizin yolu veya göreli yolu.|Yok.|

## <a name="customize-configuration-settings"></a>Yapılandırma ayarlarını özelleştirme
 İzlemeleri toplamak için CVCollectionCmd kullanıyorsanız ve koleksiyon ayarlarını özelleştirmek için bunları belirtmek için bir yapılandırma dosyası kullanın.

> [!NOTE]
> İzlemeleri toplamak Visual Studio bir dosya kullanırsanız, yapılandırma dosyasını doğrudan değiştirmeyin.  Bunun yerine, ayarları [değiştirmek Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Gelişmiş Yapılandırma iletişim kutusunu kullanın.

 Koleksiyon ayarlarını değiştirmek için, CVCollectionCmd yardımcı programını çalıştıracak makinede bir yapılandırma dosyası oluşturun. Yapılandırma dosyasını sıfırdan oluşturabilir veya yapılandırma dosyasını yüklü olan bilgisayara kopyalayıp Visual Studio değiştirebilirsiniz. Dosya, *UserConfig.xml* olarak adlandırılmış ve Local *AppData klasöründe* yer almaktadır. Yardımcı programı çalıştırarak Başlat, Ekle veya Çözümle komutuyla birlikte Yapılandırma seçeneğini kullanın.  Yapılandırma seçeneğiyle ilişkili parametrede yapılandırma dosyasının yolunu belirtin.

### <a name="configuration-file-tags"></a>Yapılandırma dosyası etiketleri
 Yapılandırma dosyası XML tabanlıdır. Geçerli etiketler ve değerler şu şekildedir:

| Etiket | Açıklama | Değerler |
|-------------------------| - | - |
| Config | Genel yapılandırma dosyasını belirtir. | Şu öğeleri içermesi gerekir:<br /><br /> - MinorVersion<br />- MajorVersion |
| MajorVersion | Yapılandırma dosyasının ana sürümünü belirtir. | Projeler için 1 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] olması gerekir. 1 yoksa, yardımcı program çalışmaz. |
| MinorVersion | Yapılandırma dosyasının ikincil sürümünü belirtir. | Projeler için 0 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] olması gerekir. 0 yoksa yardımcı program çalışmaz. |
| IncludeEnvSymbolPath | Ortam sembol yolunun (_NT_SYMBOL_PATH) kullan _NT_SYMBOL_PATH ayarlar. | - True<br />- Yanlış |
| DeleteEtlsAfterAnalysis | Analiz tamamlandığında ETL dosyalarının silinip silin olmadığını belirleyen bir değer ayarlar. | - True<br />- Yanlış |
| SymbolPath | Sembol sunucusunun yolunu belirtir. Daha fazla bilgi için [bkz. Hata ayıklama sembol dosyalarını almak için Microsoft Sembol Sunucusunu kullanma.](/windows/win32/dxtecharts/debugging-with-symbols) | Dizin adı veya URL. |
| İşaretler | İşaretçi sağlayıcıları listesini içerir. | Sıfır veya daha fazla MarkerProvider öğeleri içerebilir. |
| MarkerProvider | Tek bir işaretçi sağlayıcısı belirtir. | Şu öğeleri içermesi gerekir:<br /><br /> - Düzey<br />- GUID<br />- Ad<br /><br /> Şu öğeleri içerebilir:<br /><br /> - Kategoriler<br />- IsEnabled |
| Level | MarkerProvider'ın önem düzeyini ayarlar. | - Düşük<br />- Normal<br />- Yüksek<br />- Kritik<br />- Her şey |
| Guid | ETW işaretçi sağlayıcısının genel olarak benzersiz tanımlayıcısı. | A GUID. |
| Name | İşaretçi sağlayıcısının açıklamasını belirtir. | Bir dize. |
| Kategoriler | İşaretleyici sağlayıcısı için toplanan kategorileri belirtir. | Sayılardan veya sayı aralıklarının virgülle ayrılmış dizesi. |
| IsEnabled | İşaretçi sağlayıcısının koleksiyon için etkin olup olmadığını belirleyen bir değer ayarlar. | - True<br />- Yanlış |
| FilterConfig | Koleksiyondan filtrelenmiş ETW olaylarının yapılandırma seçeneklerinin listesini belirtir. | Şu öğeleri içerebilir:<br /><br /> - CollectClrEvents<br />- ClrCollectionOptions<br />- CollectSampleEvents<br />- CollectGpuEvents<br />- CollectFileIO |
| CollectClrEvents | CLR olaylarını toplanmış olup olmadığını belirleyen bir değer ayarlayın. | - True<br />- Yanlış |
| ClrCollectionOptions | Yerel uygulamalar için CLR olaylarını toplamayı ve NGEN rundown olaylarını toplamayı belirtir. | Bu değerlerden birini, ikisini birden veya hiçbirini içerebilir:<br /><br /> - CollectForNative<br />- DisableNGenRundown |
| CollectSampleEvents | Örnek olayların toplanmış olup olmadığını belirleyen bir değer ayarlar. | - True<br />- Yanlış |
| CollectGpuEvents | DX tarafından oluşturulan olayların toplanmış olup olmadığını belirleyen bir değer ayarlar. | - True<br />- Yanlış |
| CollectFileIO | Dosya I/O olaylarını toplanacak olup olmadığını belirleyen bir değer ayarlar. | - True<br />- Yanlış |
| UserBufferSettings | Kullanıcı arabelleği ayarları parametrelerinin listesini belirtir. | Şu öğeleri içermesi gerekir:<br /><br /> - BufferFlushTimer<br />- BufferSize<br />- MinimumBuffers<br />- MaximumBuffers |
| KernelBufferSettings | Çekirdek arabellek ayarları parametrelerinin listesini belirtir. | Şu öğeleri içermesi gerekir:<br /><br /> - BufferFlushTimer<br />- BufferSize<br />- MinimumBuffers<br />- MaximumBuffers |
| BufferFlushTimer | ETW arabelleklerinin boşaltma zamanlayıcısını belirtir. | Pozitif tamsayı. |
| Buffersize | Her olay izleme oturumu arabelleği için kilobayt cinsinden ayrılan bellek miktarı. | 0 ile 1024 arasında bir sayı. |
| MinimumBuffers | Olay izleme oturumunun arabellek havuzu için ayrılan en düşük arabellek sayısı. | Mantıksal çekirdek sayısının iki katı kadar veya daha büyük pozitif bir tamsayı. |
| MaximumBuffers | Olay izleme oturumunun arabellek havuzu için ayrılan arabellek sayısı üst sayısı. | MinimumBuffers'dan büyük veya bu değere eşit bir sayı. |
| JustMyCode | Dizinlerin listesini Yalnızca kendi kodum belirtir. | Sıfır veya daha fazla MyCodeDirectory öğelerinin listesi. |
| MyCodeDirectory | Kodunuzu içeren bir dizin belirtir. | Mutlak yol. |

### <a name="example"></a>Örnek
 Yapılandırma dosyasını en baştan oluşturmak yerine aşağıdaki örneği kopyalayıp gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz.

```xml
<?xml version="1.0"?>
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>

  <TraceLocation>C:\traces</TraceLocation>

  <SymbolPath>http://symweb</SymbolPath>

  <Markers>
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />

    <!-- The IsEnabled and Categories elements are optional -->
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />
  </Markers>

  <FilterConfig>
    <CollectClrEvents>true</CollectClrEvents>
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>
    <CollectSampleEvents>true</CollectSampleEvents>
    <CollectGpuEvents>true</CollectGpuEvents>
    <CollectFileIO>true</CollectFileIO>
  </FilterConfig>

  <UserBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </UserBufferSettings>

  <KernelBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </KernelBufferSettings>

  <!-- List of MyCodeDirectory directories -->
  <JustMyCode>
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>
  </JustMyCode>
</LocalConfig>

```
