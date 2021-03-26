---
title: 'Test alanı 3: Out-Undo kullanıma almayı denetle | Microsoft Docs'
description: Bu kaynak denetimi eklentisi test alanı, kullanıma alma ve geri alma komutlarını kullanarak sürüm deposundaki öğeleri düzenlemenizi ve geri döndürmeyi içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c184aeb1b5a43e54bc00d5694ddee7711a815593
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078636"
---
# <a name="test-area-3-check-outundo-checkout"></a>Test Alanı 3: Kullanıma Alma/Kullanıma Almayı Geri Alma
Bu kaynak denetimi eklentisi test alanı **, kullanıma alma ve** **geri alma** komutlarını kullanarak sürüm deposundan öğeleri düzenlemenizi ve geri döndürmeyi içerir.

Kullanıma **alma**: Sürüm deposundaki bir öğeyi kullanıma alınmış olarak işaretler, Yerel kopyayı okuma/yazma olarak değiştirir.

**Kullanıma almayı geri al**: Sürüm deposundaki bir öğeyi iade edildi olarak işaretler, kullanıma almadan önce yerel kopyayı duruma döndürür (seçeneklere bağlı olarak).

## <a name="command-menu-access"></a>Komut menüsü erişimi

Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı menü yolları test durumlarında kullanılır.

##### <a name="check-out"></a>Kontrol etme:

- **Dosya**, **kaynak denetimi**, kullanıma **alma**.

- **Dosya**, kullanıma **alma**.

- Kısayol menüsü, kullanıma **alma**.

- Kullanıma almayı geri al: **Dosya**, **kaynak denetimi**, **kullanıma almayı geri alma**.

## <a name="common-expected-behavior"></a>Yaygın beklenen davranış

- Kullanıma alma işleminden sonra, hedef dosya ve/veya klasörler sürüm deposunda kullanıma alınmış olarak işaretlenir.

- Sürüm deposu, kullanıma alma işlemini doğru kullanıcıya göre öznitelikler.

- Kullanıma almanın saat ve saati doğru (kullanıcının ayarlarına göre).

## <a name="test-cases"></a>Test Çalışmaları

Kullanıma alma/geri alma test alanı için belirli test çalışmaları aşağıda verilmiştir.

### <a name="case-3a-check-out"></a>Case 3A: kullanıma alma

Bu bölüm, kullanıma alma komutunun işlemine odaklanır.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Bir istemci projesi için özel (COE) özel kullanıma alma|1. bir istemci projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. tüm projeyi özel olarak inceleyin (**Dosya**, kullanıma **alma**).|Kullanıma alma işlemi gerçekleşir.|
|Dosya sistemine veya yerel IIS Web projesine özel olarak (COE) göz atın|1. **Araçlar**, **Seçenekler**, **Projeler**, **Web ayarları**'ndaki dosya paylaşımıyla Web sunucusu bağlantısını ayarlayın.<br />2. bir Web projesi oluşturun.<br />3. çözümü kaynak denetimine ekleyin.<br />4. tüm projeyi özel olarak inceleyin (**Dosya**, **kaynak denetimi**, kullanıma **alma**).|Kullanıma alma işlemi gerçekleşir.|
|Çözümdeki çözüm öğelerine göz atın (diğer dosyaları işlemek için yeni yöntem)|1. boş bir çözüm oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözüme göz atın.<br />4. birkaç çözüm öğesi ekleyin.<br />5. yeni eklenen tüm öğeleri iade edin.<br />6. birden çok çözüm öğesi seçin.<br />7. seçili öğelere (kısayol menüsü, kullanıma **alma**) göz atın.|Seçilen dosyalar kullanıma alındı.|
|Yerel sürümü kullanıma alma (test altındaki eklenti bu özelliği destekliyorsa)|1. Kullanıcı 1: bir istemci projesi oluşturun.<br />2. Kullanıcı 1: çözümü kaynak denetimine ekleyin.<br />3. Kullanıcı 2: çözümü kaynak denetiminden başka bir konuma açın.<br />4. Kullanıcı 2: bir dosyaya göz atın.<br />5. Kullanıcı 2: dosyayı değiştirin.<br />6. Kullanıcı 2: dosyayı Iade edin.<br />7. Kullanıcı 1: dosyanın yerel sürümünü Inceleyin **(kullanıma alma iletişim kutusunda** **yerel sürümü kullanıma** alma Gelişmiş seçeneğini işaretleyin).|Dosyanın yerel sürümü kullanıma alındı.<br /><br /> Kullanıcı 2 ' ye göre değişiklikler Kullanıcı 1 dosyasına uygulanmaz.|

### <a name="case-3b-disconnected-check-out"></a>Durum 3B: bağlantısı kesilen kullanıma alma

Bağlantısı kesik modda çalışan, bir sürüm deposuna doğrudan eklenmedikleri zaman, kullanıcıların bazı devam eden kaynak denetimi desteğine sahip olmasına olanak sağlar. Bu, kayıtlı çözüm ve projelerle ilgili tüm ilgili bilgileri yerel olarak önbelleğe alarak yapılır.

Dışlamalı kullanıma alma işlemleri yalnızca kaynak denetim deposuna bağlıyken gerçekleşebilir. Paylaşılan kullanıma alma işlemleri, bağlı veya bağlantısı kesik olsun, herhangi bir zamanda gerçekleşebilir. Bu nedenle, sürüm deposu bağlantısı kesildiğinde yalnızca **paylaşılan kullanıma alma** (cos) komutu etkin olur. Bağlantısı kesildiğinde, Kullanıcı tarafından yapılan değişiklikleri değiştirmek için eski sürüm alınamadığından **kullanıma** alma işlemi devre dışı bırakıldı.

Kullanıcı sürüm deposuna yeniden bağlandığında, tüm kayıtlı çözümlerin ve projelerin teslim alma durumları eşitlenir. Bu, kullanıcının gerçekleştirdiği kullanıma alma işlemleri için depoya gereken güncelleştirmeleri yapar. Eşitleme yapıldıktan sonra, Kullanıcı normal (bağlı) olarak çalışmaya devam edebilir.

#### <a name="expected-behavior"></a>Beklenen davranış

- Sürüm deposu bağlantısı kesildiğinde özel olarak kullanıma **alma** komutu kullanılamaz.

- Sürüm deposu bağlantısı kesildiğinde **geri al kullanıma** alma komutu kullanılamaz.

- **Paylaşılan kullanıma alma** komutu işe yarar.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Bağlantı kesildiğinde, bir dosyaya göz atın ve eşitleme için bağlanın|1. kaynak denetimini Değiştir iletişim kutusunu (**Dosya**, **kaynak denetimi**, **kaynak denetimini Değiştir**) kullanarak denetimli bir projenin bağlantısını kesin.<br />2. bir dosyayı denetleyin.<br />3. uyarı iletişim kutusunda kullanıma alma (bağlantısı kesildi) seçeneğine tıklayın.<br />4. dosyayı düzenleyin.<br />5. kaynak denetimini Değiştir iletişim kutusunu kullanarak bağlanın.<br />6. düzenlenmiş dosyanın en son sürümünü alın.|Yaygın beklenen davranış|

### <a name="case-3c-query-editquery-save-qeqs"></a>Durum 3c: sorgu düzenleme/sorgu kaydetme (QEQS)
 Kaynak denetimindeki öğeler, kullanıcıların dosyalarını kolayca yönetmesine yardımcı olmak için düzenlemeler, değişiklikler ve kaydetme işlemleri için izlenir. "İade edildi" olan denetimli bir öğe düzenlendiğinde, QEQS denenen düzenlemeyi karşılar ve dosyayı düzenlemek için dosyayı kullanıma almak isterse kullanıcıyı ister. **Araçlara**, **seçenek** ayarlarına bağlı olarak, Kullanıcı, düzenlemek için dosyayı kullanıma alabilir veya bellekte bir kopyayı düzenleme ve daha sonra kullanıma alma izni verilebilir. Kullanıcının **araçları**, **Seçenekler** ayarı kullanıma alma iletişim kutusunu göstermek ve yalnızca kullanıma almak için ayarlanmamışsa, Kullanıcı düzenleme yaptığında dosya, mümkün olduğunda otomatik olarak kontrol eder.

#### <a name="expected-behavior"></a>Beklenen davranış

- Kullanıma alma işleminden sonra, hedef dosya ve/veya klasörler sürüm deposunda kullanıma alınmış olarak işaretlenir.

- Sürüm deposu, doğru kullanıcıya kullanıma alma özniteliklerini düzeltir.

- Kullanıma alma saatinin saati ve tarihi doğrudur (kullanıcının ayarlarına göre).

- Hedef dosyanın veya klasörün yerel kopyası yazılabilir.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|İade edilen metin dosyasını Düzenle|1. bir metin dosyası içeren yeni bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. **Araçlar**, **Seçenekler**, **kaynak denetimi**, **diskte salt okuma açıkken dosyaların düzenlenmesine izin ver** seçeneğini işaretsiz olarak ayarlayın.<br />4. **Araçlar**, **Seçenekler**, **kaynak denetimi**, **İade edilen dosyalarda** kullanıma **alma için sor** Birleşik giriş kutusunu ayarlayın.<br />5. **Araçlar**, **Seçenekler**, **kaynak denetimi**, iade **edilmiş dosyalar kaydedildiğinde** açılan kutuda kullanıma **alma isteminde bulun** .<br />6. metin dosyasını düzenleyicide açın, dosyaya yeni metin yazma girişiminde bulunuldu. Bu adım başarılı olursa sonraki adımla devam edin.<br />7. **düzenleme için kullanıma alma** Iletişim kutusunda **iptal 'e** tıklayın. Bu adım başarılı olursa sonraki adımla devam edin.<br />8. **Araçlar**, **Seçenekler**, **kaynak denetimi**, **diskteki salt okuma sırasında dosyaların düzenlenmesine izin ver** seçeneğini belirleyin.<br />9. proje dosyasını düzenleyicide açın, dosyaya yeni metin yazma girişimi yapın. Bu adım başarılı olursa sonraki adımla devam edin.<br />10. **düzenleme için kullanıma alma** Iletişim kutusunda **Düzenle** ' ye tıklayın. Bu adım başarılı olursa sonraki adımla devam edin.<br />11. metin dosyasını düzenleyin ve kaydetmeyi deneyin.|`Result of step 6:`<br /><br /> Düzenleme için kullanıma alma iletişim kutusu görüntülenir.<br /><br /> `Result of step 7:`<br /><br /> Dosya değiştirilmez.<br /><br /> `Result of step 9:`<br /><br /> Düzenleme için kullanıma alma iletişim kutusu görüntülenir.<br /><br /> `Result of step 10:`<br /><br /> Proje dosyasını bellekte düzenleyebilirsiniz.<br /><br /> `Result of step 11:`<br /><br /> Kaydetme sırasında, kaydetme sırasında kullanıma alma iletişim kutusu görüntülenir.|
|İade edilen bir çözüm dosyasını düzenleme|Önceki testte açıklanan adımları yineleyin, ancak bir metin dosyasını değiştirmek yerine çözüm özelliklerini değiştirerek çözümü değiştirin.|Önceki testle aynı|
|İade edilmiş bir proje dosyasını düzenleme|Önceki testte açıklanan adımları yineleyin, ancak bir metin dosyasını değiştirmek yerine proje özelliklerini değiştirerek projeyi değiştirin.|Önceki testle aynı.|

### <a name="case-3d-silent-check-out"></a>Durum 3B: sessiz kullanıma alma
 Bu alt alan, kullanıma **alma** iletişim kutusunun Kullanıcı **araçları**, **Seçenekler**, **kaynak denetimi ayarları** başına görünmediğinden, kullanıma alma senaryolarını ele alır.

#### <a name="expected-behavior"></a>Beklenen davranış

- Kullanıma alma işleminden sonra, hedef dosya ve/veya klasörler sürüm deposunda kullanıma alınmış olarak işaretlenir.

- Sürüm deposu, doğru kullanıcıya kullanıma alma özniteliklerini düzeltir.

- Kullanıma alma işlemi için saat ve Tarih doğrudur (kullanıcının ayarlarına göre).

- Hedef dosyanın veya klasörün yerel kopyası yazılabilir.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Dosya için sessiz kullanıma alma|1. **dosyaları düzenleme sırasında otomatik olarak kullanıma** almak için **Araçlar**, **Seçenekler**, **kaynak denetimi** ayarlayın.<br />2. bir dosya ile yeni bir proje oluşturun.<br />3. çözümü kaynak denetimine ekleyin.<br />4. dosyaya göz atın.|Dosya sessizce kullanıma alındı (Kullanıcı arabirimi yok).|
|Bir proje için sessiz kullanıma alma|1. **dosyaları düzenleme sırasında otomatik olarak kullanıma** almak için **Araçlar**, **Seçenekler**, **kaynak denetimi** ayarlayın.<br />2. yeni bir proje oluşturun.<br />3. çözümü kaynak denetimine ekleyin.<br />4. projeye göz atın.|Dosya sessizce kullanıma alındı (Kullanıcı arabirimi yok).|

### <a name="case-3e-undo-check-out"></a>Durum 3e: kullanıma almayı geri alma
 Kullanıma **almayı geri alma** , bir dosyanın kullanıma alınmış durumunu iptal etmek ve dosyada yapılan değişiklikleri iade etmeyi önlemek için kullanılır.

#### <a name="expected-behavior"></a>Beklenen davranış

- Varsayılan değer, kullanıcının **yerel sürümü kullanıma alma** ayarına bağlıdır. Kullanıcı yerel sürümü kullanıma almayı seçtiyseniz, geri alma için varsayılan değer her zaman kullanıma alınan sürüme döndürülür.

- Geri alma işlemini kabul etmenizden sonra, **Çözüm Gezgini** simgeler etkilenen dosyalar için güncellenir ve öğe **bekleyen checkins** penceresinden kaldırılır.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Özel olarak kullanıma alınan tek bir dosyayı kullanıma almayı geri alma|1. bir istemci projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. özel olarak bir dosyaya göz atın.<br />4. dosyayı değiştirin.<br />5. kullanıma almayı geri alın (**Dosya**, **kaynak denetimi**, **kullanıma almayı geri al**).|Ortak beklenen davranış.|
|Paylaşılan kullanıma alınan tek bir dosyayı kullanıma almayı geri alma|1. bir istemci projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. paylaşılan bir dosyaya göz atın.<br />4. dosyayı değiştirin.<br />5. kullanıma almayı geri alın (**Dosya**, **kaynak denetimi**, **kullanıma almayı geri al**).|Ortak beklenen davranış.|
|Dosya (ler) projeye eklendikten sonra bir projeyi kullanıma almayı geri al|1. yeni bir proje oluşturun ve kaynak denetimine ekleyin.<br />2. projeye göz atın.<br />3. projeye bir dosya ekleyin.<br />4. projeyi kullanıma almayı geri alın.|Eklenen dosya Çözüm Gezgini projeden kaldırılır.<br /><br /> Proje artık kullanıma alınmamış.|
|Dosyaları projeden sildikten sonra bir projeyi kullanıma almayı geri al|1. yeni bir proje oluşturun ve kaynak denetimine ekleyin.<br />2. projeye göz atın.<br />3. bir dosyayı projeden silin.<br />4. projeyi kullanıma almayı geri alın.|Silinen dosya Çözüm Gezgini içindeki projenin altında görüntülenir.<br /><br /> Proje artık kullanıma alınmamış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
