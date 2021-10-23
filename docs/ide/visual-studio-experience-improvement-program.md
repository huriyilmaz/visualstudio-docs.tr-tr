---
title: Müşteri Deneyimi Geliştirme Programı
description: Visual Studio gizlilik ayarlarını yönetmeyi öğrenin ve sistem tarafından oluşturulan günlükler, toplanan veri türleri ve sorunların giderilmesi ve ürün kalitesini geliştirmek için nasıl kullanıldığı Visual Studio hakkında bilgi edinin.
ms.date: 10/18/2021
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3d2148ee4629e8d43edf60ab855dfe0d38eabae5
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130211473"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio Müşteri Deneyimini Geliştirme Programı

Visual Studio Müşteri Deneyimini Geliştirme Programı (vsceıp), Microsoft 'un zaman içinde Visual Studio iyileştirilmesine yardımcı olmak için tasarlanmıştır. bu program hatalar, bilgisayar donanımı ve kişilerin bilgisayardaki görevlerinde kullanıcıları kesintiye uğramadan Visual Studio nasıl kullandıkları [hakkında bilgi toplar](../ide/visual-studio-experience-improvement-program.md#types-of-collected-data). Toplanan bilgiler Microsoft 'un hangi özellikleri iyileştirebileceğinizi belirlemesine yardımcı olur. Bu belgede, VSCEıP 'i [kabul etme veya devre dışı](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) bırakma konuları ele alınmaktadır ve topladığımız veri türleri ve bunu nasıl kullanıyoruz hakkında bazı bilgiler sağlanmaktadır. Uzantı yazarlarının kişisel veya hassas bilgilerin yanlışlıkla açıklanmasının nasıl önleneceğini gösteren ipuçları da sağlar.

## <a name="opt-out-of-diagnostic-data-collection"></a>Tanılama veri toplamayı geri çevirme
topladığımız verilerin amacı ve erişim ve bekletme kısıtlamaları verildiğinde, Visual Studio ve Windows için varsayılan gizlilik ayarlarını kullanmanızı öneririz. ancak, Visual Studio deneyimi geliştirme programını [devre dışı](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) bırakabilirsiniz. Bunu devre dışı bırakırsanız, **isteğe bağlı** tanılama veri toplamayı devre dışı olursunuz. Visual Studio güvenli, güncel ve beklendiği gibi gerçekleştirerek emin olmak için bazı tanılama verileri koleksiyonu **gerekir** . Gerekli tanılama veri toplama, VSCEıP 'i devre dışı bırakmak için seçiminizden etkilenmeyecektir.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> VSCEıP telemetri kabul etme veya çıkış ayarları, Visual Studio ' bir sorun bildir ' için uygulanmaz. Bir sorun günlüğü raporlarken, yalnızca ' Gönder ' seçeneğine tıklayarak izin sağladığınızda Microsoft 'a gönderilir. Günlükleri ' bir sorun bildir ' e göndermeden önce yönetmek istiyorsanız lütfen daha fazla ayrıntı için [geri bildirim veri gizliliği](./developer-community-privacy.md) ' ne bakın.

### <a name="opt-in-or-out"></a>Kabul etme veya kapatma

VSCEıP varsayılan olarak açıktır. Bu yönergeleri izleyerek devre dışı bırakabilirsiniz veya tekrar tekrar açabilirsiniz:

1. Visual Studio, **yardım**  >  **geri bildirimi gönder**' i ve sonra **Ayarlar**' ı seçin.

   **Visual Studio deneyimi geliştirme programı** iletişim kutusu açılır.

1. Devre dışı bırakmak için **Hayır, katılmak istemiyorum**' u seçin ve ardından **Tamam**' ı seçin. Kabul etmek için **Evet, katılmak istiyorum**' u seçin ve ardından **Tamam**' ı seçin.

   ![Visual Studio Deneyim geliştirme programı iletişim kutusu](media/experience-improvement-program.png)

#### <a name="registry-settings"></a>Kayıt Defteri ayarları

[Visual Studio için derleme araçlarını](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)yüklerseniz, vsceıp 'yi yapılandırmak için kayıt defterini güncelleştirmeniz gerekir. Enterprise müşteriler, kayıt defteri tabanlı bir ilke ayarlayarak vsceıp 'i kabul etmek veya kapatmak için bir grup ilkesi oluşturabilir.

İlgili kayıt defteri anahtarı ve ayarları aşağıdaki gibidir:

::: moniker range="vs-2017"

- 64 bitlik bir IŞLETIM sisteminde anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- 32 bitlik bir IŞLETIM sisteminde anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Grup ilkesi etkinleştirildiğinde anahtar = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- 64 bitlik bir IŞLETIM sisteminde anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- 32 bitlik bir IŞLETIM sisteminde anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Grup ilkesi etkinleştirildiğinde anahtar = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Entry = **OptIn**

Değer = (DWORD)

- **0** kabul EDILDI (vsceıp 'i kapatın)
- **1** kabul EDILDI (vsceıp 'i açın)

> [!CAUTION]
> Kayıt defterinin hatalı düzenlenmesi sisteminize ciddi şekilde zarar verebilir. Kayıt defterinde değişiklik yapmadan önce, bilgisayarınızdaki tüm değerli verileri yedeklemelisiniz. Ayrıca, el ile yapılan değişiklikler uygulandıktan sonra sorunlarla karşılaşırsanız **bilinen son Iyi yapılandırma** başlatma seçeneğini de kullanabilirsiniz.

VSCEıP tarafından toplanan, işlenen veya aktarılan bilgiler hakkında daha fazla bilgi için [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/privacystatement)' ne bakın.

## <a name="system-generated-logs-collected-by-visual-studio"></a>Visual Studio tarafından toplanan sistem tarafından oluşturulan Günlükler

Visual Studio sorunları gidermeye ve ürünün kalitesini artırmaya yönelik sistem tarafından oluşturulan günlükleri toplar. Topladığımız veri türleri ve bunu nasıl kullandığımızda aşağıda verilmiştir. Uzantı yazarlarının kişisel veya hassas bilgilerin yanlışlıkla açıklanmasının nasıl önleneceğini gösteren ipuçları da sağlar.

### <a name="types-of-collected-data"></a>Toplanan veri türleri

Visual Studio kilitlenmeler, uı 'nin yanıt verme süresi ve yüksek CPU veya bellek kullanımı için sistem tarafından oluşturulan günlükleri toplar. Ayrıca ürün yüklemesi veya kullanımı sırasında karşılaşılan hatalarla ilgili bilgiler topladık. Toplanan veriler hataya göre farklılık gösterir ve yığın izlemeleri, bellek dökümleri ve özel durum bilgileri içerebilir:

- yüksek CPU kullanımı ve yanıt verme için, ilgili Visual Studio iş parçacıklarının yığın izlemeleri toplanır.

- Bazı iş parçacıklarının yığın izlemelerinin, sorunun kök nedenini (örneğin kilitlenmeler, yanıt verme veya yüksek bellek kullanımı) belirlemede yeterli olmadığı durumlarda bir bellek *dökümü* topladık. Döküm, hata oluştuğunda işlemin durumunu temsil eder.

- Beklenmeyen hata koşulları için örneğin, diskteki bir dosyaya yazmaya çalışırken özel durum hakkında bilgi topladık. Bu bilgiler, özel durumun adını, özel durumun oluştuğu iş parçacığının yığın izlemesini, özel durumla ilişkili iletiyi ve belirli özel durumla ilgili diğer bilgileri içerir.

   Aşağıdaki toplanmış veri örneği bir özel durum adı, yığın izlemesi ve özel durum iletisi gösterir:

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

Hatanın kök nedenini belirleme iş akışı, hatanın türüne ve önem derecesine bağlı olarak değişir.

#### <a name="error-classification"></a>Hata sınıflandırması

Günlüklere göre, hatalar sınıflandırılır ve bunların araştırılması için sayılır. Örneğin, "System.IO" öğesini keşfedebiliriz. \_ _Error. Winıoerror "konumundaki" System. ıO. FILESTREAM. Init ", ürünün sürümünde 500 kez oluştu \<x> ve bu sürümde en yüksek düzeyde oluşuma sahip.

#### <a name="work-items-for-tracking"></a>İzleme için iş öğeleri

Bireysel olarak iş öğeleri, öncelikli hatalar oluşturulur ve araştırma için mühendislere atanır. Bu iş öğeleri genellikle hata türüyle ilgili sınıflandırma, öncelik ve tanılama bilgilerini içerir. Bu bilgiler, hata için toplanan sistem tarafından oluşturulan günlüklerden türetilir. Örneğin, kilitlenme için bir iş öğesi kilitlenmenin gerçekleştiği yığın izlemesini içerebilir.

#### <a name="error-investigation"></a>Hata araştırma

Mühendisler bir hatanın kök nedenini belirlemede bir iş öğesinde bulunan bilgileri kullanır. Bazı durumlarda, iş öğesinde mevcut olandan daha fazla bilgiye gereksinim duyar ve bu durumda, toplanan özgün sistem tarafından oluşturulan günlüğe başvururlar. Örneğin, bir mühendis bir ürün kilitlenmesinin anlaşılması için bir bellek dökümünü inceleyebilir.

### <a name="tips-for-extension-authors"></a>uzantı yazarları için İpuçları

Uzantı yazarları, kişisel bilgilerin görünürlüğünü, modülleri, türleri ve yöntemleri adlarında kişisel veya diğer gizli bilgileri kullanmadan sınırlandırmalıdır. Yığında bu kodla bir kilitlenme veya benzer bir hata durumu oluşursa, bu bilgiler sistem tarafından oluşturulan günlüklerin bir parçası olarak toplanır.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Visual Studio Geliştirici Community](https://developercommunity.visualstudio.com/home)
* [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement)
* [Windows 10 'de tanılama, geri bildirim ve Gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)
