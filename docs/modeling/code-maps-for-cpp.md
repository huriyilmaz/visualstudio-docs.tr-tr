---
title: Kaynak dosyalar ve C++ üstbilgi dosyaları arasındaki bağımlılıklara bakın
ms.date: 05/16/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbba97f47c3ac0686bad15c3a1882e1e9bd85057
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654191"
---
# <a name="code-maps-for-c-projects"></a>Projeler için C++ kod haritaları

Projeler için C++ daha fazla kapsamlı haritalar oluşturmak istiyorsanız, bu projelerde tarama bilgileri derleyici seçeneğini ( **/fr**) ayarlayın. Aksi durumda, bir ileti görüntülenir ve bu seçeneği ayarlamanızı ister. **Tamam**' ı seçerseniz, bu seçeneği yalnızca geçerli harita için ayarlar. İletiyi sonraki tüm haritalar için gizlemeyi seçebilirsiniz.

Visual C++ projeleri içeren bir çözümü açtığınızda, IntelliSense veritabanını güncelleştirmek biraz zaman alabilir. Bu süre boyunca, IntelliSense veritabanı güncelleştirmeyi bitirene kadar üstbilgi ( *. h* veya `#include`) dosyaları için kod haritaları oluşturmeyebilirsiniz. Visual Studio durum çubuğunda güncelleştirme ilerleme durumunu izleyebilirsiniz.

- Çözümünüzdeki tüm kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları görmek için **mimari**  > **Içerme dosyaları grafiğini oluştur**' u seçin.

   ![Yerel kod için bağımlılık grafiği](../modeling/media/dependencygraphgeneral_nativecode.png)

- Şu anda açık olan dosya ile ilgili kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları görmek için kaynak dosyayı veya üstbilgi dosyasını açın. Dosya kısayol menüsünü dosyanın içinde herhangi bir yerde açın. **Ekleme dosyalarının grafiğini oluştur**' ı seçin.

   ![. H dosyası için birinci düzey bağımlılık grafiği](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>C ve C++ Code için kod haritaları sorunlarını giderme

Bu öğeler C ve C++ Code için desteklenmez:

- Temel türler, üst hiyerarşiyi içeren haritalar üzerinde görünmez.

- Çoğu **göster** menü öğesi C ve C++ Code için kullanılamaz.

Bu sorunlar, C ve C++ Code için kod haritaları oluşturduğunuzda oluşabilir:

|**Konuda**|**Olası neden**|**Çözünürlüğüne**|
|-|-|-|
|Kod eşlemesi oluşturulamadı.|Çözümdeki hiçbir proje başarıyla oluşturulmadı.|Oluşan yapı hatalarını giderip eşlemeyi yeniden oluşturun.|
|**Mimari** menüsünden bir kod Haritası oluşturmaya çalıştığınızda Visual Studio yanıt vermemeye çalışır.|Program veritabanı (.pdb) dosyası bozulmuş olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Çözümü yeniden oluşturun ve tekrar deneyin.|
|IntelliSense göz atma veritabanı için belirli ayarlar devre dışı bırakılır.|Visual Studio **seçenekleri** iletişim kutusunda belirli IntelliSense ayarları devre dışı bırakılabilir.|Bunları etkinleştirmek için ayarları etkinleştirin.<br /><br /> Bkz. [Seçenekler, metin düzenleyici, CC++/, gelişmiş](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|**Bilinmeyen Yöntemler** bir yöntem düğümünde görünür.<br /><br /> Yöntemin adı çözümlenemediği için bu sorun oluşur.|İkili dosya temel konum değişikliği tablosuna sahip olmayabilir.|Bağlayıcının **/fixed: No** seçeneğini açın.|
||Program veritabanı (.pdb) dosyası oluşturulmamış olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Bağlayıcının **/Debug** seçeneğini açın.|
||.pdb dosyasını beklenen konumda açamıyor veya bulamıyor.|.pdb dosyasının beklenen konumlarda var olduğundan emin olun.|
||Hata ayıklama bilgileri, .pdb dosyasından çıkarıldı.|Bağlayıcı içinde **/Pdbçıkarıldı** seçeneği kullanıldıysa, bunun yerine tüm. pdb dosyasını dahil edin.|
||Arayan bir işlev değildir ve ikili dosyada bir dönüştürücü ya da veri bölümünde bir işaretçidir.|Çağıran bir dönüştürücü olduğunda, dönüştürücü kullanmaktan kaçınmak için `_declspec(dllimport)` kullanmayı deneyin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılıkları kod eşlemeleriyle eşleyin](../modeling/map-dependencies-across-your-solutions.md)