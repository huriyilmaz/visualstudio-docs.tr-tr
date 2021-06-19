---
title: C++ kaynak ve üstbilgi dosyaları arasındaki bağımlılıklara bakın
description: C++ projeleri için kod eşlemeleri hakkında bilgi sağlar.
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93ac1f7364e23ef9ed2b44ecd1c536a7ab2b3d40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389676"
---
# <a name="code-maps-for-c-projects"></a>C++ projeleri için kod haritaları

C++ projeleri için daha fazla eşleme oluşturmak istiyorsanız, bu projelerde tarama bilgileri derleyici seçeneğini (**/fr**) ayarlayın. Aksi durumda, bir ileti görüntülenir ve bu seçeneği ayarlamanızı ister. **Tamam**' ı seçerseniz, bu seçeneği yalnızca geçerli harita için ayarlar. İletiyi sonraki tüm haritalar için gizlemeyi seçebilirsiniz.

Visual C++ projeleri içeren bir çözümü açtığınızda, IntelliSense veritabanını güncelleştirmek biraz zaman alabilir. Bu süre boyunca, IntelliSense veritabanı güncelleştirmeyi bitirene kadar üstbilgi (*. h* veya) dosyaları için kod haritaları oluşturmeyebilirsiniz `#include` . Visual Studio durum çubuğunda güncelleştirme ilerleme durumunu izleyebilirsiniz.

- Çözümünüzdeki tüm kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları görmek için,   >  **içerme dosyaları** için mimari oluştur ' u seçin.

   ![Yerel kod için bağımlılık grafiği](../modeling/media/dependencygraphgeneral_nativecode.png)

- Şu anda açık olan dosya ile ilgili kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları görmek için kaynak dosyayı veya üstbilgi dosyasını açın. Dosya kısayol menüsünü dosyanın içinde herhangi bir yerde açın. **Ekleme dosyalarının grafiğini oluştur**' ı seçin.

   ![. H dosyası için birinci düzey bağımlılık grafiği](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>C ve C++ kodu için kod haritaları sorunlarını giderme

Bu öğeler C ve C++ kodu için desteklenmez:

- Temel türler, üst hiyerarşiyi içeren haritalar üzerinde görünmez.

- Çoğu **göster** menü öğesi C ve C++ kodu için kullanılamaz.

Bu sorunlar, C ve C++ kodu için kod eşlemeleri oluşturduğunuzda oluşabilir:

|**Sorun**|**Olası nedeni**|**Çözünürlük**|
|-|-|-|
|Kod eşlemesi oluşturulamadı.|Çözümdeki hiçbir proje başarıyla oluşturulmadı.|Oluşan yapı hatalarını giderip eşlemeyi yeniden oluşturun.|
|**Mimari** menüsünden bir kod Haritası oluşturmaya çalıştığınızda Visual Studio yanıt vermemeye çalışır.|Program veritabanı (.pdb) dosyası bozulmuş olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Çözümü yeniden oluşturun ve tekrar deneyin.|
|IntelliSense göz atma veritabanı için belirli ayarlar devre dışı bırakılır.|Visual Studio **seçenekleri** iletişim kutusunda belirli IntelliSense ayarları devre dışı bırakılabilir.|Bunları etkinleştirmek için ayarları etkinleştirin.<br /><br /> Bkz. [Seçenekler, metin düzenleyici, C/C++, gelişmiş](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|**Bilinmeyen Yöntemler** bir yöntem düğümünde görünür.<br /><br /> Yöntemin adı çözümlenemediği için bu sorun oluşur.|İkili dosya temel konum değişikliği tablosuna sahip olmayabilir.|Bağlayıcının **/fixed: No** seçeneğini açın.|
||Program veritabanı (.pdb) dosyası oluşturulmamış olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Bağlayıcının **/Debug** seçeneğini açın.|
||.pdb dosyasını beklenen konumda açamıyor veya bulamıyor.|.pdb dosyasının beklenen konumlarda var olduğundan emin olun.|
||Hata ayıklama bilgileri, .pdb dosyasından çıkarıldı.|Bağlayıcı içinde **/Pdbçıkarıldı** seçeneği kullanıldıysa, bunun yerine tüm. pdb dosyasını dahil edin.|
||Arayan bir işlev değildir ve ikili dosyada bir dönüştürücü ya da veri bölümünde bir işaretçidir.|Çağıran bir dönüştürücü olduğunda, `_declspec(dllimport)` dönüştürücü kullanmaktan kaçınmak için kullanmayı deneyin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılıkları kod eşlemeleriyle eşleyin](../modeling/map-dependencies-across-your-solutions.md)
