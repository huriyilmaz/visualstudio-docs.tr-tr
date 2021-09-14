---
title: Desteklenen Kod Değişiklikleri (C++) | Microsoft Docs
description: Bir C++ projesinde hata ayıklarken Düzenle ve Devam Edin özelliğini kullanırken hangi kod değişikliklerinin destek Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: c2d7d7a4225c3a2711e238f7100054b1342a65eb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725887"
---
# <a name="supported-code-changes-c"></a>Desteklenen Kod Değişiklikleri (C++)
C++ projeleri için Düzenle ve Devam Edin, çoğu kod değişikliğini işler. Ancak, program yürütme sırasında bazı değişiklikler uygulanamaz. Bu değişiklikleri uygulamak için yürütmeyi durdurmalı ve kodun yeni bir sürümünü oluşturmalı.

 Aşağıdaki [belgelerde C++ için Düzenle](../debugger/edit-and-continue-visual-cpp.md) ve DevamLa ile çalışma hakkında bilgi için bkz. Düzenle ve Devam Visual Studio.

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Gereksinim -leri
### <a name="build-settings-project--properties"></a>Derleme ayarları (Project > Özellikleri):
  1. **C/C++ > Genel > Ayıklama Bilgileri Biçimi:** Düzenle ve Devam Etmek için Program Veritabanı ( `/ZI` )
  2. **C/C++ > Oluşturma > En Az Yeniden Oluşturmayı Etkinleştir**: Evet ( `/Gm` )
  3. **Linker > Genel > Artımlı Bağlamayı Etkinleştir:** Evet ( `/INCREMENTAL` )

     Uyumsuz tüm bağlantı ayarlarında (, veya `/SAFESEH` ...) derleme `/OPT:` sırasında _LNK4075 uyarısına_ neden olması gerekir.  
     Örnek: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Hata ayıklayıcı ayarları (Hata ayıklama > Seçenekleri > Genel):
  - Yerel Düzenleme ve Devam'a Etkinleştirme

     Uyumsuz derleyici veya bağlantıleyici ayarları Düzenle ve Devam Edin sırasında hataya neden olur.  
     Örnek: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Desteklenmeyen değişiklikler
 Hata ayıklama oturumu sırasında aşağıdaki C/C++ değişiklikleri uygulanamaz. Bu değişikliklerden herhangi birini yapın ve ardından kod değişikliklerini uygulamayı denersiniz, Çıkış penceresinde bir hata veya **uyarı iletisi** görüntülenir.

- Genel veya statik verilerde yapılan değişikliklerin çoğu.

- Başka bir makineden kopyalanan ve yerel olarak üretilen yürütülebilir dosyalarda yapılan değişiklikler.

- Bir sınıfın veri üyeleri gibi bir nesnenin düzenini etkileyen bir veri türüne yapılan değişiklikler.

- 64.000'den fazla yeni kod veya veri ekleme.

- Yönerge işaretçisinin önünde bir noktada oluşturucu gerektiren değişkenler ekleme.

- Çalışma zamanı başlatma gerektiren kodu etkileyen değişiklikler.

- Bazı örneklerde özel durum işleyicileri ekleme.

- Kaynak dosyalarında yapılan değişiklikler.

- Salt okunur dosyalarda kodda yapılan değişiklikler.

- İlgili PDB dosyası olmadan kodda yapılan değişiklikler.

- Nesne dosyası olan kodda yapılan değişiklikler.

* Şu lambdaları değiştirme:
  - Statik veya genel üyeye sahip olmalıdır.
  - Std::function'a geçirildi. Bu, orijinal bir ODR ihlaline neden olur ve C1092 ile sonuç verir.

- Düzenle ve Devam Etmek statik kitaplıkları güncelleştirmez. Statik bir kitaplıkta değişiklik yaptısanız, yürütme eski sürümle devam eder ve herhangi bir uyarı olmaz.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Desteklenmeyen senaryolar
 C/C++ için Düzenle ve Devam Bırak, aşağıdaki hata ayıklama senaryolarında kullanılamıyor:

- /Zo ile derlenmiş yerel uygulamalarda hata [ayıklama (İyileştirilmiş Hata Ayıklamayı geliştirme)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Visual Studio 2015 Güncelleştirme 1 Visual Studio önceki sürümlerde UWP uygulamaları veya bileşenlerinde hata ayıklama. Visual Studio 2015 Güncelleştirme 1'den başlayarak UWP C++ uygulamaları ve DirectX uygulamaları içinde Düzenle ve Devam Git'i kullanabilirsiniz çünkü artık anahtar ile derleyici anahtarını `/ZI` `/bigobj` desteklemektedir. Anahtarıyla derlenmiş ikili dosyalarla Düzenle ve Devam'a da `/FASTLINK` kullanabilirsiniz.

- 8/8.1 Mağaza Uygulamalarının Hata Ayıklaması. Bu projeler VC 120 araç kümesi ve C/C++ anahtarını `/bigobj` kullanır. Ile Düzenle ve `/bigobj` Devam Edin, yalnızca VC 140 araç kümesinde de destekleni.

- Windows 98'de hata ayıklama.

- Karma mod (yerel/yönetilen) hata ayıklama.

- JavaScript hata ayıklama.

- SQL hata ayıklama.

- Döküm dosyasında hata ayıklama.

- İşlenemeyen özel durumların ardından kod düzenleme, çağrı **yığınını işlanmamış** özel durumlar üzerinde geriye doğru izleme seçeneği belirlen belirlenmse.

- Hata Ayıklama menüsünde Başlat'ı **seçerek** uygulamayı çalıştırma yerine Ekle'ye **kullanarak** uygulamada **hata** ayıklama.

- İyileştirilmiş kodda hata ayıklama.

- Derleme hataları nedeniyle yeni bir sürüm derleme başarısız olduktan sonra kodunuzun eski bir sürümünde hata ayıklama.

- Özel derleyici kullanma (*cl.exe*) yolu. Güvenlik nedeniyle, Düzenle ve Devam Sırasında bir dosyanın yeniden derlene Visual Studio her zaman yüklü derleyiciyi kullanır. Özel bir derleyici yolu kullanıyorsanız (örneğin, dosyanız içinde özel bir değişken aracılığıyla), bir uyarı görüntülenir ve Visual Studio aynı `$(ExecutablePath)` sürümün/mimarinin yüklü derleyicisi kullanmaya geri `*.props` döner.

- FASTBuild derleme sistemi. FASTBuild şu anda "Minimum Yeniden Derlemeyi Etkinleştir ( )" derleyici anahtarıyla uyumlu değildir ve bu nedenle Düzenle ve Devam Et `/Gm` desteklenmiyor.

- Eski Mimariler/VC Araç Kümeleri. VC 140 araç kümesiyle, varsayılan hata ayıklayıcı hem X86 hem de X64 uygulamalarıyla Düzenle ve Devam'ı destekler. Eski araç kümeleri yalnızca X86 uygulamalarını destekler. DÜZENLE ve Devam'ı kullanmak için VC 120'den eski araç kümeleri " Hata Ayıklama _> Seçenekleri > Genel >_ Yerel Uyumluluk Modunu Kullan" denetlenerek eski hata ayıklayıcısını kullan gerekir.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Bağlama sınırlamaları

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Düzenle ve Devam'ı devre dışı bırakan linker seçenekleri
 Aşağıdaki bağlantıcı seçenekleri Düzenle ve Devam'ı devre dışı bırak:

- **/OPT:REF**, **/OPT:ICF** veya **/INCREMENTAL:NO** ayarı, Düzenle ve Devam'ı şu uyarıyla devre dışı bırakır:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- **/ORDER**, **/RELEASE** veya **/FORCE** ayarı aşağıdaki uyarıyla Düzenle ve Devam'ı devre dışı bırakır:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- Program veritabanı (.pdb) dosyasının oluşturulmasını engelleyen herhangi bir seçeneğin ayarlanmaması, Düzenle ve Devam'ı belirli bir uyarıyla devre dışı bırakır.

### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Otomatik yeniden bağlantı sınırlamaları
 Varsayılan olarak Düzenle ve Devam Bırak, güncel bir yürütülebilir dosya oluşturmak için hata ayıklama oturumunun sonunda programınızı yeniden bağlantılı olarak kullanır.

 Düzenle ve Devam, özgün derleme konumu dışında bir konumdan hata ayıklarken programınızı yeniden bağleyemez. Bir ileti, el ile yeniden oluşturmanız gerektirmektedir.

 Düzenle ve Devam Et, statik kitaplıkları yeniden oluşturmaz. Düzenle ve Devam Et'i kullanarak statik bir kitaplıkta değişiklik yaptısanız, kitaplığı el ile yeniden oluşturmanız ve bunu kullanarak uygulamaları yeniden bağlantılı hale oluşturmanız gerekir.

 Düzenle ve Devam Edin özel derleme adımlarını çağırmaz. Programınız özel derleme adımları kullanıyorsa, özel derleme adımlarını çağırmak için el ile yeniden derlemek istiyor olabilir. Bu durumda, el ile yeniden oluşturmanız istendiğinden emin olmak için Düzenle ve Devam Et'in ardından yeniden bağlantıları devre dışı ekleyebilirsiniz.

 **Düzenle ve Devam'ın ardından yeniden bağlantıları devre dışı bırakmak için**

1. Hata **Ayıkla menüsünde** **Seçenekler'i seçin ve Ayarlar.**

2. Seçenekler **iletişim kutusundaki** Hata ayıklama düğümü **altında Düzenle** ve **Devam'ı** seçin.

3. Hata **ayıklamadan sonra kod değişikliklerini yeniden bağlantıla onay** kutusunun işaretini kaldırın.

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> Önceden derlemeli üst bilgi sınırlamaları
 Varsayılan olarak Düzenle ve Devam Değiştir, kod değişikliklerini işlemeyi hızlandırmak için arka planda önceden derleme yapılan üst bilgileri yükler ve işler. Önceden derleme yapılan üst bilgileri yükleme, fiziksel bellek ayırmayı gerektirir. Bu, sınırlı RAM'e sahip bir makinede derlemek için sorun olabilir. Hata ayıklama sırasında kullanılabilir fiziksel bellek miktarını belirlemek için Windows Görev Yöneticisi'ni kullanarak bunun bir sorun olup olmadığını anabilirsiniz. Bu miktar önceden derlemeli üst bilgilerinizin boyutundan büyükse Düzenle ve Devam'da sorun olmaz. Miktar önceden derlemeli üst bilgilerinizin boyutundan küçükse Düzenle ve Devam'ın arka planda önceden derlemeli üst bilgileri yüklemesini önleyemezsiniz.

 **Düzenle ve Devam Etmek için önceden derlemeli üst bilgileri arka plan yüklemesini devre dışı bırakmak için**

1. Hata **Ayıkla menüsünde** **Seçenekler'i seçin ve Ayarlar.**

2. Seçenekler **iletişim kutusundaki** Hata ayıklama düğümü **altında Düzenle** ve **Devam'ı** seçin.

3. Ön **Derlemeye İzin Ver onay** kutusunun işaretini kaldırın.

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> IDL öznitelik sınırlamaları
 Düzenle ve Devam, arabirim tanımı (IDL) dosyalarını yeniden oluşturmaz. Bu nedenle, hata ayıklama sırasında IDL özniteliklerinde yapılan değişiklikler yansıtlanmaz. IDL özniteliklerinde yapılan değişikliklerin sonucu görmek için hata ayıklamayı durdurmanız ve uygulamanızı yeniden oluşturmanız gerekir. Düzenle ve Devam, IDL öznitelikleri değişmişse hata veya uyarı oluşturmaz. Daha fazla bilgi için [bkz. IDL Öznitelikleri.](/cpp/windows/idl-attributes)

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> Sorunları tanılama
 Senaryonız yukarıda belirtilen koşulların hiçbirine uymuyorsa, aşağıdaki DWORD kayıt defteri değerini ayarerek daha fazla ayrıntı topabilirsiniz:
 1. Bir Geliştirici Komut İstemi.
 2. Şu komutu çalıştırın:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Hata ayıklama oturumunun başında bu değerin ayarı, Düzenle ve Devam'ın çeşitli bileşenlerinin hata ayıklama bölmesinde ayrıntılı **günlük Çıkış Penceresi**  >  **neden** olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Düzenle ve Devam Et (C++)](../debugger/edit-and-continue-visual-cpp.md)
