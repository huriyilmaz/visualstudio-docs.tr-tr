---
title: Clang bağlayıcı Özellikleri (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: e8f138b6c496f9dec32ad44dbdfa2064dd639990
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950678"
---
# <a name="clang-linker-properties-android-c"></a>Clang bağlayıcı Özellikleri (Android C++)

Özellik | Açıklama | Yapabileceği
--- | ---| ---
Çıkış dosyası | Seçeneği, bağlayıcının oluşturduğu programın varsayılan adını ve konumunu geçersiz kılar. (-o)
Ilerlemeyi göster | Bağlayıcı Ilerleme Iletilerini yazdırır.
Version | -Version seçeneği, bağlayıcıya yürütülebilir dosyanın üstbilgisine bir sürüm numarası koymasını söyler.
Ayrıntılı çıktıyı etkinleştir | -Verbose seçeneği, bağlayıcıya hata ayıklama için ayrıntılı iletiler çıkışını söyler.
Artımlı bağlamayı etkinleştir | Seçeneği bağlayıcıya artımlı bağlamayı etkinleştirmesini söyler.
Paylaşılan kitaplık arama yolu | Kullanıcının paylaşılan kitaplık arama yolunu doldurmasına izin verir.
Ek kitaplık dizinleri | Kullanıcının ortam kitaplık yolunu geçersiz kılmasına izin verir. (-L klasörü).
Çözümlenmemiş sembol başvurularını raporla | Etkin olduğunda bu seçenek çözümlenmemiş sembol başvurularını rapor eder.
Bellek kullanımı Için iyileştirin | Bellek kullanımı için okuyarak, sembol tablolarını gereken şekilde iyileştirin.
Belirli varsayılan kitaplıkları Yoksay | Yoksayılacak bir veya daha fazla varsayılan kitaplık adını belirtir.
Sembol başvurularını zorla | Simgenin çıkış dosyasına tanımsız bir sembol olarak girilmesini zorla.
Hata ayıklayıcı sembol bilgisi | Çıkış dosyasından hata ayıklayıcı sembol bilgisi. | **Tümünü dahil et**<br>**Yeniden konumlandırma Işlemesi için gereksiz sembolleri atla**<br>**Yalnızca hata ayıklayıcı sembol bilgisini atla**<br>**Tüm sembol bilgilerini atla**<br>
Paket hata ayıklayıcı sembol bilgisi | Paketlemeden önce hata ayıklayıcı sembolleri bilgilerini Strip.  Hata ayıklama için özgün ikilinin bir kopyası kullanılacaktır.
Eşleme dosyası adı | MAP seçeneği, bağlayıcının Kullanıcı tanımlı ada sahip bir eşleme dosyası oluşturmasını söyler.
Yeniden konumlandırmadan sonra değişkenleri ReadOnly olarak işaretle | Bu seçenek, yeniden konumlandırmadan sonra değişkenleri salt okunurdur.
Hemen Işlev bağlamayı etkinleştir | Bu seçenek, hemen işlev bağlamasının nesnesini işaretler.
Yürütülebilir yığın gerektir | Bu seçenek çıktıyı yürütülebilir yığın gerektirmeyen olarak işaretler.
Tüm arşiv | Tüm arşiv kaynaklardaki tüm kodu ve ek bağımlılıkları kullanır.
Ek seçenekler | Ek seçenekler.
{1&gt;Ek Bağımlılıklar&lt;1} | Bağlantı komut satırına eklenecek ek öğeleri belirtir.
Kitaplık bağımlılıkları | Bu seçenek bağlayıcı komut satırına eklenecek ek kitaplıkların belirtilmesine izin verir. Ek kitaplıklar, *LIB* ile başlayan ve *. a* veya *. so* uzantılı bağlayıcı komut satırının sonuna eklenir.  (-lFILE)
