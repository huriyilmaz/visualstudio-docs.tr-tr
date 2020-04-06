---
title: 'Test Alanı 5: Kaynak Denetimini Değiştir | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c0df31fbecd532e6a5f7f317730cd995cd8225
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704520"
---
# <a name="test-area-5-change-source-control"></a>Test Alanı 5: Kaynak Denetimini Değiştirme
Bu kaynak denetimi eklentisi test alanı, **Kaynak Denetimini Değiştir** komutu aracılığıyla kaynak denetiminin değiştirilmesini kapsar.

 **Kaynak Denetimini Değiştir** komutu kullanıcı için dört temel işlev sağlar:

- **Bağlamak:**

   Bir kullanıcının çözüm/proje ile sürüm deposu arasında kaynak denetimi bağlantısı kurmasına veya yeniden kurmasına olanak tanır.

- **Unbind:**

   Bir proje/çözümü bağlantı başına kaynak denetiminden kaldırır.

- **Bağlan/Kes:**

  Alan 3'te kapsanan kontrollü çözümün bağlı veya çevrimdışı durumunu geçişler. Daha fazla bilgi için test [alanı 3: Check Out/Geri](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)Ödeme' ye bakın.

## <a name="command-menu-access"></a>Komut Menüsü ne erişim
 Test [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servis lerinde aşağıdaki tümleşik geliştirme ortamı menüsü yolu kullanılır.

 Kaynak Denetimini Değiştir:**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimini Değiştir**.

## <a name="test-cases"></a>Test Çalışmaları
 Kaynak **Denetimi komutu** test alanı için özel test çalışmaları aşağıda veda edilebistir.

### <a name="case-5a-bind"></a>Örnek 5a: Bağlama
 Bind, kullanıcının seçili projelere ve çözümlere kaynak kodu denetim bilgileri eklemesine olanak tanır. Kullanıcıdan genellikle kaynak denetiminde bunların eklendiği bir projeyi tanımlaması istenir. Kullanıcı bu işlemin bir parçası olarak kaynak denetiminde yeni bir proje oluşturamaz (Kaynak Denetimine Ekle ile kontrast).

| Eylem | Test Adımları | Doğrulaması Beklenen Sonuçlar |
| - | - | - |
| Boş konuma bağlama | 1. Bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Aç **Kaynak Denetimi** iletişim kutusunu aç (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimini Değiştir**).<br />4. **Unbind'e**tıklayın.<br />5. Görünürse uyarı iletişim kutusunu kabul edin.<br />6. Tüm öğeleri seçin.<br />7. **Bind'i**tıklatın.<br />8. Kaynak denetim deposundaki boş bir konuma göz atın.<br />9. **Kaynak Denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />10. Onay iletişim kutusunda **bu bağlamalarla Devam** et'i tıklatın.<br />11. Görünürse uyarı iletişim kutusunda **Tamam'ı** tıklatın.<br />12. Her şeyi kontrol edin. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />13. Kaynak denetiminden yeni bir konuma çözümü açın. | `Result from Step 12:`<br /><br /> Çözüm ve proje, sürüm deposundaki yeni hedefe bağlıdır ve yazılır.<br /><br /> Çözüm ve proje dosyaları iade edilir.<br /><br /> Sürüm deposu proje hiyerarşisi, diskteki projenin klasör hiyerarşisi ile eşleşir.<br /><br /> `Result from Step 13:`<br /><br /> Tüm proje öğeleri indirilir. |
| İstemci ile eşitlenmiş konuma bağlama | 1. Bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Sürüm deposunda çözümün ve projenin bir kopyasını oluşturun [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](Kullanıyorsanız Paylaş ve Şube).<br />4. Aç **Kaynak Denetimi** iletişim kutusunu aç (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimini Değiştir**).<br />5. Unbind Tüm.<br />6. **Kaynak Denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />7. **Kaynak Denetimi Değiştir** iletişim kutusunu yeniden açın.<br />8. Tümünü seçin.<br />9. **Bind'i**tıklatın.<br />10. Çözümün ve projenin dallanmış konumuna göz atın (adım 3'ten itibaren)<br />11. **Kaynak Denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />12. Tüm öğeler için en son özyinelemeli alın. | Dosya içeriği aldıktan sonra almak önce aynıdır. |
| İstemci ile eşitlenmemiş konuma bağlama | 1. Bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Sürüm deposunda çözümün ve projenin bir kopyasını oluşturun [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](Kullanıyorsanız Paylaş ve Şube).<br />4. Sürüm deposundaki dallı projedeki dosyaları değiştirin.<br />5. Aç **Kaynak Denetimi** iletişim kutusunu aç (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimini Değiştir**).<br />6. Unbind tüm.<br />7. **Kaynak Denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />8. **Kaynak Denetimi Değiştir** iletişim kutusunu yeniden açın.<br />9. Tümünü seçin.<br />10. **Bind'i**tıklatın.<br />11. Çözüm ve proje için dallı konuma göz atın.<br />12. **Kaynak Denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />13. Görünürse Uyarı iletişim kutusunu kabul edin.<br />14. Tüm öğeler için en son özyinelemeli alın. | Adım 4'te değiştirilen dosyalar da yerel olarak değiştirilir. |
| Kaynak denetimi altında hiç bağlanma çözümü | 1. Kaynak denetiminde boş bir klasör oluşturun.<br />2. Bir istemci projesi oluşturun.<br />3. Aç **Kaynak Denetimi** iletişim kutusunu aç (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimini Değiştir**).<br />4. Çözümü kaynak kontrolünde boş konuma bağlayın.<br />5. **Kaynak Denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />6. Onay iletişim kutusunda **bu bağlamalarla Devam** et'i tıklatın.<br />7. Görünürse uyarı iletişim kutusunda **Tamam'ı** tıklatın. | Çözüm kaynak denetimine eklenir.<br /><br /> Çözüm ve proje kullanıma alınır. |
| Bind'i İptal Et | 1. Bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Kaynak Denetimini Değiştir iletişim kutusunu açın.<br />4. Unbind Tüm.<br />5. İletişim kutusunu kapatmak için **Tamam** düğmesini tıklatın. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />6. Kaynak **Denetimini Değiştir** iletişim kutusunu yeniden açın.<br />7. Alakasız bir konuma bağlayın.<br />8. **İptal'i**tıklatın. | `Result from Step 5:`<br /><br /> Çözüm artık kaynak denetimi altında değil<br /><br /> `Result from Step 8:`<br /><br /> Çözüm hala kaynak denetimi altında DeğİlDir. |

### <a name="case-5b-unbind"></a>Örnek 5b: Unbind
 Unbind, projelerden ve çözümlerinden kaynak kodu denetim bilgilerini kaldırır. Etkilenen projeler ve çözüm, kullanıcı seçiminin bir karışımını ve maddelerin kaynak denetimine nasıl eklendiğine bağlıdır.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Bir Dosya Sistemi veya yerel IIS Web projesi ve bir istemci projesi içeren unbind çözüm|1. Bir Dosya Sistemi veya yerel IIS Web projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözüme yeni bir istemci projesi ekleyin.<br />4. İstenirse çözümden Çıkış Kabul Edin.<br />5. **Kaynak Denetimini Değiştir** iletişim kutusunu açın.<br />6. **Unbind'e**tıklayın.<br />7. İletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />8. Çözüm, proje, çözüm öğeleri, proje öğeleri kontrol etmeye çalışır.|Çözüm ve projeler kaynak kontrolü altında DeğİlDİ.<br /><br /> Kaynak Denetimi menüsü komutları görünmüyor.|
|Unbind'i İptal Et|1. Bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. **Kaynak Denetimini Değiştir** iletişim kutusunu açın.<br />4. **Tüm Unbind**tıklayın .<br />5. **İptal'i**tıklatın.|Çözüm kaynak kontrolü altındadır.|

### <a name="case-5c-rebind"></a>Örnek 5c: Rebind
 Rebind, daha önce kaynak denetimi altında olan ve bağlı olmayan bir proje/çözümü yeniden bağlama işlemi olan unbind ve bind'in basit bir birleşimidir.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|**Kaynak Denetimi Değiştir** iletişim kutusunu kapatmadan rebind çözümü ve projeleri|1. Bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. **Kaynak Denetimini Değiştir** iletişim kutusunu açın.<br />4. **Unbind'e**tıklayın.<br />5. Tüm satırları seçin.<br />6. **Bind'i**tıklatın.<br />7. **Kaynak Denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />8. İstenirse ödemeyi kabul edin.|Çözüm ve proje kaynak kontrolü altındadır.|
|Kaynak **Denetimi Değiştir** iletişim kutusunu kapatmadan yalnızca Rebind projesi|1. Bir proje oluşturun.<br />2. Yalnızca projeyi kaynak denetimine (Dosya >Kaynak Denetimi->Seçili Projeleri Kaynak Denetimine Ekle' yi kullanarak ekleyin.<br />3. Kaynak Denetimini Değiştir iletişim kutusunu açın.<br />4. Unbind sadece proje.<br />5. Yalnızca projeyi bağla.|Çözüm kontrolsüz kalır.<br /><br /> Proje kontrol altında kalır.|
|Kaynak **Denetimi Değiştir** iletişim kutusunu kapatmadan yalnızca rebind çözümü|1. Bir proje oluşturun.<br />2. Kaynak denetimine yalnızca çözüm ekleyin (**Dosya**, **Kaynak Denetimi**, **Seçili Projeleri Kaynak Denetimine Ekle**.<br />3. **Kaynak Denetimini Değiştir** iletişim kutusunu açın.<br />4. Yalnızca çözümü unbind **(Kaynak Denetimi değiştir** iletişim kutusunu kapatmayın.)<br />5. Yalnızca çözümü bağlayın.<br />6. İletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />7. Çözüm ve çözüm öğelerine göz atın (varsa.)|Çözüm kontrol altında kalır.<br /><br /> Proje kontrolsüz kalır.|
|Rebind çözüm/proje yalnızca aynı dizinde|1. Bir proje oluşturun.<br />2. Kullanarak kaynak denetimine yalnızca projeyi ekleyin (**Dosya**, **Kaynak Denetimi**, **Seçili Projeleri Kaynak Denetimine Ekle**.<br />3. Çözümü kapatın.<br />4. En az iki proje ile yeni bir çözüm oluşturun.<br />5. Çözümü kaynak denetimine ekleyin.<br />6. Basamak 1'de oluşturulan projeyi kaynak denetiminden ekleyin.<br />7. İstenirse çözümün ödemesini kabul edin.<br />8. Tüm çözümü kontrol edin.<br />9. **Kaynak Denetimini Değiştir** iletişim kutusunu açın.<br />10. Eklenen projeyi seçin (Adım 6'dan) ve **Unbind'i**tıklatın.<br />11. İletişim kutusunu kapatmak için **Tamam'ı** tıklatın.<br />12. İstenirse ödemeyi kabul edin.<br />13. **Kaynak Denetimi Değiştir** iletişim kutusunu yeniden aç.<br />14. Eklenen projeyi seçin (Adım 6'dan) ve **Bind'i**tıklatın.<br />15. Orijinal konumu seçin.|Çözüm ve projeler kontrol altında kalır.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
