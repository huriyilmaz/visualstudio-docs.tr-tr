---
title: 'Profiler komut satırı: Enstrüman .NET hizmeti, zamanlama detayı alın'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: af801d2b30c48deb1a88800f67ff4d3efef412b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778901"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Profil oluşturucu komut satırını kullanarak bir .NET hizmetini izleme ve ayrıntılı zamanlama verileri toplama

Bu makalede, Bir .NET Framework hizmeti ne zaman bir araç ve ayrıntılı zamanlama verileri toplamak için Visual Studio Profil Oluşturma Araçları komut satırı araçları nasıl kullanılacağı açıklanmaktadır.

> [!NOTE]
> Bilgisayar başladıktan sonra hizmet yeniden başlatılamıyorsa, bu tür bir hizmet yalnızca işletim sistemi başlatıldığında başlatılırsa, bir hizmeti enstrümantasyon yöntemiyle profilleyemezsiniz.
>
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalışmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşim verilerini topla.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

Bir .NET Framework hizmetinden enstrümantasyon yöntemini kullanarak ayrıntılı zamanlama verileri toplamak için bileşenin enstrümantasyonlu bir sürümünü oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanırsınız. Daha sonra, hizmetin el ile başlatı başlayacak şekilde yapılandırıldığından emin olmak için hizmetin araçiçermeyen sürümünü enstrümantizle değiştirirsiniz. Genel profil oluşturma ortamı değişkenlerini başlatmak ve ardından ana bilgisayarı yeniden başlatmak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanırsınız. Daha sonra profilci başlatın.

Hizmet başlatıldığında, zamanlama verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

Profil oluşturma oturumunu sona erdirmek için hizmeti kapatır ve profil oluşturucuyu açıkça kapatırsınız. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="start-the-application-with-the-profiler"></a>Uygulamayı profil oluşturucuyla başlatın

1. Bir komut istemi penceresi açın.

2. Hizmet ikilisinin enstrümantedilmiş bir sürümünü oluşturmak için **VSInstr** aracını kullanın.

3. Orijinal ikiliyi enstrümanted sürümüyle değiştirin. Windows Service Control Manager'da, hizmet Başlangıç Türü'nün El Ile ayarlandıklarına emin olun.

4. .NET Framework profil oluşturma ortamı değişkenlerini başlangıç olarak karşılayın. Şunu yazın:

     **VSPerfClrEnv /globaltraceon**

5. Bilgisayarı yeniden başlatın.

6. Bir komut istemi penceresi açın.

7. Profilciyi çalıştırın. Şunu yazın:

     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** seçeneği profil oluşturucuyu başlatir.

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verilerinin adını ve konumunu belirtir (.* vsp*) dosyası.

     **/start:trace** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

     > [!NOTE]
     > Profil oluşturma hizmetleri için **genellikle /kullanıcı** ve **/çapraz oturum** seçenekleri gereklidir.

     | Seçenek | Açıklama |
     | - | - |
     | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | Profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek, yalnızca işlem kullanıcı da oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde **Kullanıcı Adı** sütununda listelenir. |
     | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini çıkarma sağlar. Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin **İşlemler** sekmesindeki **Oturum Kimliği** sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
     | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Profilcinin bir hata döndürmeden önce başlatılmasını beklemek için saniye sayısını belirtir. `Interval` Belirtilmemişse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/start** hemen döner. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış profil oluşturucuyu başlatmak için **/globaloff** seçeneğini **/start** komut satırına ekleyin. Profil oluşturmayı sürdürmek için **/globalon'u** kullanın. |
     | [/sayaç](../profiling/counter.md) **:**`Config` | Config'de belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
     | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

8. Hizmeti Windows Service Control Manager'dan başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme

Hizmet çalışırken, profil oluşturucu veri dosyasına veri yazısını başlatmak ve durdurmak için *VSPerfCmd.exe* seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, hizmeti başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

- Aşağıdaki **VSPerfCmd** seçenekleri, veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı kimliği ( ))'nin belirttiği iş parçacığı için (**/threadon)** veya durur (**/threadoff**) veri toplamayı başlatır (`TID`).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma

Profil oluşturma oturumunu sona erdirmek için, enstrümantif bileşeni çalıştıran hizmeti durdurun ve profil oluşturma veri dosyasını kapatmak ve kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın. **VSPerfClrEnv /globaloff** komutu profil oluşturma ortamı değişkenlerini temizler.

Uygulanacak yeni ortam ayarları için bilgisayarı yeniden başlatmanız gerekir.

1. Hizmeti Servis Kontrol Yöneticisi'nden durdurun.

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd /kapatma**

3. Tüm profil oluşturmayı tamamladığınızda, profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv /globaloff**

4. Enstrümantedilen modülü orijinali ile değiştirin. Gerekirse, hizmetin Başlangıç Türünü yeniden yapılandırın.

5. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

[Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
[Enstrümantasyon yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
