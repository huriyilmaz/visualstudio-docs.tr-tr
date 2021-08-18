---
title: 'Test alanı 1: kaynak denetiminden To-Open ekleme | Microsoft Docs'
description: Bu kaynak denetimi eklentisi test alanı, çözümlerin veya projelerin kaynak denetimi altına yerleştirilmesi ve bunları kaynak denetiminden almasını içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a318574dac3370a1fe754ab1f0cf6c015531271659798dfd04972e3f7852cae6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431857"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Test Alanı 1: Kaynak Denetimine Ekleme/Kaynak Denetiminden Açma
Bu kaynak denetimi eklentisi test alanı, çözümlerin veya projelerin kaynak denetimi altına yerleştirilmesi ve bunları kaynak denetiminden almasını içerir.

## <a name="command-menu-access"></a>Komut menüsü erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı menü yolları test durumlarında kullanılır:

- için [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] kaynak denetiminden açın: **dosya**, **aç**, **Project** / **çözüm**; [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] konuma bakın.

- Diğer kaynak denetimi eklentileri için kaynak denetiminden Aç: **Dosya**, **kaynak denetimi**, **kaynak denetiminden Aç**.

- Kaynak denetimine Ekle: **Dosya**, **kaynak denetimi**, **kaynak denetim dosyasına çözüm ekleme**, **kaynak** denetimi, **Seçili projeleri kaynak denetimine ekleme**.

- kısayol menüsü (Project/solution), **kaynak denetimine çözüm ekleyin**.

- kaynak denetiminden ekle: **dosya**, **kaynak denetimi**, **kaynak denetiminden Project ekleyin**.

- için [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , kaynak denetiminden ekle ' de **dosya**, **ekle**, **varolan Project**' den de kullanılabilir; konuma bakın [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] .

  > [!NOTE]
  > Bu testte yerel bir dosyanın veya yerel bir IIS 'nin (Web sunucusu) bir yolu kullanılabilir.

## <a name="expected-behavior"></a>Beklenen davranış

- Desteklenen her proje türü için, bir Kullanıcı, kaynak denetiminden "ekleme" ve "açma" yapabilmelidir.

- kaynak denetimine bir proje eklendiğinde, karşılık gelen bir \<*ProjectName*> . vspscc dosyası (Project ipucu dosyası) oluşturulur. Dışlama dosya listesi ve bağlantı bilgilerini içerir. Projeye özgü bilgiler içerdiğinden bu dosyayı silmeyin.

- Kaynak denetimine bir çözüm eklendiğinde, buna karşılık gelen \<*SolutionName*> . vssscc (Üçlü S) dosyası oluşturulur. Metin dosyası, proje ipucu dosyasına benzer şekilde bağlantı bilgilerini ve bir hariç tutma dosya listesini içerir. Bu dosya geçicidir ve yalnızca kaynak denetimi veritabanında bulunur.

- Kaynak denetiminden bir çözüm açıldığında, \<*SolutionName*> geçici bir dosyada yerel olarak yalnızca kaynak denetim veritabanında bulunan bir. vsscc (çift S) dosyası oluşturulur. Bu dosya çözüm bağlantısı klasöründen çözüm dosyasına yolu içerir. Bu dosya geçicidir ve "kaynak denetiminden Aç" işlemi tamamlandığında yerel kopya silinir.

- Kaynak denetimine bir proje eklendikten sonra, üzerinde herhangi bir kaynak denetimi eylemi gerçekleştirebilirsiniz (kullanıma alma, alma, vb.).

## <a name="test-cases"></a>Test Çalışmaları
 Kaynak denetimi test alanından Ekle/aç ' a yönelik özel test durumları aşağıda verilmiştir.

### <a name="case-1a-add-solution-to-source-control"></a>Durum 1a: kaynak denetimine çözüm ekleme
 Bu test çalışması, kaynak denetimine çözüm eklemeye odaklanır.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetimine istemci projesi içeren çözüm ekleme|1. bir istemci projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetimine çözüm ekleme**).|çözüm/Project kaynak denetimine eklendi.|
|Kaynak denetimine bir dosya sistemi veya yerel IIS Web projesi içeren çözüm ekleme|1. bir dosya sistemi veya yerel IIS Web projesi oluşturun (projenin konumuna işaret etmek için gözatmayı kullanın; yol, ne tür bir Web projesi oluşturulacağını belirler).<br />2. çözümü kaynak denetimine ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetimine çözüm ekleme**).|çözüm/Project kaynak denetimine eklendi.|
|Kaynak denetimine uzak site Web projesi içeren çözüm ekleme|1. bir uzak site Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetimine çözüm ekleme**).<br />3. FrontPage erişim Uyarısı iletişim kutusunda **Tamam** ' a tıklayın.|Çözüm, kaynak denetimine eklendi.<br /><br /> Uzak site projesi kaynak denetimi altında DEĞIL. (Uzak site projelerinin kendi IIS sunucusundan denetlenmesi gerekir.)|
|Kaynak denetimine **Seçili projeler Ekle** öğesini kullanarak kaynak denetimine tek bir proje çözümü ekleyin.|1. tek bir proje çözümü oluşturun.<br />2. yalnızca bir seçim olarak kaynak denetimine çözüm ekleyin (**Dosya**, **kaynak denetimi**, **Seçili projeleri kaynak denetimine Ekle**). Bu adım başarılı olursa sonraki adımla devam edin.<br />3. projeyi kaynak denetimine seçim olarak ekleyin (**Dosya**, **kaynak denetimi**, **Seçili projeleri kaynak denetimine Ekle**).<br />4. projeyi aynı konuma eklemek için **Evet** 'e tıklayın.<br />5. **düzenleme için kullanıma alma** Iletişim kutusunda **kullanıma** alma ' ya tıklayın.|`Result from Step 2:`<br /><br /> Projenin ve proje içindeki tüm dosyaların kullanıma alınmış kaynak denetimi göstergesi vardır ve araç Ipucu "kaynak denetimi altında değil" olarak görüntülenir.<br /><br /> `Result from Step 5:`<br /><br /> Project ve çözüm dosyası kaynak denetimindeki aynı klasörslardır.|
|Kaynak denetimine çözüm eklemeyi iptal et|1. tek bir proje çözümü oluşturun.<br />2. kaynak denetimine proje ve çözüm eklemeyi deneyin. Bu adım başarılı olursa sonraki adımla devam edin.<br />3. kaynak denetim sisteminden sonra iptal edin.|`Result from Step 2:`<br /><br /> Proje konumu kaynak denetimini ayarla iletişim kutusu yalnızca bir kez görünür.<br /><br /> `Result from Step 3:`<br /><br /> Project ekleme iptal edildi, proje/çözüm kaynak denetimi altında değil ve tüm kaynak denetim menülerine hala erişilebilir.|

### <a name="case-1b-open-solution-from-source-control"></a>Durum 1B. Kaynak denetiminden çözüm aç
 Bu test çalışması, çözümleri kaynak denetiminden açmaya odaklanır.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetiminden bir istemci projesi içeren bir çözüm açın|1. bir istemci projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. çözümü kaynak denetiminden yeni bir konuma açın.|çözüm/Project kaynak denetiminden açıldı.|
|Kaynak denetiminden yerel veya IIS Web projesi içeren bir çözüm açın|1. yerel veya IIS Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. çözümü kaynak denetiminden yeni bir konuma açın.|çözüm/Project kaynak denetiminden açıldı.|
|Kaynak denetiminden uzak site Web projesi içeren bir çözüm açın|1. bir uzak site Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin. Bu adım başarılı olursa sonraki adımla devam edin.<br />3. çözümü kapatın.<br />4. çözümü kaynak denetiminden yeni bir konuma açın.|`Result from Step 2:`<br /><br /> Uzak site Web, kaynak denetimi altında DEĞIL.<br /><br /> `Result from Step 4:`<br /><br /> Çözüm, kaynak denetiminden açıldı.<br /><br /> Uzak site projesi yüklendi, ancak kaynak denetimi altında DEĞIL.|

### <a name="case-1c-add-solution-from-source-control"></a>Case 1C: kaynak denetiminden çözüm ekleme
 Bu test çalışması, kaynak denetiminden çözüm eklemeye odaklanır.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Boş çözüme ekleme — tek bir proje çözümü|1. tek bir proje çözümü oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. ikinci boş bir çözüm oluşturun.<br />5. Kaynak denetiminden daha önce denetlenen çözümü ekleyin (**Dosya**, **Kaynak Denetimi**, **Project Denetimi'ne ekleyin).**|Eklenen proje, **Çözüm Gezgini** ve iade edilir.|
|Tek projeyle çözüme ekleme - tek proje|1. Tek bir proje ile bir çözüm oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. İkinci bir boş çözüm oluşturun.<br />5. Kaynak denetiminden daha önce denetlenen çözümü ekleyin (**Dosya**, **Kaynak Denetimi**, **Project Denetimi'ne ekleyin).**|Eklenen proje, **Çözüm Gezgini** ve iade edilir.|
|Çözüme ekle — seçime göre kaynak denetimine eklenen çözüm|1. Proje ile bir çözüm oluşturun.<br />2. Seçim olarak kaynak denetimine yalnızca çözüm ekleyin. Bu adım başarılı olursa sonraki adıma geçin.<br />3. Çözümü kapatın.<br />4. Yeni bir çözüm oluşturun.<br />5. Kaynak denetiminden daha önce denetlenen çözümü ekleyin (**Dosya**, **Kaynak Denetimi**, **Project Denetimi'ne ekleyin).**|`Result from Step 2:`<br /><br /> Project, kaynak denetimi altında değildir.<br /><br /> `Result from Step 5:`<br /><br /> İlk çözümde çözüm öğeleri varsa, bunlar kaynak denetiminden ek olamaz, bu nedenle görünmezler.<br /><br /> Project çözümden gelen her şey kullanılamıyor olarak görünür.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
