---
title: Tanılama verileri ve sistem tarafından oluşturulan günlükler
description: Sistem tarafından Visual Studio günlükler, toplanan veri türleri ve sorunları düzeltmek ve ürün kalitesini geliştirmek için nasıl kullanıldıklarını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028208"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Sistem tarafından oluşturulan günlükler Visual Studio

Visual Studio sorunları çözmek ve ürün kalitesini geliştirmek için sistem tarafından oluşturulan günlükleri [Visual Studio Müşteri Deneyimini Geliştirme Programı.](visual-studio-experience-improvement-program.md) Bu makalede, topladığımız veri türleri ve bunları nasıl kullanabileceğimiz hakkında bazı bilgiler velanmıştır. Ayrıca, uzantı yazarlarının kişisel veya hassas bilgilerin yanlışlıkla açıklanmasından nasıl kaçınılması konusunda ipuçları sağlar.

## <a name="types-of-collected-data"></a>Toplanan veri türleri

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

## <a name="how-we-use-system-generated-logs"></a>Sistem tarafından oluşturulan günlükleri kullanma

Hatanın kök nedenini belirleyen iş akışı, hatanın türüne ve önem derecesine bağlı olarak değişir.

### <a name="error-classification"></a>Hata sınıflandırması

Günlüklere göre hatalar sınıflandırılır ve araştırma önceliklerini belirlemek için sayılır. Örneğin , "System.IO. \_ "System.IO.FileStream.Init" olan _Error.WinIOError" ürünün sürümünde 500 kez oluştu ve bu sürümde en yüksek oluşum \<x> oranına sahip.

### <a name="work-items-for-tracking"></a>İzleme için iş öğeleri

Tek tek, öncelik sırasına göre hataların iş öğeleri oluşturulur ve araştırma için mühendislere atanır. Bu iş öğeleri genellikle hata türüyle ilgili sınıflandırma, öncelik ve tanılama bilgilerini içerir. Bu bilgiler, hata için toplanan sistem tarafından oluşturulan günlüklerden türetildi. Örneğin, bir kilitlenme için iş öğesi, kilitlenmenin oluştuğu yığın izlemesini içerebilir.

### <a name="error-investigation"></a>Hata araştırma

Mühendisler, bir hatanın kök nedenini belirlemek için iş öğesinde bulunan bilgileri kullanır. Bazı durumlarda, iş öğesinde mevcut olandan daha fazla bilgiye ihtiyaç vardır ve bu durumda toplanmış olan sistem tarafından oluşturulan özgün günlüğe başvururlar. Örneğin, bir mühendis bir ürün kilitlenmesi anlamak için bellek dökümlerini inceler.

## <a name="tips-for-extension-authors"></a>İpuçları yazarları için İpuçları

Uzantı yazarları, modülleri, türleri ve yöntemleri adlarında kişisel veya diğer hassas bilgileri kullanmaarak kişisel bilgilerin açıklarını sınırlamalı. Yığında bu kodda kilitlenme veya benzer bir hata koşulu oluşursa, bu bilgiler sistem tarafından oluşturulan günlüklerin bir parçası olarak toplanır.

## <a name="opt-out-of-data-collection"></a>Veri toplamayı geri bırakma

Topladığımız verilerin amacı ve erişim ve elde tutma kısıtlamaları nedeniyle, Visual Studio ve Windows için varsayılan gizlilik ayarlarını Windows. Bununla birlikte, [Visual Studio](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) Geliştirme Programı'Visual Studio geri 3.0'dan çıkabilirsiniz. Bu seçeneği devre dışı bırakmanız, isteğe bağlı tanılama verileri **toplamayı** geri kabul etmek değildir. Verilerin güvenli, güncel **ve** beklendiği gibi Visual Studio emin olmak için bazı tanılama verileri toplaması gerekir. Gerekli tanılama verileri toplama, VSCEIP'yi geri almayı geri almak sizin seçiminiz tarafından etkilenmez. Tüm programlar için sistem tarafından oluşturulan günlük toplamayı geri almak için bkz. Tanılama, geri bildirim ve [gizlilik Windows 10.](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Seçenekler, kullandığınız uygulamanın Windows göre değişebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Müşteri Deneyimi Geliştirme Programı](visual-studio-experience-improvement-program.md)
- [Windows 10'da tanılama, geri bildirim ve gizlilik](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)
