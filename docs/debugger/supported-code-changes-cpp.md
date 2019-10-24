---
title: Desteklenen kod değişiklikleri (C++) | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b93c9cfa6767aea83d941cbc8684b27517c8f911
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729560"
---
# <a name="supported-code-changes-c"></a>Desteklenen Kod Değişiklikleri (C++)
Projeler için C++ Düzenle ve devam et çoğu kod değişikliği türünü işler. Ancak, bazı değişiklikler program yürütmesi sırasında uygulanamaz. Bu değişiklikleri uygulamak için yürütmeyi durdurmanız ve kodun yeni bir sürümünü oluşturmanız gerekir.

 Visual Studio C++ 'da Düzenle ve devam et ile çalışma hakkında bilgi için bkz. [Düzenle ve devamC++et ()](../debugger/edit-and-continue-visual-cpp.md) .

## <a name="BKMK_Unsupported_changes"></a>Desteklenmeyen değişiklikler
 Aşağıdaki C/C++ değişiklikler hata ayıklama oturumu sırasında uygulanamaz:

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

  Bu değişikliklerden birini yapar ve ardından kod değişikliklerini uygulamaya çalışırsanız **Çıkış** penceresinde bir hata veya uyarı iletisi görüntülenir.

- Düzenle ve devam et, statik kitaplıkları güncelleştirmez. Statik kitaplıkta değişiklik yaparsanız, yürütme eski sürümle devam eder ve uyarı verilmez.

## <a name="BKMK_Unsupported_scenarios"></a>Desteklenmeyen senaryolar
 Aşağıdaki hata ayıklama senaryolarında C/C++ için Düzenle ve devam et kullanılamaz:

- /Zo ile derlenen yerel uygulamalarda hata ayıklama [(Iyileştirilmiş hata ayıklamayı geliştirme)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Visual Studio 'nun Visual Studio 2015 güncelleştirme 1 ' den önceki sürümlerinde UWP uygulamalarında veya bileşenlerinde hata ayıklaması yapın. Visual Studio 2015 güncelleştirme 1 ' den başlayarak, artık `/bigobj` anahtarıyla `/ZI` derleyici anahtarını desteklediğinden C++ , UWP uygulamalarında Düzenle ve devam et ' i kullanabilirsiniz. Ayrıca, `/FASTLINK` anahtarıyla derlenen ikili dosyalarla Düzenle ve devam et ' i kullanabilirsiniz.

- Windows 98 ' de hata ayıklama.

- Karışık mod (Yerel/yönetilen) hata ayıklama.

- JavaScript hata ayıklaması.

- SQL hata ayıklaması.

- Döküm dosyasında hata ayıklama.

- İşlenmeyen özel **durumlar üzerinde çağrı yığınını geri bırakma** seçeneği seçili değilse, işlenmemiş bir özel durumdan sonra kodu düzenleyebilirsiniz.

- **Hata** ayıklama menüsünde **Başlat** ' a tıklayarak uygulamayı çalıştırmak yerine **öğesine iliştirme** kullanarak bir uygulamada hata ayıklama.

- İyileştirilmiş kodda hata ayıklama.

- Derleme hataları nedeniyle yeni bir sürüm derlenemedi sonra kodunuzun eski bir sürümünde hata ayıklama işlemi başarısız oldu.

## <a name="BKMK_Linking_limitations"></a>Bağlama sınırlamaları

### <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a>Düzenle ve devam et özelliğini devre dışı bırakan bağlayıcı seçenekleri
 Aşağıdaki bağlayıcı seçenekleri Düzenle ve devam et devre dışı bırak:

- **/OPT: ref**, **/OPT: ICF**veya **/ıncresetting** ayarları ayarı devre dışı bırakır ve şu uyarıyla devam et:

     BAĞLANTı: Warning LNK4075:/EDıTANDCONTINUE/opt nedeniyle yoksayılıyor

     belirtim

- **/Order**, **/Release**veya **/Force** ayarı, düzenlemeyi devre dışı bırakır ve Bu uyarıyla devam eder:

     BAĞLANTı: Warning LNK4075:/OPTION nedeniyle/ıNCRESAYıLıYOR

     belirtim

- Program veritabanı (. pdb) dosyasının oluşturulmasını engelleyen herhangi bir seçeneğin ayarlanması, düzenlemeyi devre dışı bırakır ve belirli bir uyarı olmadan devam eder.

### <a name="BKMK_Auto_relinking_limitations"></a>Otomatik yeniden bağlama sınırlamaları
 Varsayılan olarak, Düzenle ve devam et, programınızı bir hata ayıklama oturumunun sonunda, güncel bir çalıştırılabilir dosya oluşturacak şekilde yeniden bağlar.

 Özgün derleme konumundan başka bir konumdan hata ayıklaması yapıyorsanız, Düzenle ve devam et programınızı yeniden bağlanamaz. Bir ileti, el ile yeniden oluşturmanız gerektiğini söyler.

 Düzenle ve devam et statik kitaplıkları yeniden oluşturmaz. Düzenle ve devam et kullanarak bir statik kitaplıkta değişiklik yaparsanız, kitaplığı el ile yeniden oluşturmanız ve uygulamayı kullanarak yeniden bağlamanız gerekir.

 Düzenle ve devam et özel derleme adımlarını çağırmıyor. Programınız özel derleme adımları kullanıyorsa, özel derleme adımlarının çağrılabilmesi için el ile yeniden oluşturmak isteyebilirsiniz. Bu durumda, Düzenle ve devam et sonrasında yeniden bağlamayı devre dışı bırakarak el ile yeniden oluşturmanız istenir.

 **Düzenle ve devam et sonrasında yeniden bağlamayı devre dışı bırakmak için**

1. **Hata Ayıkla** menüsünde, **Seçenekler ve ayarlar**' ı seçin.

2. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümü altında, **Düzenle ve devam et** düğümünü seçin.

3. **Hata ayıklamadan sonra kod değişikliklerini yeniden bağla** onay kutusunu temizleyin.

## <a name="BKMK_Precompiled_Header_Limitations"></a>Ön derlenmiş üstbilgi sınırlamaları
 Varsayılan olarak, Düzenle ve devam et, kod değişikliklerinin işlenmesini hızlandırmak için arka planda önceden derlenmiş üst bilgileri yükler ve işler. Önceden derlenmiş üst bilgilerin yüklenmesi, sınırlı RAM 'e sahip bir makinede derlerken bir sorun olabilecek fiziksel belleğin ayrılmasını gerektirir. Hata ayıklarken kullanılabilir fiziksel bellek miktarını öğrenmek için Windows Görev Yöneticisi 'Ni kullanarak bir sorun olup olmadığını belirleyebilirsiniz. Bu miktar önceden derlenmiş başlıklarınızın boyutundan fazlaysa, Düzenle ve devam et bir sorun olmaz. Miktar, önceden derlenmiş başlıklarınızın boyutundan küçükse, Düzenle ' yi ve arka planda önceden derlenmiş üst bilgileri yüklemeye devam et ' i engelleyebilirsiniz.

 **Önceden derlenmiş üstbilgilerin Düzenle ve devam et için arka planda yüklemesini devre dışı bırakmak için**

1. **Hata Ayıkla** menüsünde, **Seçenekler ve ayarlar**' ı seçin.

2. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümü altında, **Düzenle ve devam et** düğümünü seçin.

3. **Önceden derlemeye Izin ver** onay kutusunu temizleyin.

## <a name="BKMK_IDL_Attribute_Limitations"></a>IDL özniteliği sınırlamaları
 Düzenle ve devam et, arabirim tanımı (IDL) dosyalarını yeniden oluşturmaz. Bu nedenle, hata ayıklarken IDL özniteliklerinde yapılan değişiklikler yansıtılmayacaktır. IDL özniteliklerinin değişikliklerinin sonucunu görmek için, hata ayıklamayı durdurup uygulamanızı yeniden oluşturmanız gerekir. Düzenle ve devam et, IDL öznitelikleri değiştiyse bir hata veya uyarı oluşturmaz. Daha fazla bilgi için bkz. [IDL öznitelikleri](/cpp/windows/idl-attributes).

## <a name="see-also"></a>Ayrıca bkz.
- [Düzenle ve devam etC++()](../debugger/edit-and-continue-visual-cpp.md)