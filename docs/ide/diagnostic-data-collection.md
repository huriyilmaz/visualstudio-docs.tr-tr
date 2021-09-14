---
title: Tanılama verileri ve sistem tarafından oluşturulan Günlükler
description: sistem tarafından oluşturulan günlükler, toplanan veri türleri ve sorunların giderilmesi ve ürün kalitesini geliştirmek için nasıl kullanıldığı Visual Studio hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/24/2018
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 1c273da8e1be162eccae100db817ab78c58f8582
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628785"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Visual Studio tarafından toplanan sistem tarafından oluşturulan Günlükler

Visual Studio sorunları gidermeye ve [Visual Studio Müşteri Deneyimini Geliştirme Programı](visual-studio-experience-improvement-program.md)aracılığıyla ürünün kalitesini artırmaya yönelik sistem tarafından oluşturulan günlükleri toplar. Bu makalede topladığımız veri türleri ve bunu nasıl kullanırız hakkında bazı bilgiler sağlanmaktadır. Uzantı yazarlarının kişisel veya hassas bilgilerin yanlışlıkla açıklanmasının nasıl önleneceğini gösteren ipuçları da sağlar.

## <a name="types-of-collected-data"></a>Toplanan veri türleri

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

## <a name="how-we-use-system-generated-logs"></a>Sistem tarafından oluşturulan günlükleri kullanma

Hatanın kök nedenini belirleme iş akışı, hatanın türüne ve önem derecesine bağlı olarak değişir.

### <a name="error-classification"></a>Hata sınıflandırması

Günlüklere göre, hatalar sınıflandırılır ve bunların araştırılması için sayılır. Örneğin, "System.IO" öğesini keşfedebiliriz. \_ _Error. Winıoerror "konumundaki" System. ıO. FILESTREAM. Init ", ürünün sürümünde 500 kez oluştu \<x> ve bu sürümde en yüksek düzeyde oluşuma sahip.

### <a name="work-items-for-tracking"></a>İzleme için iş öğeleri

Bireysel olarak iş öğeleri, öncelikli hatalar oluşturulur ve araştırma için mühendislere atanır. Bu iş öğeleri genellikle hata türüyle ilgili sınıflandırma, öncelik ve tanılama bilgilerini içerir. Bu bilgiler, hata için toplanan sistem tarafından oluşturulan günlüklerden türetilir. Örneğin, kilitlenme için bir iş öğesi kilitlenmenin gerçekleştiği yığın izlemesini içerebilir.

### <a name="error-investigation"></a>Hata araştırma

Mühendisler bir hatanın kök nedenini belirlemede bir iş öğesinde bulunan bilgileri kullanır. Bazı durumlarda, iş öğesinde mevcut olandan daha fazla bilgiye gereksinim duyar ve bu durumda, toplanan özgün sistem tarafından oluşturulan günlüğe başvururlar. Örneğin, bir mühendis bir ürün kilitlenmesinin anlaşılması için bir bellek dökümünü inceleyebilir.

## <a name="tips-for-extension-authors"></a>uzantı yazarları için İpuçları

Uzantı yazarları, kişisel bilgilerin görünürlüğünü, modülleri, türleri ve yöntemleri adlarında kişisel veya diğer gizli bilgileri kullanmadan sınırlandırmalıdır. Yığında bu kodla bir kilitlenme veya benzer bir hata durumu oluşursa, bu bilgiler sistem tarafından oluşturulan günlüklerin bir parçası olarak toplanır.

## <a name="opt-out-of-data-collection"></a>Veri toplamayı geri çevirme

topladığımız verilerin amacı ve erişim ve bekletme kısıtlamaları verildiğinde, Visual Studio ve Windows için varsayılan gizlilik ayarlarını kullanmanızı öneririz. ancak, Visual Studio deneyimi geliştirme programını [devre dışı](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) bırakabilirsiniz. Bunu devre dışı bırakırsanız, **isteğe bağlı** tanılama veri toplamayı devre dışı olursunuz. Visual Studio güvenli, güncel ve beklendiği gibi gerçekleştirerek emin olmak için bazı tanılama verileri koleksiyonu **gerekir** . Gerekli tanılama veri toplama, VSCEıP 'i devre dışı bırakmak için seçiminizden etkilenmeyecektir. Tüm programlar için sistem tarafından oluşturulan günlük toplamayı devre dışı bırakmak için [Windows 10 'de tanılama, geri bildirim ve gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)bölümüne bakın. seçenekler, kullanmakta olduğunuz Windows sürümüne göre farklılık gösterebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Müşteri Deneyimi Geliştirme Programı](visual-studio-experience-improvement-program.md)
- [Windows 10 'de tanılama, geri bildirim ve Gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)
