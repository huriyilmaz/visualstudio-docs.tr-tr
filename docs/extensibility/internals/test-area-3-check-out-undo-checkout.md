---
title: "Test Alanı 3: Out-Undo'i | Microsoft Docs"
description: Bu kaynak denetimi eklentisi test alanı, Kullanıma Alma ve Kullanıma Almayı Geri Alma komutlarını kullanarak öğeleri sürüm mağazasından düzenlemeyi ve geri almayı kapsar.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 96c5940a97fc799393d7830fa5589183afe33fb0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158794"
---
# <a name="test-area-3-check-outundo-checkout"></a>Test Alanı 3: Kullanıma Alma/Kullanıma Almayı Geri Alma
Bu kaynak denetimi eklentisi test alanı, Kullanıma Alma ve Kullanıma  Almayı Geri Alma komutları aracılığıyla sürüm mağazasındaki öğeleri düzenlemeyi ve **geri almayı** kapsar.

**Kullanıma Alın:** Sürüm mağazasındaki bir öğeyi kullanıma alınmış olarak işaretler, yerel kopyayı okuma/yazma olarak değiştiren.

**Kullanıma Almayı Geri** Al: Sürüm mağazasındaki bir öğeyi iade edildi olarak işaretler, kullanıma alma öncesinde yerel kopyayı durumuna geri alır (seçeneklere bağlı olarak).

## <a name="command-menu-access"></a>Komut Menüsü Erişimi

Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı menü yolları test çalışmalarında kullanılır.

##### <a name="check-out"></a>Kontrol etme:

- **Dosyası,** **Kaynak Denetimi**, **Check Out**.

- **Dosyası,** **Check Out**.

- Kısayol menüsüne **göz atabilirsiniz.**

- Kullanıma Almayı Geri Al: **Dosya,** **Kaynak Denetimi**, Kullanıma Almayı **Geri Al.**

## <a name="common-expected-behavior"></a>Ortak Beklenen Davranış

- Kullanıma alındıktan sonra hedef dosyalar ve/veya klasörler sürüm depolamada kullanıma alınmış olarak işaretlenir.

- Sürüm deposu, satın alma özniteliğini doğru kullanıcıya atfeder.

- Teslim alma tarihi ve saati doğru (kullanıcının ayarlarına göre).

## <a name="test-cases"></a>Test Çalışmaları

Kullanıma Alma/Kullanıma Almayı Geri Alma test alanı için belirli test testleri aşağıda ve listelemektedir.

### <a name="case-3a-check-out"></a>Olay 3a: Göz At

Bu bölüm, check-out komutunun çalışmasına odaklanır.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|İstemci projesini özel (COE) göz at|1. İstemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Yalnızca projenin tamamına göz at (**Dosya**, **Check Out**).|Check-out gerçekleşir.|
|Özel (COE) Bir Dosya Sistemini veya yerel IIS Web projesini göz at|1. Araçlar, **Seçenekler,** **Projeler,** Web Siteleri içinde Dosya **Paylaşımına** Web Sunucusu **Bağlantısını Ayarlar.**<br />2. Web projesi oluşturma.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Yalnızca projenin tamamına göz at (**Dosya,** **Kaynak Denetimi**, **Check Out**).|Check-out gerçekleşir.|
|Çözümdeki çözüm öğelerini (diğer dosyaları işlemeye yeni yöntem) göz at|1. Boş bir çözüm oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözümü kontrol edin.<br />4. Birkaç çözüm öğeleri ekleyin.<br />5. Yeni eklenen tüm öğeleri kontrol edin.<br />6. Birden çok çözüm öğesini seçin.<br />7. Seçili öğeleri (Kısayol Menüsü, Bkz. **) kontrol edin.**|Seçilen dosyalar kullanıma alınmış.|
|Yerel Sürüm'e Göz At (test altındaki eklenti bu özelliği destekliyorsa)|1. Kullanıcı 1: İstemci projesi oluşturun.<br />2. Kullanıcı 1: Çözümü kaynak denetimine ekleyin.<br />3. Kullanıcı 2: Çözümü kaynak denetiminden başka bir konuma açın.<br />4. Kullanıcı 2: Bir dosyayı kontrol edin.<br />5. Kullanıcı 2: Dosyayı değiştirme.<br />6. Kullanıcı 2: Dosyayı iade edin.<br />7. Kullanıcı 1: Dosyanın yerel sürümünü  kontrol edin (Satın Alma iletişim kutusunda Yerel Sürümün gelişmiş sürümünü satın **alma seçeneğini** işaretleyin).|Dosyanın yerel sürümü kullanıma alınmış.<br /><br /> Kullanıcı 2'ye göre değişiklikler Kullanıcı 1 dosyasına uygulanmaz.|

### <a name="case-3b-disconnected-check-out"></a>Olay 3b: Bağlantısı Kesildi

Bağlantısız modda çalışma, doğrudan bir sürüm deposuna bağlı olmayan kullanıcılara bir düzeyde devam eden kaynak denetimi desteği sağlar. Bu, listede yer alan çözüm ve projeler hakkında tüm ilgili bilgileri yerel olarak önbelleğe alma ile yapılır.

Özel denetim işlemleri yalnızca kaynak denetim deposuna bağlıyken oluşabilir. Paylaşılan iade işlemleri, bağlı veya bağlantısı kesilmiş olarak herhangi bir zamanda oluşabilir. Bu nedenle, sürüm deposu bağlantısı kesildiğinde yalnızca **Paylaşılan Check Out** (COS) komutu etkinleştirilir. Bağlantısı kesilmiş **durumdayken, kullanıcı tarafından** yapılan değişiklikleri değiştirmek için eski sürüm alınamay olduğundan Kullanıma Almayı Geri Al devre dışı bırakılmıştır.

Kullanıcı sürüm deposuna yeniden bağlandığında, listede yer alan tüm çözümlerin ve projelerin satın alma durumları eşitlenir. Bu, kullanıcının gerçekleştirilen satın almalar için mağazada gerekli güncelleştirmeleri yapar. Eşitleme gerçekleştiktan sonra kullanıcı normal (bağlı) olarak çalışmaya devam eder.

#### <a name="expected-behavior"></a>Beklenen Davranış

- Sürüm deposu **bağlantısı kesildiğinde Özel** olarak Check Out komutu kullanılamaz.

- Sürüm deposu **bağlantısı kesildiğinde** Kullanıma Almayı Geri Al komutu kullanılamaz.

- **Paylaşılan Check Out** komutu çalışır.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Bağlantısı kesilmiş durumdayken bir dosyayı kontrol edin ve eşitleme için bağlanabilirsiniz|1. Kaynak Denetimi Değiştir iletişim kutusunu (Dosya, Kaynak Denetimi,**Kaynak** Denetimi Değiştir) kullanarak **denetlenen** **bir projenin bağlantısını kesin.**<br />2. Bir dosyayı kontrol edin.<br />3. Uyarı iletişim kutusunda Check Out (bağlantısı kesildi) seçeneğine tıklayın.<br />4. Dosyayı düzenleyin.<br />5. Bağlan Denetimi Değiştir iletişim kutusunu kullanın.<br />6. Düzenlenen dosyanın En Son Sürümünü al.|Ortak Beklenen Davranış|

### <a name="case-3c-query-editquery-save-qeqs"></a>Durum 3c: Sorgu Düzenleme/Sorgu Kaydetme (QEQS)
 Kaynak denetimi altındaki öğeler, kullanıcıların dosyalarını kolayca yönetmelerine yardımcı olmak için düzenlemeler, değişiklikler ve tasarruflar için izlenemez. Denetlenen "iade edilen" bir öğe düzenlendiğinde QEQS, denenen düzenleme girişimini kesir ve kullanıcıdan dosyayı düzenlemek için kullanıma almak istediğini sorar. Araçlar , **Seçenekler ayarlarına** bağlı olarak, kullanıcı düzenlemek için dosyayı denetlemeye zorlar veya bellekte bir kopyayı düzenleyemez ve daha sonra göz atma iznine sahip olabilir.  Kullanıcının Araçlar **,** Seçenekler  ayarı, kullanımdan çıkma iletişim kutusunu görüntülemek ve yalnızca bunu kontrol etmek için ayarlanmazsa, kullanıcı düzenlemesini yaptığı anda dosya mümkün olduğunca otomatik olarak kontrol edilir.

#### <a name="expected-behavior"></a>Beklenen Davranış

- Kullanıma alındıktan sonra hedef dosyalar ve/veya klasörler sürüm depolamada kullanıma alınmış olarak işaretlenir.

- Sürüm deposu, denetimi doğru kullanıcıya öznitelik olarak sağlar.

- Teslim tarihi ve saati doğru (kullanıcının ayarlarına göre).

- Hedef dosyanın veya klasörün yerel kopyası yazılabilir.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|İşaretli metin dosyasını düzenleme|1. Metin dosyası içeren yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. **Araçlar** **,** Seçenekler , **Kaynak** Denetimi , Diskte salt okunurken dosyaların düzenlenmelerine izin **ver'i** işaretlenmemiş olarak ayarlayın.<br />4. **Set Tools**, **Options**, **Source Control**, Prompt for check **out** in when checked in files **are edited combo** box.<br />5. **Set Tools**, **Options**, **Source Control**, Prompt for check **out** in when checked in files are **saved combo** box.<br />6. Metin dosyasını düzenleyicide açın, dosyaya yeni metinler yazın. Bu adım başarılı olursa sonraki adıma geçin.<br />7. **Düzenle iletişim** kutusunda **İptal'e** tıklayın. Bu adım başarılı olursa sonraki adıma geçin.<br />8. **Set Tools**, **Options**, **Source Control**, Allow files to **edited while read-only on disk** to checked.<br />9. Proje dosyasını düzenleyicide açın, dosyaya yeni metin yazın. Bu adım başarılı olursa sonraki adıma geçin.<br />10. **Düzenle iletişim** kutusunda **Düzenle'ye** tıklayın. Bu adım başarılı olursa sonraki adıma geçin.<br />11. Metin dosyasını düzenleyin ve kaydetmeyi deneme.|`Result of step 6:`<br /><br /> Düzenle iletişim kutusu açılır.<br /><br /> `Result of step 7:`<br /><br /> Dosya değiştirilmez.<br /><br /> `Result of step 9:`<br /><br /> Düzenle iletişim kutusu açılır.<br /><br /> `Result of step 10:`<br /><br /> Proje dosyasını bellekte düzenleyebilirsiniz.<br /><br /> `Result of step 11:`<br /><br /> Kaydetmede Kaydet'e göz at iletişim kutusu görüntülenir.|
|Giriş yapılan bir çözüm dosyasını düzenleme|Adımları önceki testte açıklandığı gibi tekrarlayın, ancak metin dosyasını değiştirmek yerine çözüm özelliklerini değiştirerek çözümü değiştirin.|Önceki testle aynı|
|İşaretli bir proje dosyasını düzenleme|Adımları önceki testte açıklandığı gibi tekrarlayın, ancak metin dosyasını değiştirmek yerine proje özelliklerini değiştirerek projeyi değiştirin.|Önceki testle aynı.|

### <a name="case-3d-silent-check-out"></a>Olay 3d: Sessiz Göz At
 Bu alt alan, Kullanıcının Araçları,  Seçenekler, Kaynak Denetimi ayarlarına göre Ele Aç iletişim kutusunun **görünmey** olduğu kullanım **senaryolarını kapsar.**

#### <a name="expected-behavior"></a>Beklenen Davranış

- Kullanıma alındıktan sonra hedef dosyalar ve/veya klasörler sürüm depolamada kullanıma alınmış olarak işaretlenir.

- Sürüm deposu, denetimi doğru kullanıcıya öznitelik olarak sağlar.

- Onay tarihi ve saati doğru (kullanıcının ayarlarına göre).

- Hedef dosyanın veya klasörün yerel kopyası yazılabilir.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Dosya için sessiz iade|1. Düzenleme **sırasında dosyaları otomatik** **olarak** kontrol etmek **için Araçlar,** **Seçenekler, Kaynak Denetimi'ne ayarlayın.**<br />2. Dosya ile yeni bir proje oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Dosyayı kontrol edin.|Dosya sessiz bir şekilde kullanıma alınmış (kullanıcı arabirimi yok).|
|Proje için sessiz iade|1. Düzenleme **sırasında dosyaları otomatik** **olarak** kontrol etmek **için Araçlar,** **Seçenekler, Kaynak Denetimi'ne ayarlayın.**<br />2. Yeni bir proje oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Projeyi kontrol edin.|Dosya sessiz bir şekilde kullanıma alınmış (kullanıcı arabirimi yok).|

### <a name="case-3e-undo-check-out"></a>Durum 3e: Kullanıma Almayı Geri Alma
 **Kullanıma Almayı Geri** Al, bir dosyanın kullanıma alınmış durumunu iptal etmek ve dosyada yapılan değişikliklerin iadesini önlemek için kullanılır.

#### <a name="expected-behavior"></a>Beklenen Davranış

- Varsayılan değer, kullanıcının Yerel Sürüme **Göz At ayarına göredir.** Kullanıcı yerel sürümü kullanıma almayı seçtiyseniz, kullanıma alma işlemini geri almak için varsayılan ayar her zaman kullanıma alınmış sürüme geri dönmektir.

- Geri alma işleminin kabulü  Çözüm Gezgini, etkilenen dosyalar için güncelleştirilmiş olur ve öğe **Bekleyen Iadeler penceresinden** kaldırılır.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Yalnızca kullanıma alınmış tek bir dosyanın Kullanıma Almayı Geri Alma|1. İstemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Bir dosyayı özel olarak kontrol edin.<br />4. Dosyayı değiştirme.<br />5. Kullanıma Almayı Geri Al (**Dosya,** **Kaynak Denetimi**, Kullanıma Almayı **Geri Al**).|Ortak Beklenen Davranış.|
|Paylaşılan kullanıma alınmış tek bir dosyanın kullanıma almayı geri alma|1. İstemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Paylaşılan bir dosyayı kontrol edin.<br />4. Dosyayı değiştirme.<br />5. Kullanıma Almayı Geri Al (**Dosya,** **Kaynak Denetimi**, Kullanıma Almayı **Geri Al**).|Ortak Beklenen Davranış.|
|Projeye dosya ekledikten sonra projenin kullanıma almayı geri alma|1. Yeni bir proje oluşturun ve bunu kaynak denetimine ekleyin.<br />2. Projeyi kontrol edin.<br />3. Projeye bir dosya ekleyin.<br />4. Projenin Kullanıma Almayı Geri Alma.|Eklenen dosya, projeden Çözüm Gezgini.<br /><br /> Project artık kullanıma alınmış değil.|
|Projeden dosya sildikten sonra projenin kullanıma almayı geri alma|1. Yeni bir proje oluşturun ve bunu kaynak denetimine ekleyin.<br />2. Projeyi kontrol edin.<br />3. Projeden bir dosyayı silin.<br />4. Projenin Kullanıma Almayı Geri Alma.|Silinen dosya, proje altında Çözüm Gezgini.<br /><br /> Project artık kullanıma alınmış değil.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
