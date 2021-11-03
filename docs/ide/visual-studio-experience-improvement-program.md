---
title: Müşteri Deneyimi Geliştirme Programı
description: Visual Studio'de gizlilik ayarlarını yönetmeyi öğrenin ve Visual Studio sistem tarafından oluşturulan günlükler, toplanan veri türleri ve sorunları düzeltmek ve ürün kalitesini geliştirmek için nasıl kullanıldıklarını öğrenin.
ms.date: 10/28/2021
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b5f8991deec8543cd0ce6bf1d134318996bdfc22
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127642"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio Müşteri Deneyimini Geliştirme Programı

Bu Visual Studio Müşteri Deneyimini Geliştirme Programı (VSCEIP), Microsoft'un zaman içinde Visual Studio yardımcı olmak için tasarlanmıştır. Bu [program, hatalara,](../ide/visual-studio-experience-improvement-program.md#types-of-collected-data)bilgisayar donanımına ve kullanıcıların bilgisayar Visual Studio kesintiye uğratmadan nasıl kullanımları hakkında bilgi toplar. Toplanan bilgiler, Microsoft'un hangi özellikleri geliştirmesi için yardımcı olduğunu belirlemeye yardımcı olur. Bu belge VSCEIP'i [nasıl](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) kabul etmek veya devre dışı bırakmayı kapsar ve topladığımız veri türleri ve bunları nasıl kullanabileceğimiz hakkında bazı bilgiler sağlar. Ayrıca, uzantı yazarlarının kişisel veya hassas bilgilerin yanlışlıkla açıklanmasından nasıl kaçınılması konusunda ipuçları sağlar.

## <a name="opt-out-of-diagnostic-data-collection"></a>Tanılama verileri toplamayı geri almayı geri bırakma
Topladığımız verilerin amacı ve erişim ve elde tutma kısıtlamaları nedeniyle, veri koruma ve saklama için varsayılan gizlilik ayarlarını Visual Studio Windows. Bununla birlikte, [Visual Studio](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) Geliştirme Programı'Visual Studio geridildi. Bu seçeneği devre dışı bırakmanız, isteğe bağlı tanılama verileri **toplamayı** geri kabul etmek değildir. Verilerin güvenli, güncel **ve** beklendiği gibi Visual Studio emin olmak için bazı tanılama verileri toplaması gerekir. Gerekli tanılama verileri toplama, VSCEIP'yi geri almayı geri almak sizin seçiminiz tarafından etkilenmez.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> VSCEIP telemetri kabul veya devre dışı bırakma ayarları, uygulamanın 'Sorun Bildir' Visual Studio. Sorun günlüklerini rapor edince toplanır ve yalnızca 'Gönder' seçeneğine tıklayarak izin sağlarken Microsoft'a gönderilir. 'Sorun Bildirin' durumuna göndermeden önce günlükleri yönetmekle ilgileniyorsanız daha fazla ayrıntı için lütfen [Geri Bildirim Veri Gizliliği'ne](./developer-community-privacy.md) bakın.

### <a name="opt-in-or-out"></a>Kabul veya devre dışı bırakma

VSCEIP varsayılan olarak açıktır. Aşağıdaki yönergeleri izleyerek bu sayfayı kapatarak veya yeniden açarak yeniden açamazsınız:

::: moniker range="vs-2017"

1. Bu Visual Studio Geri Bildirim **Gönder'> Yardım'ı seçin** ve sonra da **Ayarlar.**

   Visual Studio **Deneyimi Geliştirme Programı** iletişim kutusu açılır.

1. Geri almak için **Hayır, Katılmak istiyorum'ı ve ardından** Tamam'ı **seçin.** Kabul etmek için **Evet, Katılmak istiyorum'ı ve ardından** Tamam'ı **seçin.**

   ![Visual Studio Deneyim Geliştirme Programı iletişim kutusu](media/experience-improvement-program.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Bu Visual Studio Gizlilik **Gizliliğine Yardım'ı** >  > **Ayarlar.**

   Visual Studio **Deneyimi Geliştirme Programı** iletişim kutusu açılır.

1. Geri almak için **Hayır, Katılmak istiyorum'ı ve ardından** Tamam'ı **seçin.** Kabul etmek için **Evet, Katılmak istiyorum (Önerilen)** seçeneğini ve ardından Tamam'ı **seçin.**

   ![Visual Studio Deneyim Geliştirme Programı iletişim kutusu](media/vs-2022/experience-improvement-program.png)

::: moniker-end

#### <a name="registry-settings"></a>Kayıt Defteri ayarları

Visual Studio için [Derleme Araçları'Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)VSCEIP'yi yapılandırmak için kayıt defterini güncelleştirmeniz gerekir. Enterprise, kayıt defteri tabanlı bir ilke ayarerek VSCEIP'i kabul etmek veya devre dışı bırakmak için bir grup ilkesi yapılandırabilirsiniz.

İlgili kayıt defteri anahtarı ve ayarları aşağıdaki gibidir:

::: moniker range="vs-2017"

- 64 bit işletim sistemi üzerinde Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- 32 bit işletim sistemi üzerinde Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Bu grup ilkesi etkinleştirildiğinde Key = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range="vs-2019"

- 64 bit işletim sistemi üzerinde Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- 32 bit işletim sistemi üzerinde Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Bu grup ilkesi etkinleştirildiğinde Key = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2022"

- 64 bit işletim sistemi üzerinde Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\17.0\SQM**
- 32 bit işletim sistemi üzerinde Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\17.0\SQM**
- Bu grup ilkesi etkinleştirildiğinde Key = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Giriş = **OptIn**

Değer = (DWORD)

- **0** devre dışı (VSCEIP'yi kapatma)
- **1** kabul edildi (VSCEIP'yi açma)

> [!CAUTION]
> Kayıt defterinin hatalı düzenlenmesi sisteminize ciddi şekilde zarar verebilir. Kayıt defterinde değişiklik yapmadan önce, bilgisayarınızdaki tüm değerli verileri yedeklemelisiniz. El ile değişiklikler **uygulandıktan sonra sorunlarla karşılaşırsanız** Bilinen Son İyi Yapılandırma başlatma seçeneğini de kullanabilirsiniz.

VSCEIP tarafından toplanan, işlenen veya iletilen bilgiler hakkında daha fazla bilgi için [bkz. Microsoft Gizlilik Bildirimi.](https://privacy.microsoft.com/privacystatement)

## <a name="system-generated-logs-collected-by-visual-studio"></a>Sistem tarafından oluşturulan günlükler Visual Studio

Visual Studio sorunları düzeltmek ve ürünün kalitesini geliştirmek için sistem tarafından oluşturulan günlükleri toplar. Burada, topladığımız veri türleri ve bunları nasıl kullanabileceğimiz hakkında bazı bilgiler veserde veserde yer alan bilgileri içerir. Ayrıca, uzantı yazarlarının kişisel veya hassas bilgilerin yanlışlıkla açıklanmasından nasıl kaçınılması konusunda ipuçları sağlar.

### <a name="types-of-collected-data"></a>Toplanan veri türleri

Visual Studio kilitlenmeler, kullanıcı arabirimi yanıt vermiyor ve yüksek CPU veya bellek kullanımı için sistem tarafından oluşturulan günlükleri toplar. Ayrıca ürün yüklemesi veya kullanımı sırasında karşılaşılan hatalar hakkında da bilgi toplarız. Toplanan veriler hataya göre değişir ve yığın izlemeleri, bellek dökümleri ve özel durum bilgilerini içerebilir:

- Yüksek CPU kullanımı ve yanıt vermemeye karşı ilgili iş parçacıklarının Visual Studio izlemeleri toplanır.

- Kilitlenme, yanıt vermemeye veya yüksek bellek kullanımı gibi bazı iş parçacıklarının yığın izlemelerinin sorunun kök nedenini belirlemek için yeterli olmayan durumlar için bir bellek dökümünü *toplarız.* Döküm, hatanın meydana geldiği sürecin durumunu temsil eder.

- Örneğin, diskte bir dosyaya yazmaya çalışırken özel durum gibi beklenmeyen hata koşulları için, özel durum hakkında bilgi topluyoruz. Bilgiler özel durumun adını, özel durumun meydana geldiği iş parçacığının yığın izlemesini, özel durumla ilişkili iletiyi ve belirli özel durumla ilgili diğer bilgileri içerir.

   Aşağıdaki toplanan veri örneği bir özel durum adı, yığın izlemesi ve özel durum iletisi gösterir:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

### <a name="how-we-use-system-generated-logs"></a>Sistem tarafından oluşturulan günlükleri kullanma

Hatanın kök nedenini belirleyen iş akışı, hatanın türüne ve önem derecesine bağlı olarak değişir.

#### <a name="error-classification"></a>Hata sınıflandırması

Günlüklere göre hatalar sınıflandırılır ve araştırma önceliklerini belirlemek için sayılır. Örneğin , "System.IO. \_ "System.IO.FileStream.Init" dosyasındaki _Error.WinIOError" ürünün sürümünde 500 kez oluştu ve bu sürümde en yüksek oluşum \<x> oranına sahip.

#### <a name="work-items-for-tracking"></a>İzleme için iş öğeleri

Tek tek, öncelik sırasına göre hataların iş öğeleri oluşturulur ve araştırma için mühendislere atanır. Bu iş öğeleri genellikle hata türüyle ilgili sınıflandırma, öncelik ve tanılama bilgilerini içerir. Bu bilgiler hata için toplanan sistem tarafından oluşturulan günlüklerden türetildi. Örneğin, bir kilitlenme için iş öğesi, kilitlenmenin oluştuğu yığın izlemesini içerebilir.

#### <a name="error-investigation"></a>Hata araştırma

Mühendisler, bir hatanın kök nedenini belirlemek için iş öğesinde bulunan bilgileri kullanır. Bazı durumlarda, iş öğesinde mevcut olandan daha fazla bilgiye ihtiyaç vardır ve bu durumda toplanmış olan sistem tarafından oluşturulan özgün günlüğe başvururlar. Örneğin, bir mühendis bir ürün kilitlenmesi anlamak için bellek dökümlerini inceler.

### <a name="tips-for-extension-authors"></a>İpuçları yazarları için İpuçları

Uzantı yazarları, modülleri, türleri ve yöntemleri adlarında kişisel veya diğer hassas bilgileri kullanmaarak kişisel bilgilerin açıklarını sınırlamalı. Yığında bu kodda kilitlenme veya benzer bir hata koşulu oluşursa, bu bilgiler sistem tarafından oluşturulan günlüklerin bir parçası olarak toplanır.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio ile ilgili bir sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Visual Studio Geliştirici Community](https://developercommunity.visualstudio.com/home)
* [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement)
* [Windows 10'de tanılama, geri bildirim ve gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)
