---
title: 'Test Alanı 5: Kaynak Denetimi Ayarlarını | Microsoft Docs'
description: Bu kaynak denetimi eklentisi test alanı, Kaynak Denetimi Değiştir komutunu kullanarak kaynak denetimin değiştirilmesini kapsar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 541a904789b3e3d9dc7334790fa473cde2e40e63479e84b3ee61e4d376a9ba50
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431792"
---
# <a name="test-area-5-change-source-control"></a>Test Alanı 5: Kaynak Denetimini Değiştirme
Bu kaynak denetimi eklentisi test alanı, Kaynak Denetimi Değiştir komutuyla kaynak **denetimin değiştirilmesini** kapsar.

 **Kaynak Denetimi Değiştir** komutu kullanıcı için dört temel işlev sağlar:

- **Bağlamak:**

   Kullanıcının bir çözüm/proje ile sürüm deposu arasında kaynak denetimi bağlantısı kurması veya yeniden kurması için izin verir.

- **Unbind:**

   Bir projeyi/çözümü bağlantı başına kaynak denetiminden kaldırır.

- **Bağlan/Bağlantıyı Kes:**

  Denetimli çözümün bağlı veya çevrimdışı durumunu açıp kapatarak 3. Alan'da ele alınamaz. Daha fazla bilgi için bkz. [Test Alanı 3: Kullanıma Alma/Kullanıma Almayı Geri Alma.](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

## <a name="command-menu-access"></a>Komut Menüsü Erişimi
 Test [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çalışmalarında aşağıdaki tümleşik geliştirme ortamı menü yolu kullanılır.

 Kaynak Denetimi Değiştir:**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimi'nin Değişiklik.**

## <a name="test-cases"></a>Test Çalışmaları
 Aşağıda, Kaynak Denetimi Değiştir komut test **alanına özgü** test testleri yer almaktadır.

### <a name="case-5a-bind"></a>Durum 5a: Bağlama
 Bağlama, kullanıcının seçilen projelere ve çözümlere kaynak kodu denetim bilgileri eklemelerini sağlar. Kullanıcıdan genellikle kaynak denetiminde bunların ekli olduğu bir projeyi tanımlaması istenir. Kullanıcı, bu işlem kapsamında kaynak denetiminde yeni bir proje oluşturamayebiliyor (Kaynak Denetimine Ekle ile karşıtlık).

| Eylem | Test Adımları | Doğrulandı Beklenen Sonuçlar |
| - | - | - |
| Boş konuma bağlama | 1. Proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Kaynak **Denetimi Değiştir iletişim** kutusunu açın (**Dosya**, **Kaynak Denetimi**, Kaynak **Denetimi Değiştir**).<br />4. **Bindirin'e tıklayın.**<br />5. Görünürse uyarı iletişim kutusunu kabul et.<br />6. Tüm öğeleri seçin.<br />7. **Bağla'ya tıklayın.**<br />8. Kaynak denetim deposu içinde boş bir konuma göz atma.<br />9. Kaynak **Denetimi** Değiştir iletişim **kutusunu kapatmak için Tamam'a** tıklayın.<br />10. Onay **iletişim kutusunda Bu bağlamalarla devam'a** tıklayın.<br />11. **Görünürse** uyarı iletişim kutusunda Tamam'a tıklayın.<br />12. Her şeyi kontrol edin. Bu adım başarılı olursa sonraki adıma geçin.<br />13. Kaynak denetiminden yeni bir konuma çözüm açın. | `Result from Step 12:`<br /><br /> Çözüm ve proje, sürüm deposuna bağlı ve yeni hedefe yazılır.<br /><br /> Çözüm ve proje dosyaları iade edilir.<br /><br /> Sürüm deposu proje hiyerarşisi, diskte projenin klasör hiyerarşisi ile eşler.<br /><br /> `Result from Step 13:`<br /><br /> Tüm proje öğeleri indirilir. |
| İstemciyle eşitlenen konuma bağlama | 1. Proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Sürüm depolamada çözümün ve projenin bir kopyasını oluşturun (kullanıyorsanız Paylaş ve [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Dal).<br />4. Kaynak **Denetimi Değiştir iletişim** kutusunu açın (**Dosya**, **Kaynak Denetimi**, Kaynak **Denetimi Değiştir**).<br />5. TümLerin Bindirin.<br />6. Kaynak **Denetimi Değiştir** iletişim kutusunu kapatmak **için Tamam'a** tıklayın.<br />7. Kaynak **Denetimi Değiştir iletişim kutusunu** yeniden açın.<br />8. Hepsini seçin.<br />9. **Bağla'ya tıklayın.**<br />10. Çözümün ve projenin dallı konuma göz atma (3. adımdan)<br />11. Kaynak **Denetimi** Değiştir iletişim **kutusunu kapatmak için Tamam'a** tıklayın.<br />12. Tüm öğeler için En Son'a recursively al. | Get sonrasındaki dosya içeriği, get'den öncekiyle aynıdır. |
| İstemciyle eşitlenen konuma bağlama | 1. Proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Sürüm depolamada çözümün ve projenin bir kopyasını oluşturun (kullanıyorsanız Paylaş ve [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Dal).<br />4. Sürüm deposuna dallı proje dosyaları değiştirme.<br />5. Kaynak **Denetimi Değiştir iletişim** kutusunu açın (**Dosya**, **Kaynak Denetimi**, Kaynak **Denetimi Değiştir**).<br />6. Tümlerin bindirin.<br />7. Kaynak **Denetimi Değiştir** iletişim kutusunu kapatmak **için Tamam'a** tıklayın.<br />8. Kaynak **Denetimi Değiştir iletişim kutusunu** yeniden açın.<br />9. Hepsini seçin.<br />10. **Bağla'ya tıklayın.**<br />11. Çözüm ve proje için dallı konuma göz atma.<br />12. Kaynak **Denetimi** Değiştir iletişim **kutusunu kapatmak için Tamam'a** tıklayın.<br />13. Görünürse Uyarı iletişim kutusunu kabul et.<br />14. Tüm öğeler için En Son tekrarlayıcıyı al. | 4. Adımda değiştirilen dosyalar da yerel olarak değiştirilir. |
| Hiçbir zaman kaynak denetimi altında yer alan bağlama çözümü | 1. Kaynak denetiminde boş bir klasör oluşturun.<br />2. İstemci projesi oluşturma.<br />3. Kaynak **Denetimi Değiştir iletişim** kutusunu açın (**Dosya**, **Kaynak Denetimi**, Kaynak **Denetimi Değiştir**).<br />4. Çözümü kaynak denetiminde boş konuma bağlayın.<br />5. Kaynak **Denetimi** Değiştir iletişim **kutusunu kapatmak için Tamam'a** tıklayın.<br />6. Onay **iletişim kutusunda Bu bağlamalarla devam'a** tıklayın.<br />7. **Görünürse** uyarı iletişim kutusunda Tamam'a tıklayın. | Çözüm kaynak denetimine eklenir.<br /><br /> Çözüm ve proje kullanıma alınmış. |
| Bağlamayı İptal Etme | 1. Proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Kaynak Denetimi Değiştir iletişim kutusunu açın.<br />4. TümLerin Bindirin.<br />5. İletişim **kutusunu** kapatmak için Tamam düğmesine tıklayın. Bu adım başarılı olursa sonraki adıma geçin.<br />6. Kaynak Denetimi **Değiştir iletişim kutusunu** yeniden açın.<br />7. Ilgisiz konuma bağlama.<br />8. **İptal'e tıklayın.** | `Result from Step 5:`<br /><br /> Çözüm artık kaynak denetimi altında değil<br /><br /> `Result from Step 8:`<br /><br /> Çözüm hala kaynak denetimi altında DEĞIL. |

### <a name="case-5b-unbind"></a>Olay 5b: Bindirin
 Unbind, projelerden ve çözümlerinden kaynak kodu denetim bilgilerini kaldırır. Etkilenen projeler ve çözüm, kullanıcı seçiminin bir karışımına ve öğelerin kaynak denetimine nasıl eklendiğine dayalıdır.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Bir Dosya Sistemi veya yerel IIS Web projesi ve bir istemci projesi içeren bağlantısız çözüm|1. Dosya Sistemi veya yerel IIS Web projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözüme yeni bir istemci projesi ekleyin.<br />4. İstendiğinde çözümün Çıkış'larını kabul edin.<br />5. Kaynak **Denetimi Değiştir iletişim** kutusunu açın.<br />6. **Bindirin'e tıklayın.**<br />7. İletişim **kutusunu kapatmak** için Tamam'a tıklayın.<br />8. Çözüm, proje, çözüm öğeleri, proje öğelerini denetlemeyi deneyin.|Çözüm ve projeler kaynak denetimi altında YOK.<br /><br /> Kaynak Denetimi menü komutları görünmez.|
|Unbind'i İptal Etme|1. Proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Kaynak **Denetimi Değiştir iletişim** kutusunu açın.<br />4. Tüm **öğesinin bindirin'e tıklayın.**<br />5. **İptal'e tıklayın.**|Çözüm kaynak denetimi altında.|

### <a name="case-5c-rebind"></a>Durum 5c: Yeniden bindir
 Rebind, daha önce kaynak denetimi altında olan ve sınırsız olan bir projeyi/çözümü yeniden bağlama işlemi olan bağlamayı ve bağlamayı bağlama işleminin bir birleşimidir.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak Denetimi Değiştir iletişim kutusunu kapatmadan çözümü **ve projeleri yeniden** ekleyin|1. Proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Kaynak **Denetimi Değiştir iletişim** kutusunu açın.<br />4. **Bindirin'e tıklayın.**<br />5. Tüm satırları seçin.<br />6. **Bağla'ya tıklayın.**<br />7. Kaynak **Denetimi** Değiştir iletişim **kutusunu kapatmak için Tamam'a** tıklayın.<br />8. İstendiğinde iadeyi kabul edin.|Çözüm ve proje kaynak denetimi altında.|
|Projeyi yalnızca Kaynak Denetimi Değiştir iletişim **kutusunu kapatmadan yeniden** ekleyin|1. Proje oluşturun.<br />2. Kullanarak yalnızca projeyi kaynak denetimine ekleyin (Dosya->-Kaynak Denetimi->Seçilen Projeleri Kaynak Denetimine Ekle.<br />3. Kaynak Denetimi Değiştir iletişim kutusunu açın.<br />4. Yalnızca projenin bindirin.<br />5. Yalnızca projeyi bağlayın.|Çözüm denetimsiz kalır.<br /><br /> Project denetim altında kalır.|
|Çözümü yalnızca Kaynak Denetimi Değiştir iletişim **kutusunu kapatmadan yeniden** ekleyin|1. Proje oluşturun.<br />2. Kullanarak yalnızca çözümü kaynak denetimine ekleyin (**Dosya**, **Kaynak Denetimi**, Seçilen Projeleri **Kaynak Denetimine Ekle.**<br />3. Kaynak **Denetimi Değiştir iletişim** kutusunu açın.<br />4. Yalnızca çözümün bindirin (Kaynak Denetimi **Değiştir iletişim kutusunu** kapat'ı kapatın.)<br />5. Yalnızca çözümü bağlayın.<br />6. İletişim **kutusunu kapatmak** için Tamam'a tıklayın.<br />7. Çözüm ve çözüm öğelerini (varsa) kontrol edin.|Çözüm denetim altında kalır.<br /><br /> Project denetimsiz kalır.|
|Çözümü/projeyi yalnızca aynı dizinde olduğunda yeniden bindirin|1. Proje oluşturun.<br />2. Kullanarak yalnızca projeyi kaynak denetimine ekleyin (**Dosya**, **Kaynak Denetimi**, Seçilen Projeleri **Kaynak Denetimine Ekle.**<br />3. Çözümü kapatın.<br />4. En az iki projeyle yeni bir çözüm oluşturun.<br />5. Çözümü kaynak denetimine ekleyin.<br />6. Kaynak denetiminden 1. Adımda oluşturulan projeyi ekleyin.<br />7. İstendiğinde çözümün onay kutusunu kabul edin.<br />8. Çözümün tamamını kontrol edin.<br />9. Kaynak **Denetimi Değiştir iletişim** kutusunu açın.<br />10. Eklenen projeyi seçin (Adım 6'dan) ve **Unbind 'e tıklayın.**<br />11. İletişim **kutusunu kapatmak** için Tamam'a tıklayın.<br />12. İstendiğinde onay kutusunu kabul edin.<br />13. Kaynak **Denetimi Değiştir iletişim kutusunu** yeniden açın.<br />14. Eklenen projeyi seçin (6. Adım'dan) ve **Bağla'ya tıklayın.**<br />15. Özgün konumu seçin.|Çözüm ve projeler denetim altında kalır.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
