---
title: Desteklenen kod değişiklikleri (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f167b3e9d27145284defa2ff491bb9ce0085f2a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684910"
---
# <a name="supported-code-changes-c"></a>Desteklenen Kod Değişiklikleri (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birçok kod değişikliğini Visual C++ işleme için Düzenle ve devam et. Ancak, bazı değişiklikler program yürütmesi sırasında uygulanamaz. Bu değişiklikleri uygulamak için yürütmeyi durdurmanız ve kodun yeni bir sürümünü oluşturmanız gerekir.  
  
 Visual Studio 'da C++ için Düzenle ve devam et ile çalışma hakkında bilgi için bkz. [Düzenle ve devam et (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) .  
  
## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Desteklenmeyen değişiklikler  

Aşağıdaki C/C++ değişiklikleri hata ayıklama oturumu sırasında uygulanamaz:  
  
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
  
## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Desteklenmeyen senaryolar  
 C/C++ için Düzenle ve devam et aşağıdaki hata ayıklama senaryolarında kullanılamaz:  
  
- /Zo ile derlenen yerel uygulamalarda hata ayıklama [(Iyileştirilmiş hata ayıklamayı geliştirme)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)  
  
- Visual Studio 'nun Visual Studio 2015 güncelleştirme 1 ' den önceki sürümlerinde, Windows Mağazası uygulamaları veya bileşenlerinde hata ayıklama. Visual Studio 2015 güncelleştirme 1 ' den başlayarak, artık `/ZI` anahtar ile derleyici anahtarını desteklediğinden Windows Mağazası C++ uygulamaları ve DirectX uygulamalarında Düzenle ve devam et ' i kullanabilirsiniz  `/bigobj` . Ayrıca, anahtarla derlenen ikili dosyalarla Düzenle ve devam et ' i de kullanabilirsiniz `/FASTLINK` .  
  
- Windows 98 ' de hata ayıklama.  
  
- Karışık mod (Yerel/yönetilen) hata ayıklama.  
  
- JavaScript hata ayıklaması.  
  
- SQL hata ayıklaması.  
  
- Döküm dosyasında hata ayıklama.  
  
- İşlenmeyen özel **durumlar üzerinde çağrı yığınını geri bırakma** seçeneği seçili değilse, işlenmemiş bir özel durumdan sonra kodu düzenleyebilirsiniz.  
  
- **Hata** ayıklama menüsünde **Başlat** ' a tıklayarak uygulamayı çalıştırmak yerine **öğesine iliştirme** kullanarak bir uygulamada hata ayıklama.  
  
- İyileştirilmiş kodda hata ayıklama.  
  
- Derleme hataları nedeniyle yeni bir sürüm derlenemedi sonra kodunuzun eski bir sürümünde hata ayıklama işlemi başarısız oldu.  
  
## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Bağlama sınırlamaları  
  
### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Düzenle ve devam et özelliğini devre dışı bırakan bağlayıcı seçenekleri  
 Aşağıdaki bağlayıcı seçenekleri Düzenle ve devam et devre dışı bırak:  
  
- **/OPT: ref**, **/OPT: ICF**veya **/ıncresetting** ayarları ayarı devre dışı bırakır ve şu uyarıyla devam et:  
  
     BAĞLANTı: Warning LNK4075:/EDıTANDCONTINUE/opt nedeniyle yoksayılıyor  
  
     belirtim  
  
- **/Order**, **/Release**veya **/Force** ayarı, düzenlemeyi devre dışı bırakır ve Bu uyarıyla devam eder:  
  
     BAĞLANTı: Warning LNK4075:/OPTION nedeniyle/ıNCRESAYıLıYOR  
  
     belirtim  
  
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
  
## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_Header_Limitations"></a> Ön derlenmiş üstbilgi sınırlamaları  
 Varsayılan olarak, Düzenle ve devam et, kod değişikliklerinin işlenmesini hızlandırmak için arka planda önceden derlenmiş üst bilgileri yükler ve işler. Önceden derlenmiş üst bilgilerin yüklenmesi, sınırlı RAM 'e sahip bir makinede derlerken bir sorun olabilecek fiziksel belleğin ayrılmasını gerektirir. Hata ayıklarken kullanılabilir fiziksel bellek miktarını öğrenmek için Windows Görev Yöneticisi 'Ni kullanarak bir sorun olup olmadığını belirleyebilirsiniz. Bu miktar önceden derlenmiş başlıklarınızın boyutundan fazlaysa, Düzenle ve devam et bir sorun olmaz. Miktar, önceden derlenmiş başlıklarınızın boyutundan küçükse, Düzenle ' yi ve arka planda önceden derlenmiş üst bilgileri yüklemeye devam et ' i engelleyebilirsiniz.  
  
 **Önceden derlenmiş üstbilgilerin Düzenle ve devam et için arka planda yüklemesini devre dışı bırakmak için**  
  
1. **Hata Ayıkla** menüsünde, **Seçenekler ve ayarlar**' ı seçin.  
  
2. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümü altında, **Düzenle ve devam et** düğümünü seçin.  
  
3. **Önceden derlemeye Izin ver** onay kutusunu temizleyin.  
  
## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_Attribute_Limitations"></a> IDL özniteliği sınırlamaları  
 Düzenle ve devam et, arabirim tanımı (IDL) dosyalarını yeniden oluşturmaz. Bu nedenle, hata ayıklarken IDL özniteliklerinde yapılan değişiklikler yansıtılmayacaktır. IDL özniteliklerinin değişikliklerinin sonucunu görmek için, hata ayıklamayı durdurup uygulamanızı yeniden oluşturmanız gerekir. Düzenle ve devam et, IDL öznitelikleri değiştiyse bir hata veya uyarı oluşturmaz. Daha fazla bilgi için bkz. [IDL öznitelikleri](https://msdn.microsoft.com/library/04c596f4-c97b-4952-8053-316678b1d0b6).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenle ve devam et (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)
