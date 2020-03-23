---
title: Tanılama verileri ve sistem tarafından oluşturulan günlükler
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9702439569fa9db1ff8687e914d5c9d20865e2b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72652469"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Visual Studio tarafından toplanan sistem tarafından oluşturulan günlükler

Visual Studio, Visual [Studio Müşteri Deneyimi Geliştirme Programı](visual-studio-experience-improvement-program.md)aracılığıyla sorunları gidermek ve ürünün kalitesini artırmak için sistem tarafından oluşturulan günlükleri toplar. Bu makalede, topladığımız veri türleri ve bunları nasıl kullandığımız hakkında bazı bilgiler verilmektedir. Ayrıca, uzantı lı yazarların kişisel veya hassas bilgilerin yanlışlıkla ifşa edilmesinden nasıl kaçınabileceklerine ilişkin ipuçları da sağlar.

## <a name="types-of-collected-data"></a>Toplanan veri türleri

Visual Studio çökmeleri, askıda kalma, yanıt vermeme ve yüksek CPU veya bellek kullanımı için sistem tarafından oluşturulan günlükleri toplar. Ayrıca, ürün yükleme veya kullanım sırasında karşılaşılan hatalar hakkında da bilgi toplarız. Toplanan veriler hataya göre değişir ve yığın izlemelerini, bellek dökümlerini ve özel durum bilgilerini içerebilir:

- Yüksek CPU kullanımı ve yanıt vermeme için, ilgili Visual Studio iş parçacıklarının yığın izleri toplanır.

- Bazı iş parçacıklarının yığın izlerinin sorunun temel nedenini belirlemek için yeterli olmadığı durumlarda, örneğin, kilitlenmeler, askıda kalmaveya yüksek bellek kullanımı, bir bellek *dökümü*toplarız. Döküm, hata oluştuğunda işlemin durumunu gösterir.

- Beklenmeyen hata koşulları için, örneğin, diskteki bir dosyaya yazmaya çalışırken bir özel durum için, özel durum hakkında bilgi toplarız. Bilgiler, özel durum adı, özel durum oluştu iş parçacığı yığın izleme, özel durum ile ilişkili ileti ve belirli özel durum ile ilgili diğer bilgileri içerir.

   Toplanan verilerin aşağıdaki örneği bir özel durum adı, yığın izleme ve özel durum iletisi gösterir:

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

## <a name="how-we-use-system-generated-logs"></a>Sistem tarafından oluşturulan günlükleri nasıl kullanırız?

Bir hatanın kök nedenini belirlemek için iş akışı hata türüne ve önem derecesine bağlı olarak değişir.

### <a name="error-classification"></a>Hata sınıflandırması

Günlüklere göre, hatalar sınıflandırılır ve soruşturmalarına öncelik vermek için sayılır. Örneğin, biz keşfedebiliriz "System.IO. \__Error.WinIOError" at "System.IO.FileStream.Init" ürünün sürümü \<x> 500 kez oluştu ve bu sürümde en yüksek oluşum oranına sahiptir.

### <a name="work-items-for-tracking"></a>İzleme için çalışma öğeleri

Tek tek, öncelikli hatalar için çalışma öğeleri oluşturulur ve araştırma için mühendislere atanır. Bu çalışma öğeleri genellikle hata türüyle ilgili sınıflandırma, öncelik ve tanılama bilgilerini içerir. Bu bilgiler, hata için toplanan sistem tarafından oluşturulan günlüklerden türetilmiştir. Örneğin, bir kilitlenme için bir çalışma öğesi, kilitlenmenin gerçekleştiği yığın izini içerebilir.

### <a name="error-investigation"></a>Hata araştırması

Mühendisler, bir hatanın temel nedenini belirlemek için iş öğesinde bulunan bilgileri kullanır. Bazı durumlarda, iş öğesinde bulunandan daha fazla bilgiye ihtiyaç duyarlar ve bu durumda toplanan özgün sistem tarafından oluşturulan günlüklere başvururlar. Örneğin, bir mühendis bir ürün çökmesini anlamak için bellek dökümlerini inceleyebilir.

## <a name="tips-for-extension-authors"></a>Uzantılı yazarlar için ipuçları

Uzantılı yazarlar, modüllerinin, türlerinin ve yöntemlerinin adlarında kişisel veya diğer hassas bilgileri kullanmayarak kişisel bilgilerin maruz kalmasını sınırlamalıdır. Yığındaki bu kodla bir kilitlenme veya benzer hata koşulu oluşursa, bu bilgiler sistem tarafından oluşturulan günlüklerin bir parçası olarak toplanır.

## <a name="opt-out-of-data-collection"></a>Veri toplamayı devre dışı bırakma

Topladığımız verilerin amacı ve erişim ve saklama üzerindeki kısıtlamalar göz önüne alındığında, Visual Studio ve Windows için varsayılan gizlilik ayarlarını kullanmanızı öneririz. Ancak, Visual Studio Deneyimi Geliştirme [Programı'ndan vazgeçebilirsiniz.](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) Tüm programlar için sistem tarafından oluşturulan günlük koleksiyonunu devre dışı bırakmak için [Windows 10'daki Tanılama, geri bildirim ve gizlilik bölümüne](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)bakın. Seçenekler, kullanmakta olduğunuz Windows sürümüne bağlı olarak değişebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Müşteri Deneyimi Geliştirme Programı](visual-studio-experience-improvement-program.md)
- [Windows 10'da tanılama, geri bildirim ve gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)