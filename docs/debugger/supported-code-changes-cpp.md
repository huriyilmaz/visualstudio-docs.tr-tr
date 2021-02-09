---
title: Desteklenen kod değişiklikleri (C++) | Microsoft Docs
description: Visual Studio 'da bir C++ projesinde hata ayıklarken Düzenle ve devam et özelliğini kullanırken hangi kod değişikliklerinin desteklendiğini anlayın.
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
ms.workload:
- cplusplus
ms.openlocfilehash: d000d2757321701c2e14427c6bbb4d3e4164d26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876309"
---
# <a name="supported-code-changes-c"></a>Desteklenen Kod Değişiklikleri (C++)
C++ projeleri için Düzenle ve devam et çoğu kod değişikliği türünü işler. Ancak, bazı değişiklikler program yürütmesi sırasında uygulanamaz. Bu değişiklikleri uygulamak için yürütmeyi durdurmanız ve kodun yeni bir sürümünü oluşturmanız gerekir.

 Visual Studio 'da C++ için Düzenle ve devam et ile çalışma hakkında bilgi için bkz. [düzenleme ve devam etme (C++)](../debugger/edit-and-continue-visual-cpp.md) .

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Gereklilik
### <a name="build-settings-project--properties"></a>Derleme ayarları (proje > özellikleri):
  1. **C/C++ > genel > hata ayıklama bilgisi biçimi**: Düzenle ve devam et Için program veritabanı ( `/ZI` )
  2. **C/C++ > kod oluşturma > en az yeniden derlemeyi etkinleştir**: Evet ( `/Gm` )
  3. **Bağlayıcı > genel > artımlı bağlamayı etkinleştir**: Evet ( `/INCREMENTAL` )

     Uyumsuz bağlayıcı ayarlarının ( `/SAFESEH` veya... `/OPT:` ), derleme sırasında uyarı _LNK4075_ neden olması gerekir.  
     Örnek: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Hata ayıklayıcı ayarları (hata ayıklama > seçenekler > genel):
  - Yerel Düzenle ve devam et 'i etkinleştir

     Uyumsuz derleyici veya bağlayıcı ayarları, düzenleme ve devam etme sırasında hataya neden olur.  
     Örnek: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Desteklenmeyen değişiklikler
 Aşağıdaki C/C++ değişiklikleri hata ayıklama oturumu sırasında uygulanamaz. Bu değişikliklerden herhangi birini yapar ve ardından kod değişikliklerini uygulamaya çalışırsanız **Çıkış** penceresinde bir hata veya uyarı iletisi görüntülenir.

- Genel veya statik verilerde çoğu değişiklik.

- Başka bir makineden kopyalanmış ve yerel olarak oluşturulmamış yürütülebilir dosyalarda yapılan değişiklikler.

- Bir sınıfın veri üyeleri gibi bir nesnenin yerleşimini etkileyen bir veri türünde yapılan değişiklikler.

- En fazla 64 bayt yeni kod veya veri ekleniyor.

- Yönerge işaretçisinden önce bir noktada Oluşturucu gerektiren değişkenler ekleme.

- Çalışma zamanı başlatma gerektiren kodu etkileyen değişiklikler.

- Bazı örneklerde özel durum işleyicileri ekleme.

- Kaynak dosyalarındaki değişiklikler.

- Salt okuma dosyalarındaki koddaki değişiklikler.

- İlgili PDB dosyası olmayan koddaki değişiklikler.

- Nesne dosyası olmayan koddaki değişiklikler.

* Lambdaları değiştirme:
  - Statik veya genel bir üyeye sahip.
  - Bir std:: işlevine geçirilir. Bu, C1092 ' de gerçek bir ODR ihlaline ve sonuçlara neden olur.

- Düzenle ve devam et, statik kitaplıkları güncelleştirmez. Statik kitaplıkta değişiklik yaparsanız, yürütme eski sürümle devam eder ve uyarı verilmez.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Desteklenmeyen senaryolar
 C/C++ için Düzenle ve devam et aşağıdaki hata ayıklama senaryolarında kullanılamaz:

- /Zo ile derlenen yerel uygulamalarda hata ayıklama [(Iyileştirilmiş hata ayıklamayı geliştirme)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Visual Studio 'nun Visual Studio 2015 güncelleştirme 1 ' den önceki sürümlerinde UWP uygulamalarında veya bileşenlerinde hata ayıklaması yapın. Visual Studio 2015 güncelleştirme 1 ' den başlayarak, artık `/ZI` anahtar ile derleyici anahtarını desteklediğinden, UWP C++ uygulamalarında ve DirectX uygulamalarında Düzenle ve devam et ' i kullanabilirsiniz  `/bigobj` . Ayrıca, anahtarla derlenen ikili dosyalarla Düzenle ve devam et ' i de kullanabilirsiniz `/FASTLINK` .

- 8/8.1 Mağaza uygulamalarında hata ayıklama. Bu projeler VC 120 araç takımını ve C/C++ anahtarını kullanır `/bigobj` . Düzenle ve devam et `/bigobj` yalnızca VC 140 araç takımı 'nda desteklenir.

- Windows 98 ' de hata ayıklama.

- Karışık mod (Yerel/yönetilen) hata ayıklama.

- JavaScript hata ayıklaması.

- SQL hata ayıklaması.

- Döküm dosyasında hata ayıklama.

- İşlenmeyen özel **durumlar üzerinde çağrı yığınını geri bırakma** seçeneği seçili değilse, işlenmemiş bir özel durumdan sonra kodu düzenleyebilirsiniz.

- **Hata** ayıklama menüsünde **Başlat** ' a tıklayarak uygulamayı çalıştırmak yerine **öğesine iliştirme** kullanarak bir uygulamada hata ayıklama.

- İyileştirilmiş kodda hata ayıklama.

- Derleme hataları nedeniyle yeni bir sürüm derlenemedi sonra kodunuzun eski bir sürümünde hata ayıklama işlemi başarısız oldu.

- Özel bir derleyici (*cl.exe*) yolu kullanma. Güvenlik nedenleriyle, düzenleme ve devam etme sırasında bir dosyanın yeniden derlenmesi için, Visual Studio her zaman yüklü derleyiciyi kullanır. Özel bir derleyici yolu kullanıyorsanız (örneğin, dosyanızda özel bir `$(ExecutablePath)` değişken aracılığıyla `*.props` ), bir uyarı görüntülenir ve Visual Studio aynı sürüm/mimarinin yüklü derleyicisini kullanmaya geri döner.

- FASTBuild derleme sistemi. FASTBuild Şu anda "En düşük yeniden oluşturma ( `/Gm` )" derleyici anahtarıyla uyumlu değil ve Düzenle ve devam et desteklenmez.

- Eski mimariler/VC araç kümeleri. VC 140 araç takımı ile, varsayılan hata ayıklayıcı hem x86 hem de x64 uygulamalarına göre Düzenle ve devam et ' i destekler. Eski araç kümeleri yalnızca x86 uygulamalarını destekler. VC 120 ' den eski araç kümeleri, Düzenle ve devam et ' i kullanmak için "_hata ayıklama > seçeneklerini > genel >_ yerel uyumluluk modunu kullan" seçeneğini işaretleyerek eski hata ayıklayıcısını kullanmalıdır.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Bağlama sınırlamaları

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Düzenle ve devam et özelliğini devre dışı bırakan bağlayıcı seçenekleri
 Aşağıdaki bağlayıcı seçenekleri Düzenle ve devam et devre dışı bırak:

- **/OPT: ref**, **/OPT: ICF** veya **/ıncresetting** ayarları ayarı devre dışı bırakır ve şu uyarıyla devam et:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- **/Order**, **/Release** veya **/Force** ayarı, düzenlemeyi devre dışı bırakır ve aşağıdaki uyarıyla devam eder:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- Program veritabanı (. pdb) dosyasının oluşturulmasını engelleyen herhangi bir seçeneğin ayarlanması, düzenlemeyi devre dışı bırakır ve belirli bir uyarı olmadan devam eder.

### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Otomatik yeniden bağlama sınırlamaları
 Varsayılan olarak, Düzenle ve devam et, programınızı bir hata ayıklama oturumunun sonunda, güncel bir çalıştırılabilir dosya oluşturacak şekilde yeniden bağlar.

 Özgün derleme konumundan başka bir konumdan hata ayıklaması yapıyorsanız, Düzenle ve devam et programınızı yeniden bağlanamaz. Bir ileti, el ile yeniden oluşturmanız gerektiğini söyler.

 Düzenle ve devam et statik kitaplıkları yeniden oluşturmaz. Düzenle ve devam et kullanarak bir statik kitaplıkta değişiklik yaparsanız, kitaplığı el ile yeniden oluşturmanız ve uygulamayı kullanarak yeniden bağlamanız gerekir.

 Düzenle ve devam et özel derleme adımlarını çağırmıyor. Programınız özel derleme adımları kullanıyorsa, özel derleme adımlarının çağrılabilmesi için el ile yeniden oluşturmak isteyebilirsiniz. Bu durumda, Düzenle ve devam et sonrasında yeniden bağlamayı devre dışı bırakarak el ile yeniden oluşturmanız istenir.

 **Düzenle ve devam et sonrasında yeniden bağlamayı devre dışı bırakmak için**

1. **Hata Ayıkla** menüsünde, **Seçenekler ve ayarlar**' ı seçin.

2. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümü altında, **Düzenle ve devam et** düğümünü seçin.

3. **Hata ayıklamadan sonra kod değişikliklerini yeniden bağla** onay kutusunu temizleyin.

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> Ön derlenmiş üstbilgi sınırlamaları
 Varsayılan olarak, Düzenle ve devam et, kod değişikliklerinin işlenmesini hızlandırmak için arka planda önceden derlenmiş üst bilgileri yükler ve işler. Önceden derlenmiş üst bilgilerin yüklenmesi, sınırlı RAM 'e sahip bir makinede derlerken bir sorun olabilecek fiziksel belleğin ayrılmasını gerektirir. Hata ayıklarken kullanılabilir fiziksel bellek miktarını öğrenmek için Windows Görev Yöneticisi 'Ni kullanarak bir sorun olup olmadığını belirleyebilirsiniz. Bu miktar önceden derlenmiş başlıklarınızın boyutundan fazlaysa, Düzenle ve devam et bir sorun olmaz. Miktar, önceden derlenmiş başlıklarınızın boyutundan küçükse, Düzenle ' yi ve arka planda önceden derlenmiş üst bilgileri yüklemeye devam et ' i engelleyebilirsiniz.

 **Önceden derlenmiş üstbilgilerin Düzenle ve devam et için arka planda yüklemesini devre dışı bırakmak için**

1. **Hata Ayıkla** menüsünde, **Seçenekler ve ayarlar**' ı seçin.

2. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümü altında, **Düzenle ve devam et** düğümünü seçin.

3. **Önceden derlemeye Izin ver** onay kutusunu temizleyin.

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> IDL özniteliği sınırlamaları
 Düzenle ve devam et, arabirim tanımı (IDL) dosyalarını yeniden oluşturmaz. Bu nedenle, hata ayıklarken IDL özniteliklerinde yapılan değişiklikler yansıtılmayacaktır. IDL özniteliklerinin değişikliklerinin sonucunu görmek için, hata ayıklamayı durdurup uygulamanızı yeniden oluşturmanız gerekir. Düzenle ve devam et, IDL öznitelikleri değiştiyse bir hata veya uyarı oluşturmaz. Daha fazla bilgi için bkz. [IDL öznitelikleri](/cpp/windows/idl-attributes).

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> Sorunları tanılama
 Senaryonuz yukarıda bahsedilen koşullara uymuyorsa, aşağıdaki DWORD kayıt defteri değerini ayarlayarak daha fazla ayrıntı toplayabilirsiniz:
 1. Bir Geliştirici Komut İstemi açın.
 2. Şu komutu çalıştırın:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Bir hata ayıklama oturumunun başlangıcında bu değerin ayarlanması, düzenleme ve **Çıkış penceresi**  >  **hata ayıklama** bölmesine ayrıntılı günlük kaydı yapmaya devam eden çeşitli bileşenlere neden olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Düzenle ve Devam Et (C++)](../debugger/edit-and-continue-visual-cpp.md)
