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
ms.openlocfilehash: 24cbcc50b3641bc62242ee7216d6ce4c1f290efd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158781"
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

|Eylem|Test Adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Bir dosya sistemi veya yerel IIS Web projesi ve bir istemci projesi içeren çözümün bağlantısını kaldır|1. bir dosya sistemi veya yerel IIS Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözüme yeni bir istemci projesi ekleyin.<br />4. istenirse çözümü kullanıma alma kabul edin.<br />5. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />6. **ciltten çıkar**'a tıklayın.<br />7. iletişim kutusunu kapatmak için **Tamam 'ı** tıklatın.<br />8. çözümü, projeyi, çözüm öğelerini, proje öğelerini kullanıma alma girişimi.|Çözüm ve projeler kaynak denetimi altında DEĞIL.<br /><br /> Kaynak denetimi menü komutları görünmüyor.|
|Kesme bağlantısını iptal et|1. bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />4. **Tümünü çöz**' e tıklayın.<br />5. **Iptal 'e** tıklayın.|Çözüm, kaynak denetimi altında.|

### <a name="case-5c-rebind"></a>Case 5c: yeniden bağlama
 Yeniden bağlama, daha önce kaynak denetimi altında olan ve bağlantısı olmayan bir projeyi/çözümü yeniden bağlama işleminin yalnızca ciltten ve bağlamaya yönelik bir birleşimidir.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|**Kaynak denetimini Değiştir** iletişim kutusunu kapatmadan çözümü ve projeleri yeniden bağlayın|1. bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />4. **ciltten çıkar**'a tıklayın.<br />5. tüm satırları seçin.<br />6. **bağla**'yı tıklatın.<br />7. **kaynak denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam** 'a tıklayın.<br />8. istenirse, kullanıma almayı kabul edin.|Çözüm ve proje kaynak denetimi altındadır.|
|Projeyi yalnızca **değişiklik kaynağı denetimini** kapatmadan yeniden bağlayın iletişim kutusu|1. bir proje oluşturun.<br />2. (dosya->kaynak denetimi->seçilen projeleri kaynak denetimine Ekle öğesini kullanarak kaynak denetimine yalnızca proje ekleyin.<br />3. kaynak denetimini Değiştir iletişim kutusunu açın.<br />4. yalnızca projenin bağlantısını kesin.<br />5. yalnızca projeyi bağlayın.|Çözüm denetlenmeye devam ediyor.<br /><br /> Project denetlenmeye devam eder.|
|Çözümü yalnızca **değişiklik kaynağı denetimi** 'ni kapatmadan yeniden bağlayın iletişim kutusu|1. bir proje oluşturun.<br />2. (**Dosya**, **kaynak denetimi**, **Seçili projeleri kaynak denetimine Ekle**) kullanarak yalnızca kaynak denetimine çözüm ekleyin.<br />3. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />4. yalnızca çözümün bağlantısını kesin ( **kaynak denetimini Değiştir** iletişim kutusunu kapatmayın.)<br />5. yalnızca çözümü bağlayın.<br />6. iletişim kutusunu kapatmak için **Tamam** 'a tıklayın.<br />7. çözüm ve çözüm öğelerine göz atın (varsa).|Çözüm denetlenmeye devam eder.<br /><br /> Project denetlenmeye devam ediyor.|
|Çözümü/projeyi yalnızca aynı dizinde olduğunda yeniden bağlayın|1. bir proje oluşturun.<br />2. (**Dosya**, **kaynak denetimi**, **Seçili projeleri kaynak denetimine Ekle**) kullanarak yalnızca projeyi kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. en az iki projeyle yeni bir çözüm oluşturun.<br />5. çözümü kaynak denetimine ekleyin.<br />6. Adım 1 ' de oluşturulan projeyi kaynak denetiminden ekleyin.<br />7. istenirse çözümü kullanıma almayı kabul edin.<br />8. tüm çözümü iade edin.<br />9. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />10. eklenen projeyi seçin (6. adımdan) ve **ciltten çıkar**' a tıklayın.<br />11. iletişim kutusunu kapatmak için **Tamam 'ı** tıklatın.<br />12. istenirse, kullanıma almayı kabul edin.<br />13. **değişiklik kaynağı denetimini** yeniden açın iletişim kutusu.<br />14. eklenen projeyi seçin (6. adımdan) ve ardından **bağla**' ya tıklayın.<br />15. özgün konumu seçin.|Çözüm ve projeler denetlenmeye devam eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
