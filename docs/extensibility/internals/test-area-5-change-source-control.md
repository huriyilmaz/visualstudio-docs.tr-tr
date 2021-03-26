---
title: 'Test alanı 5: kaynak denetimini değiştirme | Microsoft Docs'
description: Bu kaynak denetimi eklentisi test alanı, kaynak denetimini Değiştir komutunu kullanarak kaynak denetiminin değiştirilmesini içerir.
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
ms.workload:
- vssdk
ms.openlocfilehash: 44647781b8f7605a59fba5d9249b6a7165c0e27e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073410"
---
# <a name="test-area-5-change-source-control"></a>Test Alanı 5: Kaynak Denetimini Değiştirme
Bu kaynak denetimi eklentisi test alanı, kaynak denetimini **Değiştir** komutunu kullanarak kaynak denetiminin değiştirilmesini içerir.

 **Kaynak denetimini Değiştir** komutu, Kullanıcı için dört temel işlev sağlar:

- **Bağladığınızda**

   Kullanıcının bir çözüm/proje ile sürüm deposu arasında bir kaynak denetimi bağlantısı kurmasını veya yeniden kurmasını sağlar.

- **Kesin**

   Kaynak denetiminden bir proje/çözümü bağlantı başına temelinde kaldırır.

- **Bağlan/Bağlantıyı Kes:**

  , Alan 3 ' te ele alınan denetimli çözümün bağlı veya çevrimdışı durumuna geçer. Daha fazla bilgi için bkz. [test alanı 3: kullanıma almayı kullanıma alma/geri alma](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Komut menüsü erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı menü yolu, test durumlarında kullanılır.

 Kaynak denetimini Değiştir:**Dosya**, **kaynak denetimi**, **kaynak denetimini Değiştir**.

## <a name="test-cases"></a>Test Çalışmaları
 Aşağıda, **kaynak denetimi değiştir** komut testi alanı için özel test çalışmaları verilmiştir.

### <a name="case-5a-bind"></a>Case 5A: bağlama
 Bağlama, kullanıcının seçili projelere ve çözümlere kaynak kodu denetim bilgisi eklemesine izin verir. Kullanıcıdan, genellikle bunların ekleneceği kaynak denetimindeki bir projeyi tanımlaması istenir. Kullanıcı bu işlemin bir parçası olarak kaynak denetiminde yeni bir proje oluşturmayabilir (kaynak denetimine Ekle ' ye kontrast).

| Eylem | Test adımları | Doğrulanacak beklenen sonuçlar |
| - | - | - |
| Boş konuma bağla | 1. bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. **kaynak denetimini Değiştir** iletişim kutusunu açın (**Dosya**, **kaynak denetimi**, **kaynak denetimini değiştirin**).<br />4. **ciltten çıkar**'a tıklayın.<br />5. görüntülenirse uyarı iletişim kutusunu kabul edin.<br />6. tüm öğeleri seçin.<br />7. **bağla**'yı tıklatın.<br />8. kaynak denetim deposundaki boş bir konuma gidin.<br />9. **kaynak denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam** 'a tıklayın.<br />10. onay iletişim kutusunda **Bu bağlamalarla devam et** ' e tıklayın.<br />11. görüntülenirse, uyarı iletişim kutusunda **Tamam** ' a tıklayın.<br />12. her şeyi iade edin. Bu adım başarılı olursa sonraki adımla devam edin.<br />13. kaynak denetiminden yeni bir konuma çözüm açın. | `Result from Step 12:`<br /><br /> Çözüm ve proje, sürüm deposundaki yeni hedefe bağlanır ve bu hedefe yazılır.<br /><br /> Çözüm ve proje dosyaları iade edilir.<br /><br /> Sürüm deposu proje hiyerarşisi diskteki projenin klasör hiyerarşisine eşleşiyor.<br /><br /> `Result from Step 13:`<br /><br /> Tüm proje öğeleri indirilir. |
| İstemcisiyle eşitlenmiş konuma bağlama | 1. bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. sürüm deposunda çözüm ve proje yinelemesi oluşturun (Eğer kullanıyorsanız, paylaşma ve dalı [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. **kaynak denetimini Değiştir** iletişim kutusunu açın (**Dosya**, **kaynak denetimi**, **kaynak denetimini değiştirin**).<br />5. tümünün bağlantısını kaldır.<br />6. **Tamam** 'A tıklayarak **kaynak denetimini Değiştir** iletişim kutusunu kapatın.<br />7. **kaynak denetimini Değiştir** iletişim kutusunu yeniden açın.<br />8. tümünü seçin.<br />9. **bağla**'yı tıklatın.<br />10. çözümün ve projenin dallanmış konumuna gidin (adım 3 ' ten)<br />11. **kaynak denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam** 'a tıklayın.<br />12. tüm öğeler için yinelemeli olarak en son alın. | Get öğesinden sonra dosya içeriği, Get öncesindeki ile aynı olur. |
| İstemci ile eşitlenmemiş konuma bağlama | 1. bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. sürüm deposunda çözüm ve proje yinelemesi oluşturun (Eğer kullanıyorsanız, paylaşma ve dalı [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. Sürüm deposundaki dallanmış projedeki dosyaları değiştirin.<br />5. **kaynak denetimini Değiştir** iletişim kutusunu açın (**Dosya**, **kaynak denetimi**, **kaynak denetimini değiştirin**).<br />6. tümünün bağlantısını kaldır.<br />7. **Tamam** 'A tıklayarak **kaynak denetimini Değiştir** iletişim kutusunu kapatın.<br />8. **kaynak denetimini Değiştir** iletişim kutusunu yeniden açın.<br />9. tümünü seçin.<br />10. **bağla**' ya tıklayın.<br />11. çözüm ve proje için dallanmış konuma gidin.<br />12. **kaynak denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam** 'a tıklayın.<br />13. görüntülenirse uyarı iletişim kutusunu kabul edin.<br />14. tüm öğeler için en son özyinelemeli alın. | Adım 4 ' te değiştirilen dosyalar da yerel olarak değiştirilir. |
| Kaynak denetimi altında hiç bir şekilde bağlama çözümü | 1. kaynak denetiminde boş bir klasör oluşturun.<br />2. bir istemci projesi oluşturun.<br />3. **kaynak denetimini Değiştir** iletişim kutusunu açın (**Dosya**, **kaynak denetimi**, **kaynak denetimini değiştirin**).<br />4. çözümü kaynak denetimindeki boş konuma bağlayın.<br />5. **kaynak denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam** 'a tıklayın.<br />6. onay iletişim kutusunda **Bu bağlamalara devam et** ' e tıklayın.<br />7. görüntülenirse, uyarı iletişim kutusunda **Tamam** ' a tıklayın. | Çözüm, kaynak denetimine eklenir.<br /><br /> Çözüm ve proje kullanıma alındı. |
| Bağlamayı iptal et | 1. bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. kaynak denetimini Değiştir iletişim kutusunu açın.<br />4. tümünün bağlantısını kaldır.<br />5. iletişim kutusunu kapatmak için **Tamam** düğmesine tıklayın. Bu adım başarılı olursa sonraki adımla devam edin.<br />6. **kaynak denetimini Değiştir** iletişim kutusunu yeniden açın.<br />7. ilişkisiz konuma bağlayın.<br />8. **Iptal 'e** tıklayın. | `Result from Step 5:`<br /><br /> Çözüm artık kaynak denetimi altında değil<br /><br /> `Result from Step 8:`<br /><br /> Çözüm hala kaynak denetimi altında DEĞIL. |

### <a name="case-5b-unbind"></a>Case 5B: ciltten çıkar
 Ciltten Çıkar, projelerden ve çözümlerinin kaynak kodu denetim bilgilerini kaldırır. Etkilenen projeler ve çözüm, Kullanıcı seçiminin bir karışımını ve öğelerin kaynak denetimine Eklenme şeklini temel alır.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Bir dosya sistemi veya yerel IIS Web projesi ve bir istemci projesi içeren çözümün bağlantısını kaldır|1. bir dosya sistemi veya yerel IIS Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözüme yeni bir istemci projesi ekleyin.<br />4. istenirse çözümü kullanıma alma kabul edin.<br />5. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />6. **ciltten çıkar**'a tıklayın.<br />7. iletişim kutusunu kapatmak için **Tamam 'ı** tıklatın.<br />8. çözümü, projeyi, çözüm öğelerini, proje öğelerini kullanıma alma girişimi.|Çözüm ve projeler kaynak denetimi altında DEĞIL.<br /><br /> Kaynak denetimi menü komutları görünmüyor.|
|Kesme bağlantısını iptal et|1. bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />4. **Tümünü çöz**' e tıklayın.<br />5. **Iptal 'e** tıklayın.|Çözüm, kaynak denetimi altında.|

### <a name="case-5c-rebind"></a>Case 5c: yeniden bağlama
 Yeniden bağlama, daha önce kaynak denetimi altında olan ve bağlantısı olmayan bir projeyi/çözümü yeniden bağlama işleminin yalnızca ciltten ve bağlamaya yönelik bir birleşimidir.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|**Kaynak denetimini Değiştir** iletişim kutusunu kapatmadan çözümü ve projeleri yeniden bağlayın|1. bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />4. **ciltten çıkar**'a tıklayın.<br />5. tüm satırları seçin.<br />6. **bağla**'yı tıklatın.<br />7. **kaynak denetimini Değiştir** iletişim kutusunu kapatmak için **Tamam** 'a tıklayın.<br />8. istenirse, kullanıma almayı kabul edin.|Çözüm ve proje kaynak denetimi altındadır.|
|Projeyi yalnızca **değişiklik kaynağı denetimini** kapatmadan yeniden bağlayın iletişim kutusu|1. bir proje oluşturun.<br />2. (dosya->kaynak denetimi->seçilen projeleri kaynak denetimine Ekle öğesini kullanarak kaynak denetimine yalnızca proje ekleyin.<br />3. kaynak denetimini Değiştir iletişim kutusunu açın.<br />4. yalnızca projenin bağlantısını kesin.<br />5. yalnızca projeyi bağlayın.|Çözüm denetlenmeye devam ediyor.<br /><br /> Proje denetlenmeye devam ediyor.|
|Çözümü yalnızca **değişiklik kaynağı denetimi** 'ni kapatmadan yeniden bağlayın iletişim kutusu|1. bir proje oluşturun.<br />2. (**Dosya**, **kaynak denetimi**, **Seçili projeleri kaynak denetimine Ekle**) kullanarak yalnızca kaynak denetimine çözüm ekleyin.<br />3. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />4. yalnızca çözümün bağlantısını kesin ( **kaynak denetimini Değiştir** iletişim kutusunu kapatmayın.)<br />5. yalnızca çözümü bağlayın.<br />6. iletişim kutusunu kapatmak için **Tamam** 'a tıklayın.<br />7. çözüm ve çözüm öğelerine göz atın (varsa).|Çözüm denetlenmeye devam eder.<br /><br /> Proje denetlenmeye devam ediyor.|
|Çözümü/projeyi yalnızca aynı dizinde olduğunda yeniden bağlayın|1. bir proje oluşturun.<br />2. (**Dosya**, **kaynak denetimi**, **Seçili projeleri kaynak denetimine Ekle**) kullanarak yalnızca projeyi kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. en az iki projeyle yeni bir çözüm oluşturun.<br />5. çözümü kaynak denetimine ekleyin.<br />6. Adım 1 ' de oluşturulan projeyi kaynak denetiminden ekleyin.<br />7. istenirse çözümü kullanıma almayı kabul edin.<br />8. tüm çözümü iade edin.<br />9. **kaynak denetimini Değiştir** iletişim kutusunu açın.<br />10. eklenen projeyi seçin (6. adımdan) ve **ciltten çıkar**' a tıklayın.<br />11. iletişim kutusunu kapatmak için **Tamam 'ı** tıklatın.<br />12. istenirse, kullanıma almayı kabul edin.<br />13. **değişiklik kaynağı denetimini** yeniden açın iletişim kutusu.<br />14. eklenen projeyi seçin (6. adımdan) ve ardından **bağla**' ya tıklayın.<br />15. özgün konumu seçin.|Çözüm ve projeler denetlenmeye devam eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
