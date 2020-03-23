---
title: Eşzamanlı Visualizer Command-Line Utility (CVCollectionCmd) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2721798ee9f0c7e006acdedbecaecbd56068be3f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911201"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Eşzamanlı Visualizer komut satırı yardımcı programı (CVCollectionCmd)
Visual Studio için Eşzamanlılık Görselleştiricisi'nde görüntüleyebilmeniz için komut satırından izleme toplamak için Eşzamanlı Visualizer komut satırı yardımcı programını *(CVCollectionCmd.exe)* kullanabilirsiniz. Araçlar Visual Studio yüklü olmayan bilgisayarlarda kullanılabilir.

> [!NOTE]
> Visual Studio 2013'ten itibaren Eşzamanlı Görüntüleyici isteğe bağlı bir uzantıdır. (Daha önce Visual Studio dahil edilmişti.) Visual Studio [2015 için Eşzamanlı Visualizer toplama araçlarını](https://www.microsoft.com/download/details.aspx?id=49103) Download Center'dan indirebilirsiniz.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Eşzamanlı Visualizer komut satırı yardımcı programını indirin
 Komut satırı yardımcı programını indirmek ve yüklemek [için Visual Studio 2015 için Eşzamanlı Visualizer Collection Tools'a](https://www.microsoft.com/download/details.aspx?id=49103) gidin ve talimatları izleyin. Varsayılan *olarak, CVCollectionCmd.exe* x64 bilgisayarlarda %ProgramFiles%\Microsoft Concurrency Visualizer Collection Tools\ (%ProgramFiles(x86)%\Microsoft Concurrency Visualizer Collection Tools\ olarak yüklenir.

## <a name="collect-a-trace-with-cvcollectioncmd"></a>CVCollectionCmd ile bir iz toplamak
 Uygulamayı CVCollectionCmd ile başlatarak veya ekleyerek bir izleme toplayabilirsiniz. Seçenekleriniz için aşağıdaki komut başvurusuna bakın. Örneğin:

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Komutlar ve parametreler
 Komut satırı yardımcı programındaki komutlar ve parametreler hakkında yardım almak için bunu komut istemine yazın:

 **CvCollectionCmd /?**

|Seçenek|Açıklama|Parametreler|Döndürülen değerler|
|------------|-----------------|----------------|-------------------|
|Sorgu|Koleksiyonun başlatılıp başlatılamayacağına dair verir.|None|Toplama başlamaya hazırsa 0.<br /><br /> Toplama zaten devam ediyorsa 1.<br /><br /> 2 toplama devam etmiyorsa, ancak gerekli [ETW](/dotnet/framework/wcf/samples/etw-tracing) oturumlarından biri veya daha fazlası zaten etkin.|
|Başlat|Eşzamanlılık Görselleştiricisi altında belirtilen işlemi çalıştırır.|Yürütülebilir yolun.|0 eğer koşmak başarılı oldu.<br /><br /> Hedef uygulama başlatılamadığı için çalıştırılan 1 başarısız oldu.<br /><br /> CVCollectionCmd belirtilen çıktı dizini yazmak için yeterli izinleri vardır çünkü çalıştırılmaz 13.|
|İliştir|Sistem çapında bir izleme toplamaya başlar; aksi takdirde, bir işlem belirtilirse bağlanır.|Yok.|Eki başarılı olursa 0.<br /><br /> Belirtilen işlem geçersiz veya belirsiz olduğundan eki başarısız olduysa 1.<br /><br /> CVCollectionCmd belirtilen çıktı dizini yazmak için yeterli izinleri vardır çünkü eki başarısız oldu 13.|
|Ayır|Toplamayı durdurur.|Yok.|Müfreze başarılı olursa 0.<br /><br /> Toplama şu anda devam etmediği için ayırma başarısız olduysa 1.<br /><br /> Toplama durdurulamadığından ayırma başarısız olduysa 2.|
|Çözümleme|Belirtilen izi analiz eder.|CVTrace dosyasının tam yolu.|Analiz başarılı olursa 0.<br /><br /> 1 belirtilen izleme sistem çapında olduğu için çözümleme başlanamıyorsa, ancak hedef işlem belirtilmedi.<br /><br /> 2, izleme sistem çapında olmadığı ve bir işlem belirtildiği için çözümlemeye başlayamıyorsa.<br /><br /> Belirtilen işlem geçersiz olduğu için çözümleme başarısız olduysa 3.<br /><br /> Belirtilen CVTrace dosyası geçersiz olduğu için çözümleme başarısız olduysa 4.|
|LaunchArgs|Hedef yürütülebilir bağımsız değişkenleri belirtir. Bu seçenek yalnızca Başlat komutu için geçerlidir.|Uygulamaya komut satırı bağımsız değişkenleri.|Yok.|
|Outdir|İzleme dosyalarını kaydetmek için dizini belirtir. Başlat ve Ekle komutları için geçerlidir.|Dizin yolu veya göreli yol.|Yok.|
|İşleme|Ekle komutu yürütüldüğünde eklenecek işlemi veya Çözümle komutu yürütüldüğünde çözümlemek için bir izlemedeki işlemi belirtir. Ekle ve Çözümle komutları için geçerlidir.|PID veya işlemin adı.|Yok.|
|Config|Varsayılanlar dışında toplama ayarları istiyorsanız yapılandırma dosyasının yolunu belirtir.   Başlat, Ekle ve Çözümle komutları için geçerlidir.|XML yapılandırma dosyasının dizin yolu veya göreli yolu.|Yok.|

## <a name="customize-configuration-settings"></a>Yapılandırma ayarlarını özelleştirme
 İzlemeleri toplamak için CVCollectionCmd kullanıyorsanız ve koleksiyon ayarlarını özelleştirmek istiyorsanız, bunları belirtmek için bir yapılandırma dosyası kullanın.

> [!NOTE]
> İzlemeleri toplamak için Visual Studio'yu kullandığınızda, yapılandırma dosyasını doğrudan değiştirmeyin.  Bunun yerine, ayarları değiştirmek için [Gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu kullanın.

 Koleksiyon ayarlarını değiştirmek için, makinede CVCollectionCmd yardımcı programını çalıştıracağınız bir yapılandırma dosyası oluşturun. Yapılandırma dosyasını sıfırdan oluşturabilir veya Visual Studio yüklü olan bilgisayardaki yapılandırma dosyasını kopyalayabilir ve bunu değiştirebilirsiniz. Dosya *userConfig.xml* olarak adlandırılır ve *Yerel AppData* klasöründe yer alır. Yardımcı programı çalıştırdığınızda, Başlat, Ekle veya Çözümle komutuyla birlikte Config seçeneğini kullanın.  Config seçeneğiyle ilişkili parametrede yapılandırma dosyasının yolunu belirtin.

### <a name="configuration-file-tags"></a>Yapılandırma dosya etiketleri
 Yapılandırma dosyası XML tabanlıdır. Geçerli etiketler ve değerler şunlardır:

| Etiket | Açıklama | Değerler |
|-------------------------| - | - |
| Config | Genel config dosyasını çizer. | Bu öğeleri içermelidir:<br /><br /> - MinorVersion<br />- MajorVersion |
| MajorVersion | Config dosyasının ana sürümünü belirtir. | Projeler için [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 1 olmalıdır. 1 değilse, yardımcı program çalışmaz. |
| MinorVersion | Config dosyasının küçük sürümünü belirtir. | Projeler için [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 0 olmalıdır. 0 değilse, yardımcı program çalışmaz. |
| IncludeEnvSymbolPath | Ortam sembolü yolunun (_NT_SYMBOL_PATH) kullanılıp kullanılmadığını belirleyen bir değer ayarlar. | - Doğru<br />- Yanlış |
| DeleteEtlsAfterAnalysis | Çözümleme tamamlandığında ETL dosyalarının silinip silinmeyeceğini belirleyen bir değer ayarlar. | - Doğru<br />- Yanlış |
| SymbolPath | Sembol sunucusunun yolunu belirtir. Daha fazla bilgi için hata [ayıklama simgesi dosyaları elde etmek için Microsoft Symbol Server'ı kullanın'a](/windows/win32/dxtecharts/debugging-with-symbols)bakın. | Dizin adı veya URL. |
| İşaretler | İşaretleyici sağlayıcılarının listesini içerir. | Sıfır veya daha fazla MarkerSağlayıcı öğesi içerebilir. |
| MarkerSağlayıcı | Tek bir işaret sağlayıcı belirtir. | Bu öğeleri içermelidir:<br /><br /> - Seviye<br />- YOL GÖSTERICI<br />- Adı<br /><br /> Bu öğeleri içerebilir:<br /><br /> - Kategoriler<br />- Etkin |
| Düzey | MarkerSağlayıcı'nın önem düzeyini ayarlar. | - Düşük<br />- Normal<br />- Yüksek<br />- Kritik<br />- Her şey |
| Guid | ETW işaretleyici sağlayıcısının genel olarak benzersiz tanımlayıcısı. | Bİr REHBER. |
| Adı | İşaretleyici sağlayıcısının açıklamasını belirtir. | Bir ip. |
| Kategoriler | İşaretleyici sağlayıcısı için toplanan kategorileri belirtir. | Virgülle sınırlı sayı veya sayı aralıkları dizesi. |
| IsEnabled | İşaretçi sağlayıcısının koleksiyon için etkin olup olmadığını belirleyen bir değer ayarlar. | - Doğru<br />- Yanlış |
| FiltreConfig | Koleksiyondan filtrelenen ETW olaylarının yapılandırma seçenekleri listesini belirtir. | Bu öğeleri içerebilir:<br /><br /> - CollectClrEvents<br />- ClrCollectionSeçenekleri<br />- CollectSampleEvents<br />- CollectGpuEvents<br />- CollectFileio |
| CollectClrEvents | CLR olaylarının toplanıp toplanmadığını belirleyen bir değer ayarlayın. | - Doğru<br />- Yanlış |
| ClrCollectionSeçenekleri | Yerel uygulamalar için CLR etkinliklerinin toplanıp toplanmayacağını ve NGEN özet etkinliklerini toplayıp toplayamayacağını belirtir. | Bu değerlerden birini, her ikisini de veya hiçbirini içerebilir:<br /><br /> - CollectFornative<br />- DisableNGenRundown |
| CollectSampleEvents | Örnek olayların toplanıp toplanmadığını belirleyen bir değer ayarlar. | - Doğru<br />- Yanlış |
| CollectGpuEvents | DX tarafından oluşturulan olayların toplanıp toplanmadığını belirleyen bir değer ayarlar. | - Doğru<br />- Yanlış |
| CollectFileio | Dosya G/Ç olaylarının toplanıp toplanmadığını belirleyen bir değer ayarlar. | - Doğru<br />- Yanlış |
| UserBufferAyarlar | Kullanıcı arabellek ayarları parametreleri listesini belirtir. | Bu öğeleri içermelidir:<br /><br /> - BufferFlushTimer<br />- ArabellekBoyut<br />- Minimum Buffers<br />- MaximumBuffers |
| KernelBufferAyarlar | Çekirdek arabellek ayarları parametreleri listesini belirtir. | Bu öğeleri içermelidir:<br /><br /> - BufferFlushTimer<br />- ArabellekBoyut<br />- Minimum Buffers<br />- MaximumBuffers |
| BufferFlushTimer | ETW arabelleklerinin floş zamanlayıcısını belirtir. | Pozitif bir tamsayı. |
| Buffersize | Her olay izleme oturumu arabelleği için kilobayt olarak ayrılan bellek miktarı. | 0'dan 1024'e kadar bir sayı. |
| Minimum Buffers | Olay izleme oturumunun arabellek havuzuiçin ayrılan en az arabellek sayısı. | Mantıksal çekirdek sayısından iki kat daha büyük veya eşit pozitif bir tamsayı. |
| MaximumBuffers | Olay izleme oturumunun arabellek havuzuiçin ayrılan maksimum arabellek sayısı. | MinimumBuffers'dan daha büyük veya eşit bir sayı. |
| JustMyCode | Just My Code dizinlerinin listesini belirtir. | Sıfır veya daha fazla MyCodeDirectory öğesi listesi. |
| MyCodeDirectory | Kodunuzu içeren bir dizini belirtir. | Mutlak bir yol. |

### <a name="example"></a>Örnek
 En başından itibaren bir yapılandırma dosyası oluşturmak yerine, aşağıdaki örneği kopyalayabilir ve gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz.

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
