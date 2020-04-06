---
title: 'Test Alanı 3: Check-Out-Geri Ödeme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5365da1e342df5aea9c1b1cd2ae5a446baea57f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704611"
---
# <a name="test-area-3-check-outundo-checkout"></a>Test Alanı 3: Check Out/Geri Ödeme
Bu kaynak denetimi eklentisi test alanı, **Kullanıma Alma** ve **Geri Ödeme** komutları aracılığıyla sürüm deposundaki öğeleri düzenleme yi ve geri alma yı kapsar.

**Kullanıma Alma**: Sürüm deposundaki bir öğeyi kullanıma alındıkça işaretler, yerel kopyayı okumak/yazmak için değiştirir.

**Geri Ödeme**: Sürüm deposundaki bir öğeyi iade edilmiş olarak işaretler, kullanıma almadan önce yerel kopyayı duruma geri geri döner (seçeneklere bağlı olarak).

## <a name="command-menu-access"></a>Komut Menüsü ne erişim

Test [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servis örneklerinde aşağıdaki tümleşik geliştirme ortamı menü yolları kullanılır.

##### <a name="check-out"></a>Kontrol etme:

- **Dosya**, **Kaynak Denetimi**, **Kullanıma Ala.**

- **Dosya**, Kullanıma **Ala.**

- Kısayol Menüsü, **Kullanıma Al**.

- Geri Ödeme: **Dosya**, **Kaynak Denetimi**, **Geri Ödeme**Geri .

## <a name="common-expected-behavior"></a>Ortak Beklenen Davranış

- Kullanıma alma işleminden sonra, hedef dosya(lar) ve/veya klasör(ler) sürüm deposunda kullanıma alındı olarak işaretlenir.

- Sürüm deposu, ödemeyi doğru kullanıcıya bağlar.

- Ödemenin saati ve tarihi doğrudur (kullanıcının ayarlarına göre).

## <a name="test-cases"></a>Test Çalışmaları

Aşağıda, Ödeme/Geri Ödeme testi alanı için özel test çalışmaları vereme çalışmaları yer almaktadır.

### <a name="case-3a-check-out"></a>Örnek 3a: Kullanıma Son

Bu bölümde kullanıma ait komutun çalışmasına odaklanın.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Bir müşteri projesine Özel (COE) kullanıma bak|1. Bir istemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Tüm projeyi özel olarak kontrol edin (**Dosya**, **Check Out**).|Kullanıma ait olduğu ortaya çıkar.|
|Bir Dosya Sistemi veya yerel IIS Web projesine Özel (COE) kullanıma giriş|1. **Araçlarda**Dosya Paylaşımı için Web Sunucusu Bağlantısını Ayarlayın, **Seçenekler**, **Projeler**, **Web Ayarları**.<br />2. Bir Web projesi oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Tüm projeyi özel olarak kontrol edin (**Dosya**, **Kaynak Denetimi**, Check **Out**).|Kullanıma ait olduğu ortaya çıkar.|
|Çözümdeki çözüm öğelerine göz atın (diğer dosyaları işlemek için yeni yöntem)|1. Boş bir çözüm oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözüme göz atın.<br />4. Birkaç çözüm öğesi ekleyin.<br />5. Yeni eklenen tüm öğeleri iade edin.<br />6. Birden çok çözüm öğesi seçin.<br />7. Seçili öğeleri kontrol edin (Kısayol Menüsü, **Çıkış ).**|Seçili dosyalar kullanıma alınır.|
|Yerel Sürümü Kullanıma Alanın (test altındaki eklenti bu özelliği destekliyorsa)|1. Kullanıcı 1: Bir istemci projesi oluşturun.<br />2. Kullanıcı 1: Çözüm kaynağı denetimine ekleyin.<br />3. Kullanıcı 2: Çözümü kaynak denetiminden başka bir konuma açın.<br />4. Kullanıcı 2: Bir dosyaya göz atın.<br />5. Kullanıcı 2: Dosyayı değiştirin.<br />6. Kullanıcı 2: Dosyayı iade edin.<br />7. Kullanıcı 1: Dosyanın yerel sürümüne göz atın **(Kullanıma Alma** iletişim kutusunda **Yerel Sürüm** gelişmiş seçeneğini işaretleyin).|Dosyanın yerel sürümü kullanıma alındı.<br /><br /> Kullanıcı 2 tarafından yapılan değişiklikler Kullanıcı 1 dosyasına uygulanmaz.|

### <a name="case-3b-disconnected-check-out"></a>Örnek 3b: Bağlantısı kesilen Kullanıma Al

Bağlantısı kesilen modda çalışmak, kullanıcılara doğrudan bir sürüm deposuna bağlı değilken bir miktar sürekli kaynak denetimi desteği sağlar. Bu, kayıtlı çözüm ve projeler le ilgili tüm ilgili bilgilerin yerel olarak önbelleğe alınmasıyla yapılır.

Özel kullanıma para verme işlemleri yalnızca kaynak denetim deposuna bağlıyken oluşabilir. Paylaşılan kullanıma alma işlemleri, bağlı veya bağlantısı kesilen herhangi bir zamanda oluşabilir. Bu nedenle, sürüm deposundan bağlantısı kesildiğinde, yalnızca **Kullanıma Alma Paylaşılan** (COS) komutu etkinleştirilir. Bağlantısı kesilse de, eski sürüm kullanıcı tarafından yapılan değişiklikleri değiştirmek için alınamadığından, **Geri Ödeme'yi** Geri Al devre dışı bırakılır.

Kullanıcı sürüm deposuna yeniden bağlandığında, kayıtlı tüm çözümlerin ve projelerin ödeme durumları eşitlenir. Bu, kullanıcının gerçekleştirdiği ödeme ler için mağazaya gerekli güncelleştirmeleri yapar. Eşitleme gerçekleştikten sonra, kullanıcı normal (bağlı) olarak çalışmaya devam edebiliyor.

#### <a name="expected-behavior"></a>Beklenen Davranış

- Sürüm deposundan bağlantısı kesilirken **Yalnızca Kullanıma Alma** komutunu kullanamazsınız.

- Sürüm deposundan bağlantısı kesilirken **Ödeme Yi geri alma** komutunu kullanamaz.

- **Paylaşılan Kullanıma Alma** komutu çalışır.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Bağlantısı kesilirken, bir dosyayı kullanıma çekin ve ardından eşitleme için bağlanın|1. Kaynak Denetimi Değiştir iletişim kutusunu kullanarak denetlenen projeyi kesme (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimini Değiştir**).<br />2. Bir dosyayı kontrol edin.<br />3. Uyarı iletişim kutusunda Kullanıma (bağlantısı kesilmiş) seçeneğini tıklatın.<br />4. Dosyayı edin.<br />5. Kaynak Denetimini Değiştir iletişim kutusunu kullanarak bağlanın.<br />6. Düzenlenen dosyanın En Son Sürümünü Alın.|Ortak Beklenen Davranış|

### <a name="case-3c-query-editquery-save-qeqs"></a>Büyük/Küçük Harf 3c: Sorgu Lat/Sorgu Kaydet (QEQS)
 Kaynak denetimi altındaki öğeler, kullanıcıların dosyalarını kolayca yönetmelerine yardımcı olmak için yapılan denetimler, değişiklikler ve kaydedilebilir. "Iade edilen" denetlenen bir öğe düzenlendiğinde, QEQS düzenleme girişimini yakalar ve kullanıcıya dosyayı düzenlemek için kullanıma almak isteyip istemediğini sorar. **Araçlar**, **Seçenekler** ayarlarına bağlı olarak, kullanıcı ya düzenlemek için dosyayı kullanıma almak zorunda kalır ya da bir kopyasını bellekte düzenleyip daha sonra kullanıma almalarına izin verilebilir. Kullanıcının **Araçlar**, **Seçenekler** ayarı kullanıma al iletişim kutusunu görüntülemek ve yalnızca kullanıma almak için ayarlanmıyorsa, kullanıcı yaptığı edinde, dosya mümkün olduğunda otomatik olarak kullanıma sunar.

#### <a name="expected-behavior"></a>Beklenen Davranış

- Kullanıma alma işleminden sonra, hedef dosya(lar) ve/veya klasör(ler) sürüm deposunda kullanıma alındı olarak işaretlenir.

- Sürüm deposu, kullanıma alma özelliğini doğru kullanıcıya bağlar.

- Kullanıma son unun saati ve tarihi doğrudur (kullanıcının ayarlarına göre).

- Hedef dosyanın veya klasörün yerel kopyası yazılabilir.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Denetlenen metin dosyalarını edin|1. Metin dosyası içeren yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. **Araçları**Ayarla , **Seçenekler**, **Kaynak Denetimi**, **Yalnızca diskte okunurken dosyaların denetlenmeden düzenlenmesine izin verin.**<br />4. **Set Araçları**, **Seçenekler**, **Kaynak Denetimi**, Dosyalarda kontrol edildiğinde kullanıma almak için **komut istemi** açılan kutu **düzenlenir.**<br />5. **Set Araçları**, **Seçenekler**, **Kaynak Denetimi**, Dosyalarda kontrol edildiğinde kullanıma almak için **komut istemi** açılan kutu **kaydedilir.**<br />6. Editörde metin dosyasını açın, dosyaya yeni metin yazmaya çalışın. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />7. Yap iletişim kutusunu Yap'a **Kaydet** kutusunda **İptal** Et'i tıklatın. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />8. **Araçları**Ayarla , **Seçenekler**, **Kaynak Denetimi**, Yalnızca okundu diskte denetlenirken **dosyaların düzenlenmesine izin verin.**<br />9. Proje dosyasını düzenleyicide açın, dosyaya yeni metin yazmaya çalışın. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />10. Yap iletişim kutusunu Yap'a **Gözat'ta** **Edit'i** tıklatın. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />11. Metin dosyasını edin ve kaydetmeye çalışın.|`Result of step 6:`<br /><br /> Edit iletişim kutusu için kullanıma açın.<br /><br /> `Result of step 7:`<br /><br /> Dosya değişmedi.<br /><br /> `Result of step 9:`<br /><br /> Edit iletişim kutusu için kullanıma açın.<br /><br /> `Result of step 10:`<br /><br /> Proje dosyasını bellekte atabilirsiniz.<br /><br /> `Result of step 11:`<br /><br /> Kaydet'te kaydet iletişim kutusunda Kullanıma Alın kutusu görüntülenir.|
|Denetlenen bir çözüm dosyanı edin|Önceki testte açıklandığı gibi adımları yineleyin, ancak metin dosyasını değiştirmek yerine çözüm özelliklerini değiştirerek çözümü değiştirin.|Önceki testle aynı|
|Denetlenen proje dosyalarını düzenlemesi|Önceki testte açıklandığı gibi adımları yineleyin, ancak metin dosyasını değiştirmek yerine proje özelliklerini değiştirerek projeyi değiştirin.|Önceki testle aynı.|

### <a name="case-3d-silent-check-out"></a>Örnek 3d: Sessiz Check Out
 Bu alt alan, **Kullanıma Alma** iletişim kutusunun kullanıcının **Araçları,** **Seçenekleri**, Kaynak Denetimi ayarları başına görünmediği kullanıma alma **senaryolarını**kapsar.

#### <a name="expected-behavior"></a>Beklenen Davranış

- Kullanıma alma işleminden sonra, hedef dosya(lar) ve/veya klasör(ler) sürüm deposunda kullanıma alındı olarak işaretlenir.

- Sürüm deposu, kullanıma alma özelliğini doğru kullanıcıya bağlar.

- Kullanıma son unun saati ve tarihi doğrudur (kullanıcının ayarlarına göre).

- Hedef dosyanın veya klasörün yerel kopyası yazılabilir.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Bir dosya için sessiz ödeme|1. **Set Araçları**, **Seçenekler**, **Kaynak Denetimi** otomatik **olarak dosyalarını edit**.<br />2. Dosyaile yeni bir proje oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Dosyaya göz atın.|Dosya sessizce kullanıma edilir (ui yok).|
|Bir proje için sessiz ödeme|1. **Set Araçları**, **Seçenekler**, **Kaynak Denetimi** otomatik **olarak dosyalarını edit**.<br />2. Yeni bir proje oluşturun.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Projeye göz atın.|Dosya sessizce kullanıma edilir (ui yok).|

### <a name="case-3e-undo-check-out"></a>Örnek 3e: Check Out'u Geri Ala
 **Geri Ödeme Çıkış,** bir dosyanın kullanıma alındı durumunu iptal etmek ve dosyada yapılan değişiklikleri iade etmekten kaçınmak için kullanılır.

#### <a name="expected-behavior"></a>Beklenen Davranış

- Varsayılan değer, kullanıcının **Yerel Sürüm Kullanıma ayarına** dayanır. Kullanıcı yerel sürüme kullanıma son verdiyse, geri alma ödemesi için varsayılan değer her zaman kullanıma verilen sürüme geri dönmektir.

- Geri alma kabul edildikten sonra, **Çözüm Gezgini'ndeki** simgeler etkilenen dosyalar için güncelleştirilir ve öğe **Bekleyen Denetimler** penceresinden kaldırılır.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Yalnızca kullanıma verilen tek bir dosyanın Ödemesini Geri Al|1. Bir istemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Yalnızca bir dosyaya göz atın.<br />4. Dosyayı değiştirin.<br />5. Geri Ödeme (**Dosya**, **Kaynak Denetimi**, Geri **Ödeme ).**|Ortak Beklenen Davranış.|
|Kullanıma Al'ın Kullanıma Al|1. Bir istemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Paylaşılan bir dosyaya göz atın.<br />4. Dosyayı değiştirin.<br />5. Geri Ödeme (**Dosya**, **Kaynak Denetimi**, Geri **Ödeme ).**|Ortak Beklenen Davranış.|
|Projeye dosya(lar) ekledikten sonra projenin Ödemesini Geri Ala|1. Yeni bir proje oluşturun ve kaynak denetimine ekleyin.<br />2. Projeye göz atın.<br />3. Projeye bir dosya ekleyin.<br />4. Projenin Ödemesini Geri Ala.|Eklenen dosya Çözüm Gezgini'nde projeden kaldırılır.<br /><br /> Proje artık kullanıma alındı.|
|Dosya(lar) projeden silen projeden ödemeyi geri alma|1. Yeni bir proje oluşturun ve kaynak denetimine ekleyin.<br />2. Projeye göz atın.<br />3. Projeden bir dosya silin.<br />4. Projenin Ödemesini Geri Ala.|Silinen dosya Çözüm Gezgini'nde proje altında görünür.<br /><br /> Proje artık kullanıma alındı.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
