---
title: C++ kaynak ve üst bilgi dosyaları arasındaki bağımlılıklara bakın
description: C++ projeleri için kod eşlemeleri hakkında bilgi sağlar.
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 572f0daff0d4ca114f3c718f0334eeced32e42fc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157572"
---
# <a name="code-maps-for-c-projects"></a>C++ projeleri için kod eşlemeleri

C++ projeleri için daha eksiksiz eşlemeler oluşturmak için, bu projelerde göz atma bilgileri derleyicisi seçeneğini (**/FR**) ayarlayın. Aksi durumda, bir ileti görüntülenir ve bu seçeneği ayarlamanızı ister. **Tamam'ı seçerseniz,** bu yalnızca geçerli harita için seçeneğini ayarlar. İletiyi sonraki tüm eşlemeler için gizlemeyi seçebilirsiniz.

Visual C++ projeleri içeren bir çözümü açtığınızda, IntelliSense veritabanını güncelleştirmek biraz zaman alabilir. Bu süre boyunca IntelliSense veritabanı güncelleştirilene kadar üst bilgi (*.h veya* ) dosyaları için kod `#include` eşlemeleri oluşturamayabilirsiniz. Visual Studio durum çubuğunda güncelleştirme ilerleme durumunu izleyebilirsiniz.

- Çözümünüzde tüm kaynak dosyalar ve üst bilgi dosyaları arasındaki bağımlılıkları görmek için Mimari Dosyaları Dahil  >  **Graph Oluştur'a tıklayın.**

   ![Yerel kod için bağımlılık grafiği](../modeling/media/dependencygraphgeneral_nativecode.png)

- O anda açık olan dosya ile ilgili kaynak dosyalar ile üst bilgi dosyaları arasındaki bağımlılıkları görmek için kaynak dosyayı veya üst bilgi dosyasını açın. Dosyanın herhangi bir yerinde dosya kısayol menüsünü açın. Dosya **Dahil Graph Oluştur'a seçin.**

   ![.h dosyası için birinci düzey bağımlılık grafiği](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>C ve C++ kodu için kod eşleme sorunlarını giderme

Bu öğeler C ve C++ kodu için desteklenmiyor:

- Temel türler, üst hiyerarşiyi içeren haritalarda görünmez.

- C **ve** C++ kodu için Göster menü öğelerinin çoğu kullanılamaz.

C ve C++ kodu için kod eşlemeleri oluşturma sırasında bu sorunlar oluşabilir:

|**Sorun**|**Olası nedeni**|**Çözünürlük**|
|-|-|-|
|Kod eşlemesi oluşturulamadı.|Çözümdeki hiçbir proje başarıyla oluşturulmadı.|Oluşan derleme hatalarını düzeltin ve haritayı yeniden üretin.|
|Visual Studio menüsünden kod eşlemesi oluşturma denemesi yanıt **vermemeye** başladı.|Program veritabanı (.pdb) dosyası bozulmuş olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Çözümü yeniden oluşturun ve tekrar deneyin.|
|IntelliSense göz atma veritabanı için belirli ayarlar devre dışı bırakılır.|Belirli IntelliSense ayarları, Visual Studio Seçenekleri iletişim **kutusunda devre dışı** bırakılabilir.|Bunları etkinleştirmek için ayarları etkinleştirin.<br /><br /> Bkz. [Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Yöntem **düğümünde** Bilinmeyen Yöntemler iletisi görüntülenir.<br /><br /> Yöntemin adı çözümlenemediği için bu sorun oluşur.|İkili dosya temel konum değişikliği tablosuna sahip olmayabilir.|Bağlantıcıda **/FIXED:NO** seçeneğini açma.|
||Program veritabanı (.pdb) dosyası oluşturulmamış olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|**Bağlantıcıda /DEBUG** seçeneğini açma.|
||.pdb dosyasını beklenen konumda açamıyor veya bulamıyor.|.pdb dosyasının beklenen konumlarda var olduğundan emin olun.|
||Hata ayıklama bilgileri, .pdb dosyasından çıkarıldı.|**Bağlantıcıda /PDBSTRIPPED** seçeneği kullanılmışsa, bunun yerine tam .pdb dosyasını dahil edin.|
||Arayan bir işlev değildir ve ikili dosyada bir dönüştürücü ya da veri bölümünde bir işaretçidir.|Çağıran bir thunk olduğunda, `_declspec(dllimport)` thunk'u önlemek için kullanmayı deneyin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılıkları kod eşlemeleriyle eşleme](../modeling/map-dependencies-across-your-solutions.md)
