---
title: Eşzamanlılık görselleştiricisi komut satırı yardımcı programı (CVCollectionCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 23c6f008050cc2695a5b86d2164093823726a7b2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300656"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Eşzamanlılık Görselleştiricisi Komut Satırı Yardımcı Programı (CVCollectionCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşzamanlılık görselleştiricisi komut satırı yardımcı programını (CVCollectionCmd. exe), bunları Visual Studio için eşzamanlılık görselleştiricisi içinde görüntüleyebilmeniz için komut satırından izleme toplamak üzere kullanabilirsiniz. Oir 'ler, Visual Studio yüklü olmayan bilgisayarlarda kullanılabilir.  
  
> [!NOTE]
> Visual Studio 2013 başlayarak eşzamanlılık görselleştiricisi isteğe bağlı bir uzantıdır. (Daha önce Visual Studio 'Ya eklenmiştir.) [Visual Studio 2015 Için eşzamanlılık görselleştiricisi koleksiyon araçları](https://www.microsoft.com/download/details.aspx?id=49103) 'Nı indirme merkezi ' nden indirebilirsiniz.  
  
## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Eşzamanlılık görselleştiricisi komut satırı yardımcı programını indirin  
 Komut satırı yardımcı programını indirip yüklemek için, [Visual Studio 2015 Için eşzamanlılık görselleştiricisi koleksiyon araçları](https://www.microsoft.com/download/details.aspx?id=49103) ' na gidin ve yönergeleri izleyin. Varsayılan olarak, CVCollectionCmd. exe,%ProgramFiles%\Microsoft Eşzamanlılık görselleştiricisi koleksiyon araçları \ (% ProgramFiles (x86)% \ Microsoft eşzamanlılık görselleştiricisi koleksiyon araçları \ x64 bilgisayarlarda yüklü).  
  
## <a name="collect-a-trace-with-cvcollectioncmd"></a>CVCollectionCmd ile izleme toplama  
 Uygulamayı CVCollectionCmd ile başlatarak veya buna ekleyerek bir izleme toplayabilirsiniz. Seçenekleriniz için aşağıdaki komut başvurusuna bakın. Örneğin:  
  
```  
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data  
```  
  
## <a name="commands-and-parameters"></a>Komutlar ve Parametreler  
 Komut satırı yardımcı programındaki komutlar ve parametreler hakkında yardım almak için komut istemine şunu yazın:  
  
 **CvCollectionCmd/?**  
  
|Seçenek|Açıklama|Parametreler|Döndürülen değerler|  
|------------|-----------------|----------------|-------------------|  
|Sorgu|Koleksiyonun başlatılıp başlatılmayacağını döndürür.|Yok.|koleksiyon başlamaya hazırsanız 0.<br /><br /> 1 koleksiyon zaten devam ediyorsa.<br /><br /> 2 koleksiyon devam etmiyor, ancak bir veya daha fazla gerekli [ETW](https://msdn.microsoft.com/library/ac99a063-e2d2-40cc-b659-d23c2f783f92) oturumu zaten etkin.|  
|Başlat|Belirtilen işlemi eşzamanlılık görselleştiricisi altında çalıştırır.|Yürütülebilir dosyanın yolu.|çalışma başarılı olursa 0.<br /><br /> 1 hedef uygulama başlatılamadığından çalıştırma başarısız olduysa.<br /><br /> Bu, CVCollectionCmd 'nin belirtilen çıkış dizinine yazmak için yeterli izinlere sahip olduğu için, çalıştırma başarısız olursa 13.|  
|Kullanıma aç|Sistem genelinde izleme toplamaya başlar; Aksi takdirde, bir işlem belirtilmişse bir işleme iliştirir.|Yok.|ek başarılı olursa 0.<br /><br /> Belirtilen işlem geçersiz veya belirsiz olduğundan ek başarısız olursa 1.<br /><br /> CVCollectionCmd 'nin belirtilen çıkış dizinine yazmak için izinleri yetersiz olduğundan, ek başarısız olursa 13.|  
|Ayır|Koleksiyonu durduruyor.|Yok.|Bu, kesilmesi başarılı olursa 0 ' dır.<br /><br /> 1 Şu anda devam eden bir dağıtım başarısız olduğu için çıkarılabilir işlem başarısız oldu.<br /><br /> 2, koleksiyon durdurulamadığından gönderilemedi.|  
|Çözümle|Belirtilen izlemeyi analiz eder.|CVTrace dosyasının tam yolu.|analiz başarılı olursa 0.<br /><br /> 1 analiz başlatılamıyor, çünkü belirtilen izleme sistem genelinde, ancak hedef işlem belirtilmedi.<br /><br /> 2 analiz başlatılamıyor, çünkü izleme sistem genelinde değil ve bir işlem belirtildi.<br /><br /> 3 belirtilen işlem geçersiz olduğundan analiz başarısız oldu.<br /><br /> 4 belirtilen CVTrace dosyası geçersiz olduğundan analiz başarısız oldu.|  
|LaunchArgs|Hedef yürütülebilir bağımsız değişkenleri belirtir. Bu seçenek yalnızca başlatma komutu için geçerlidir.|Uygulamanın komut satırı bağımsız değişkenleri.|Yok.|  
|OutDir|İzleme dosyalarının kaydedileceği dizini belirtir. Başlatma ve Iliştirme komutları için geçerlidir.|Dizin yolu veya göreli yol.|Yok.|  
|Process|Attach komutu yürütüldüğünde iliştirilecek veya çözümle komutu yürütüldüğünde analiz edilecek işlem olan işlemi belirtir. Ekle ve çözümle komutları için geçerlidir.|İşlemin PID 'SI veya adı.|Yok.|  
|Yapılandırma|Koleksiyon ayarlarının varsayılanlar dışında olmasını istiyorsanız, yapılandırma dosyasının yolunu belirtir.   Başlat, Ekle ve çözümle komutları için geçerlidir.|XML yapılandırma dosyasının dizin yolu veya göreli yolu.|Yok.|  
  
## <a name="customizing-configuration-settings"></a>Yapılandırma ayarlarını özelleştirme  
 İzlemeleri toplamak için CVCollectionCmd kullanırsanız ve koleksiyon ayarlarını özelleştirmek istiyorsanız, bunları belirtmek için bir yapılandırma dosyası kullanın.  
  
> [!NOTE]
> İzlemeleri toplamak için Visual Studio kullandığınızda, yapılandırma dosyasını doğrudan değiştirmeyin.  Bunun yerine, ayarları değiştirmek için [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu kullanın.  
  
 Koleksiyon ayarlarını değiştirmek için, CVCollectionCmd yardımcı programını çalıştıracağınız makinede bir yapılandırma dosyası oluşturun. Yapılandırma dosyasını sıfırdan oluşturabilir veya Visual Studio 'nun yüklü olduğu bilgisayarda yapılandırma dosyasını kopyalayabilir ve bunu değiştirebilirsiniz. Dosya `UserConfig.xml` olarak adlandırılır ve **Yerel AppData** klasöründe bulunur. Yardımcı programını çalıştırdığınızda, başlatma, Iliştirme veya çözümle komutuyla birlikte yapılandırma seçeneğini kullanın.  Yapılandırma seçeneği ile ilişkili parametrede, yapılandırma dosyasının yolunu belirtin.  
  
### <a name="configuration-file-tags"></a>Yapılandırma dosyası etiketleri  
 Yapılandırma dosyası XML tabanlıdır. Geçerli Etiketler ve değerler şunlardır:  
  
|Etiket|Açıklama|Değerler|  
|---------|-----------------|------------|  
|Yapılandırma|Genel yapılandırma dosyasını kaldırır.|Şu öğeleri içermelidir:<br /><br /> -MinorVersion<br />-MajorVersion|  
|MajorVersion|Yapılandırma dosyasının ana sürümünü belirtir.|[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projeleri için 1 olmalıdır. 1 değilse, yardımcı program çalışmaz.|  
|MinorVersion|Yapılandırma dosyasının ikincil sürümünü belirtir.|[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projeleri için 0 olmalıdır. 0 değilse, yardımcı program çalışmaz.|  
|Includeenvsymbolpath|Ortam sembol yolunun (_NT_SYMBOL_PATH) kullanılıp kullanılmayacağını belirleyen bir değer ayarlar.|-True<br />-False|  
|DeleteEtlsAfterAnalysis|Analiz tamamlandığında ETL dosyalarının silinip silinmediğini belirleyen bir değer ayarlar.|-True<br />-False|  
|SymbolPath|Sembol sunucusunun yolunu belirtir. Daha fazla bilgi için bkz. [hata ayıklama sembol dosyalarını almak Için Microsoft sembol sunucusunu kullanma](https://go.microsoft.com/fwlink/?LinkID=149389).|Bir dizin adı veya URL 'SI.|  
|İmleçleri|İşaretleyici sağlayıcılarının listesini içerir.|Sıfır veya daha fazla MarkerProvider öğesi içerebilir.|  
|MarkerProvider|Tek bir işaret sağlayıcısını belirtir.|Şu öğeleri içermelidir:<br /><br /> -Düzey<br />-GUID<br />-Ad<br /><br /> Şu öğeleri içerebilir:<br /><br /> -Kategoriler<br />-IsEnabled|  
|Düzey|Bir MarkerProvider 'ın önem düzeyini ayarlar.|-Düşük<br />-Normal<br />-Yüksek<br />-Kritik<br />-Her şey|  
|Guid|ETW işaretleyici sağlayıcısının genel benzersiz tanımlayıcısı.|BIR GUıD.|  
|Name|İşaret sağlayıcısının açıklamasını belirtir.|Bir dize.|  
|Kategoriler|İşaretleyici sağlayıcısı için toplanan kategorileri belirtir.|Virgülle ayrılmış sayı veya sayı aralığı dizesi.|  
|IsEnabled|İşaretleyici sağlayıcının koleksiyon için etkinleştirilip etkinleştirilmeyeceğini belirleyen bir değer ayarlar.|-True<br />-False|  
|FilterConfig|Koleksiyondan filtrelenen ETW olaylarının yapılandırma seçeneklerinin listesini belirtir.|Şu öğeleri içerebilir:<br /><br /> - CollectClrEvents<br />-ClrCollectionOptions<br />-CollectSampleEvents<br />-CollectGpuEvents<br />-CollectFileIO|  
|CollectClrEvents|CLR olaylarının toplanıp toplanmayacağını belirleyen bir değer ayarlayın.|-True<br />-False|  
|ClrCollectionOptions|Yerel uygulamalar için CLR olayları toplayıp toplamayacağını ve NGEN Özet olaylarının toplanmasını isteyip istemediğinizi belirtir.|Şu değerlerden birini, her ikisini birden içerebilir:<br /><br /> -CollectForNative<br />-Disablengenrunaşağı|  
|CollectSampleEvents|Örnek olayların toplanıp toplanmayacağını belirleyen bir değer ayarlar.|-True<br />-False|  
|CollectGpuEvents|DX tarafından oluşturulan olayların toplanıp toplanmadığını belirleyen bir değer belirler.|-True<br />-False|  
|CollectFileIO|Dosya g/ç olaylarının toplanıp toplanmayacağını belirleyen bir değer ayarlar.|-True<br />-False|  
|UserBufferSettings|Kullanıcı arabelleği-ayarlar parametrelerinin listesini belirtir.|Şu öğeleri içermelidir:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers|  
|KernelBufferSettings|Çekirdek arabellek ayarları parametrelerinin listesini belirtir.|Şu öğeleri içermelidir:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers|  
|BufferFlushTimer|ETW arabelleklerinin Temizleme zamanlayıcısını belirtir.|Pozitif bir tamsayı.|  
|Boyutu|Her olay izleme oturumu arabelleği için ayrılan bellek miktarı (kilobayt cinsinden).|0 ile 1024 arasında bir sayı.|  
|MinimumBuffers|Olay izleme oturumunun arabellek havuzu için ayrılan arabellek sayısı alt sınırı.|Mantıksal çekirdek sayısının iki katına eşit veya daha büyük pozitif bir tamsayı.|  
|MaximumBuffers|Olay izleme oturumunun arabellek havuzu için ayrılan en fazla arabellek sayısı.|MinimumBuffers değerinden büyük veya buna eşit bir sayı.|  
|Adatmycode|Yalnızca kendi kodum dizinlerin listesini belirtir.|Sıfır veya daha fazla MyCodeDirectory öğesi listesi.|  
|MyCodeDirectory|Kodunuzu içeren bir dizini belirtir.|Mutlak bir yol.|  
  
### <a name="example"></a>Örnek  
 Baştan itibaren bir yapılandırma dosyası oluşturmak yerine, aşağıdaki örneği kopyalayabilir ve gereksinimlerinizi karşılayacak şekilde değiştirebilirsiniz.  
  
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
