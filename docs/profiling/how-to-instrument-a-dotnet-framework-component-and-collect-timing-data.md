---
title: 'Profiler komut satırı: Enstrüman istemcisi .NET bileşeni, zaman verilerini almak'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ef50983d964c4b7ef6479117ed2501569a77a62d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778914"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Nasıl yapılır: Tek başına bir .NET Framework bileşenini izleme ve komut satırından profil oluşturucu ile zamanlama verileri toplama
Bu konu, profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar. *exe* veya . *dll* dosya ve ayrıntılı zamanlama verileri toplamak için.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.
>
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalışmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşim verilerini topla.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Enstrümantasyon yöntemini kullanarak bir .NET Framework bileşeninden ayrıntılı zamanlama verileri toplamak için, bileşenin enstrümantize edilmiş bir sürümünü ve profil oluşturma ortamı değişkenlerini başlatmayı sağlamak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanırsınız. Daha sonra profilci başlatın.

 Enstrümantif bileşen yürütüldüğünde, zamanlama verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sona erdirmek için hedef uygulamayı kapatır ve profil oluşturucuyu açıkça kapatırsınız. Çoğu durumda, oturumun sonunda profil oluşturma ortamı değişkenlerini temizlemenizi öneririz.

## <a name="start-the-profiling-session"></a>Profil oluşturma oturumunu başlatma

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Enstrümantasyon yöntemini kullanarak profil oluşturmayı başlatmak için

1. Bir komut istemi penceresi açın. Gerekirse, PATH ortamı değişkeninize profil oluşturma araçları dizini ekleyin. Yol yüklemede eklenmez.

2. Hedef uygulamanın enstrümanted sürümünü oluşturmak için **VSInstr** aracını kullanın.

3. .NET Framework profil oluşturma ortamı değişkenlerini başlangıç olarak karşılayın. Şunu yazın:

    **VSPerfClrEnv /traceon**

4. Profilciyi çalıştırın. Şunu yazın:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** seçeneği profil oluşturucuyu başlatir.

   - [/output](../profiling/output.md)**:** `OutputFile` seçeneği **/start**ile gereklidir. `OutputFile`profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:trace** seçeneği ile aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/kullanıcı](../profiling/user-vsperfcmd.md) **:**[ ]`Domain`**\\**`UserName` | Profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde **Kullanıcı Adı** sütununda listelenir. |
   | [/çapraz oturum](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilini çıkarma sağlar. ASP.NET uygulaması farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi'nin **İşlemler** sekmesindeki **Oturum Kimliği** sütununda listelenir. **/CS** **/ crosssession**için bir kısaltma olarak belirtilebilir. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Veri toplama duraklatılmış profil oluşturucuyu başlatır. Profil oluşturmayı sürdürmek için [/globalon'u](../profiling/globalon-and-globaloff.md) kullanın. |
   | [/sayaç](../profiling/counter.md) **:**`Config` | 'de `Config`belirtilen işlemci performans sayacından bilgi toplar. Sayaç bilgileri, her profil oluşturma etkinliğinde toplanan verilere eklenir. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Yalnızca **/wincounter** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'dir. |
   | [/olaylar](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak windows için olay izleme (ETW) olayı belirtir. ETW olayları ayrı bir şekilde toplanır (.* etl*) dosyası. |

5. Komut İstemi penceresinden hedef uygulamayı başlatın.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazısını başlatıp durdurarak veri toplamayı denetleyebilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmesinin belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlayıp durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler için **(/globalon)** başlatır veya durur (**/globaloff**) veri toplama.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem Kimliği tarafından belirtilen işlem için **(/processon)** başlatır veya **(/processoff)** veri toplamayı durdurur (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı kimliği ( ))'nin belirttiği iş parçacığı için (**/threadon)** veya durur (**/threadoff**) veri toplamayı başlatır (`TID`).|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sonlandırma
 Profil oluşturma oturumunu sona erdirmek için, enstrümantasyonlu bileşeni çalıştıran uygulamayı kapatın. Profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/shutdown](../profiling/shutdown.md) seçeneğini arayın. **VSPerfClrEnv /off** komutu profil oluşturma ortamı değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirmek için

1. Hedef uygulamayı kapatın.

2. Profilciyi kapat. Şunu yazın:

     **VSPerfCmd /kapatma**

3. (İsteğe bağlı) Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv /kapalı**

## <a name="see-also"></a>Ayrıca bkz.
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Enstrümantasyon yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
