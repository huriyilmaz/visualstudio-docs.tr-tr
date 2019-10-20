---
title: Tanılama verileri ve sistem tarafından oluşturulan Günlükler
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9702439569fa9db1ff8687e914d5c9d20865e2b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652469"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Visual Studio tarafından toplanan sistem tarafından oluşturulan Günlükler

Visual Studio, sorunları gidermeye ve [Visual Studio müşteri deneyimini geliştirme programı](visual-studio-experience-improvement-program.md)aracılığıyla ürünün kalitesini artırmaya yönelik sistem tarafından oluşturulan günlükleri toplar. Bu makalede topladığımız veri türleri ve bunu nasıl kullanırız hakkında bazı bilgiler sağlanmaktadır. Uzantı yazarlarının kişisel veya hassas bilgilerin yanlışlıkla açıklanmasının nasıl önleneceğini gösteren ipuçları da sağlar.

## <a name="types-of-collected-data"></a>Toplanan veri türleri

Visual Studio kilitlenmeler, askıda kalma süresi, Kullanıcı Arabirimi yanıt verme ve yüksek CPU ya da bellek kullanımı için sistem tarafından oluşturulan günlükleri toplar. Ayrıca ürün yüklemesi veya kullanımı sırasında karşılaşılan hatalarla ilgili bilgiler topladık. Toplanan veriler hataya göre farklılık gösterir ve yığın izlemeleri, bellek dökümleri ve özel durum bilgileri içerebilir:

- Yüksek CPU kullanımı ve yanıt verme için, ilgili Visual Studio iş parçacıklarının yığın izlemeleri toplanır.

- Bazı iş parçacıklarının yığın izlemelerinin, sorunun kök nedenini (örneğin kilitlenmeler, askıda kalma veya yüksek bellek kullanımı) belirlemede yeterli olmadığı durumlarda bir bellek *dökümü*topladık. Döküm, hata oluştuğunda işlemin durumunu temsil eder.

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

## <a name="how-we-use-system-generated-logs"></a>Sistem tarafından oluşturulan günlükleri kullanma

Hatanın kök nedenini belirleme iş akışı, hatanın türüne ve önem derecesine bağlı olarak değişir.

### <a name="error-classification"></a>Hata sınıflandırması

Günlüklere göre, hatalar sınıflandırılır ve bunların araştırılması için sayılır. Örneğin, "System.IO" öğesini keşfedebiliriz. \__Error. WinIOError "konumundaki" System. ıO. FILESTREAM. Init ", ürünün \<x > bir 500 kez oluştu ve bu sürümde en yüksek düzeyde oluşuma sahip.

### <a name="work-items-for-tracking"></a>İzleme için iş öğeleri

Bireysel olarak iş öğeleri, öncelikli hatalar oluşturulur ve araştırma için mühendislere atanır. Bu iş öğeleri genellikle hata türüyle ilgili sınıflandırma, öncelik ve tanılama bilgilerini içerir. Bu bilgiler, hata için toplanan sistem tarafından oluşturulan günlüklerden türetilir. Örneğin, kilitlenme için bir iş öğesi kilitlenmenin gerçekleştiği yığın izlemesini içerebilir.

### <a name="error-investigation"></a>Hata araştırma

Mühendisler bir hatanın kök nedenini belirlemede bir iş öğesinde bulunan bilgileri kullanır. Bazı durumlarda, iş öğesinde mevcut olandan daha fazla bilgiye gereksinim duyar ve bu durumda, toplanan özgün sistem tarafından oluşturulan günlüğe başvururlar. Örneğin, bir mühendis bir ürün kilitlenmesinin anlaşılması için bir bellek dökümünü inceleyebilir.

## <a name="tips-for-extension-authors"></a>Uzantı yazarları için ipuçları

Uzantı yazarları, kişisel bilgilerin görünürlüğünü, modülleri, türleri ve yöntemleri adlarında kişisel veya diğer gizli bilgileri kullanmadan sınırlandırmalıdır. Yığında bu kodla bir kilitlenme veya benzer bir hata durumu oluşursa, bu bilgiler sistem tarafından oluşturulan günlüklerin bir parçası olarak toplanır.

## <a name="opt-out-of-data-collection"></a>Veri toplamayı geri çevirme

Topladığımız verilerin amacı ve erişim ve bekletme kısıtlamaları verildiğinde, Visual Studio ve Windows için varsayılan gizlilik ayarlarını kullanmanızı öneririz. Ancak, Visual Studio Deneyimini Geliştirme Programı [devre dışı](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) bırakabilirsiniz. Tüm programlar için sistem tarafından oluşturulan günlük toplamayı devre dışı bırakmak için bkz. [Windows 10 ' da tanılama, geri bildirim ve gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Seçenekler, kullanmakta olduğunuz Windows sürümüne bağlı olarak farklılık gösterebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Müşteri Deneyimi Geliştirme Programı](visual-studio-experience-improvement-program.md)
- [Windows 10 ' da tanılama, geri bildirim ve Gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)